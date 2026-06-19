Database Rules & Safe Transaction Handling

Strictly follow these rules when writing database queries or migrations to prevent bottleneck issues, deadlocks, and transaction timeouts.

1. Manual Transaction Control (Highly Recommended)

Do not rely on implicit or automatic transactions without clear boundaries. Always use manual transactions wrapped in strict try-catch blocks with explicit rollback mechanisms:

use Illuminate\Support\Facades\DB;
use Illuminate\Support\Facades\Log;

DB::beginTransaction();
try {
    // Execute database operations as quickly as possible
    
    DB::commit();
} catch (\Exception $e) {
    DB::rollBack();
    Log::error("Database transaction failed: " . $e->getMessage());
    throw $e;
}


2. Isolating File I/O & External API Calls (MANDATORY)

The Golden Rule: Never perform File System operations, HTTP API requests, file uploads, directory creations (mkdir), or dispatch emails inside a database transaction block (DB::beginTransaction()).

The Reason: I/O operations are slow. While they execute, the database holds a lock (Row Lock) on the affected rows. High traffic will queue these locks, leading directly to Error 1206: Lock wait timeout exceeded.

Bad Pattern (PROHIBITED):

DB::beginTransaction(); // ❌ LOCK STARTS
$data = Model::create($request);
if ($request->hasFile('image')) {
    $path = $request->file('image')->store('uploads'); // ❌ Slow I/O holding DB lock
    $data->update(['path' => $path]);
}
DB::commit();


Good Pattern (REQUIRED):

// 1. Handle all slow I/O operations outside the transaction
$path = null;
if ($request->hasFile('image')) {
    $path = $request->file('image')->store('uploads'); // ✅ Safe and isolated
}

// 2. Execute database operations at lightning speed
DB::beginTransaction(); // ✅ LOCK STARTS
try {
    $data = Model::create(array_merge($request->validated(), ['path' => $path]));
    DB::commit(); // ✅ LOCK ENDS
} catch (\Exception $e) {
    DB::rollBack();
    if ($path) Storage::delete($path); // Cleanup orphan files on failure
    throw $e;
}


3. Indexing Best Practices

Any column used inside a where clause (such as nrp, uuid, is_active, payment_month) must be indexed within its database migration file.

Lacking indices forces MySQL to perform a Table Lock instead of a Row Lock, heavily increasing the probability of Error 1206 under high concurrent traffic.
Workflow: Database Schema Modifications

Follow these steps when modifying or extending an existing database schema to prevent breaking production environments or dropping live transaction records.

Step 1: Generate a New Migration (Never edit old ones)

If the schema has been deployed to testing, staging (QAS), or production environments, DO NOT EDIT previous migration files.

Always create a brand-new incremental migration file (e.g., php artisan make:migration add_columns_to_users_table).

Step 2: Handling Existing Data (Data Migrations)

If you are adding a new NOT NULL column, provide a safe default value or write a transitional data-filling logic so existing records do not trigger database constraint failures.

Step 3: Update Model Guarded/Fillable Properties

Once the migration runs successfully, update the $fillable array or model casts inside the Eloquent Model to accommodate the new database changes.
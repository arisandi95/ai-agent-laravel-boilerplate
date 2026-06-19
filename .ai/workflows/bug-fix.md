Workflow: Bug Fixing

Follow this debugging and repair workflow to identify, isolate, and resolve application bugs.

Step 1: Replicate & Identify

Analyze the error trace (Fatal Error, Syntax Error, or stack traces).

Pinpoint the exact file name and line number throwing the exception.

Execute direct database diagnostics if the bug is related to data-state inconsistencies.

Step 2: Isolate the Root Cause

Path/Missing File Errors: Check for relative vs. absolute path discrepancies (realpath), or case-sensitivity mismatch issues on Linux server environments.

Lock Wait Timeout (1206): Run SHOW FULL PROCESSLIST; or analyze information_schema.innodb_trx to identify hanging queries keeping tables/rows locked.

Step 3: Write Defensive Fixes

Write structural repairs without breaking existing system workflows.

Use defensive programming techniques (e.g., early-exit returns, if (empty($data)) guards) before executing operations on variables.

Step 4: Verify & Cleanup

Test the previously failing screen, route, or API endpoint.

Provide the user with a concise summary of the modified files and updated line blocks.
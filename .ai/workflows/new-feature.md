Workflow: Implementing a New Feature

Follow this structured step-by-step workflow whenever implementing a brand new feature or module.

Step 1: Requirements & Database Schema Analysis

Determine the required database tables.

Design database migrations ensuring proper indexing, foreign keys, and audit fields are set up safely.

Review this database layout with the user in the chat before running migrations.

Step 2: Creating Migrations & Models

Scaffold migrations and models using Artisan.

Fill the migration file with appropriate field constraints, indices, softDeletes, and audit trail columns (created_by, updated_by).

Declare the exact Eloquent relationships on the corresponding Model classes.

Step 3: Service Layer Implementation

Create a dedicated Service class to handle data manipulation and orchestration.

Wrap all database modifications in manual try-catch transaction blocks adhering to .ai/database-rules.md.

Step 4: Form Request & Controller Scaffolding

Generate a dedicated Form Request class to validate user inputs.

Inject the Service class into the Controller and delegate the business logic to it.

Step 5: Designing the UI

Design the responsive layout using Blade template engine combined with Tailwind CSS.

Ensure dynamic variables passed from the controller are bound safely.
Project Architecture & Design Patterns

To keep the codebase clean, modular, and maintainable, all new feature implementations must strictly adhere to the following architectural patterns.

1. Controller-Service-Repository/Model Pattern

Controller: Acts solely as an HTTP traffic director. It must contain no business logic, complex database queries, or raw data manipulation.

Form Request: Data validation must be isolated inside a dedicated Form Request class (php artisan make:request).

Service Layer: Houses all core business logic. One service handles one specific domain (e.g., IntegrityPactService).

Eloquent Model: Represents the data entity. Use Eloquent Scopes to handle reusable query logic.

[Request] ──> [Controller] ──> [Form Request (Validation)]
                                     │
                                     ▼
                              [Service Layer] (Business Logic & Transactions)
                                     │
                                     ▼
                              [Eloquent Model] ──> [Database]


2. API & Responses

Use Eloquent API Resources (php artisan make:resource) to format JSON outputs for all API endpoints.

Never return raw arrays or bare Eloquent model instances directly to an HTTP response.

3. UUID vs Auto-increment

For transactional tables, logs, and sensitive public-facing data (e.g., integrity_pact or payroll details), use UUID as the Primary Key.

Use standard auto-incrementing integers only for internal lookup/master tables that are never exposed outside the application boundaries.
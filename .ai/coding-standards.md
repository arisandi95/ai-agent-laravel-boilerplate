Coding Standards & Best Practices

All PHP files must adhere to PSR-12 and modern Laravel development conventions.

1. PHP Code Style

Declare strict typing at the top of every PHP file: declare(strict_types=1);.

All properties, parameters, and function return values must be explicitly typed.

Leverage modern PHP features where applicable (e.g., match expressions, constructor property promotion, nullsafe operators).

2. Naming Conventions

Controllers: PascalCase with Controller suffix (e.g., IntegrityPactController).

Models: Singular PascalCase (e.g., IntegrityPactMaster).

Services: PascalCase with Service suffix (e.g., PactApprovalService).

Methods/Functions: camelCase (e.g., storeApprovalData()).

3. Tailwind CSS & UI Standards

When designing UI elements, prioritize a mobile-first responsive approach using Tailwind's breakpoint prefixes (sm:, md:, lg:).

Lean on modern visual tokens: smooth rounded corners (rounded-lg or rounded-2xl), soft depths (shadow-sm, shadow-md), and cohesive color palettes.

CRITICAL: Never use native JavaScript alert() or confirm() boxes. Always use UI toasts, custom alert panels, or interactive modals.
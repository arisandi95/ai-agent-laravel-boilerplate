# AI Agent Harness — Laravel Web App Boilerplate

## Project Overview
This is an **AI Agent Harness** boilerplate for building Laravel web applications. AI agents use this harness to generate domain-specific Laravel code — models, migrations, controllers, views, tests, and documentation — based on the application's business context.

## Agent Capabilities
Agents can perform Laravel-specific tasks:
- **Artisan Commands**: `make:model`, `make:controller`, `make:migration`, `make:request`, `make:resource`
- **Eloquent ORM**: Models, relationships, factories, seeders, policies
- **Validation**: Form Requests with domain-specific rules
- **API Development**: Controllers, Resources, Routes (sanctum/passport)
- **Frontend**: Blade templates, Inertia.js pages, Livewire components
- **Testing**: PHPUnit/Pest feature/unit tests, Dusk browser tests
- **Packages**: Composer/NPM package installation via `.ai/` guidance

## Project Structure
```
├── .ai/                    # Agent rules, architecture, workflows
├── app/
│   ├── Http/
│   │   ├── Controllers/
│   │   ├── Requests/
│   │   └── Resources/
│   ├── Models/
│   ├── Services/
│   └── Providers/
├── database/
│   ├── migrations/
│   ├── factories/
│   └── seeders/
├── resources/
│   ├── views/
│   └── js/
├── routes/
│   ├── web.php
│   └── api.php
├── tests/
└── AGENTS.md
```

## How Agents Use This Harness

### Step 1: Read AGENTS.md
Every task starts by reading this file.

### Step 2: Load Context from `.ai/`
Agents read the configuration files to understand rules, architecture, and coding standards:
- `.ai/project-rules.md` — scope, security, quality rules
- `.ai/architecture.md` — system design principles
- `.ai/database-rules.md` — schema conventions
- `.ai/coding-standards.md` — PHP/Laravel coding style
- `.ai/workflows/*.yaml` — step-by-step task workflows

### Step 3: Read `README.md` for Domain Context
Agents read README.md to understand:
- **Application name** (e.g., "Aplikasi Perencanaan Keuangan")
- **Domain** (e.g., financial planning, school management, e-commerce)
- **Business entities** (e.g., `Transaksi`, `Anggaran`, `Siswa`, `Guru`)

### Step 4: Execute Domain-Adapted Workflows
All workflows, code generation, and naming conventions are adapted to the application's domain:
- Example: Finance app → Models `Transaksi`, `Anggaran`; validation `jumlah > 0`
- Example: School app → Models `Siswa`, `Guru`, `Jadwal`; validation `nis_unique`

## Workflow Files (`.ai/workflows/`)
- `agent-lifecycle.yaml` — Init, context loading, tool discovery, task execution
- `code-development.yaml` — Requirements → design → implement → tests → PR
- `code-review.yaml` — Static analysis, security, complexity, human review
- `debugging.yaml` — Reproduce → RCA → fix → verify → document
- `documentation.yaml` — Extract → generate → validate → commit docs

## Naming Convention for Domain Adaptation
All generated code uses **domain-specific terminology**, not generic Laravel defaults:
| Generic Name | Finance App | School App |
|---|---|---|
| `Item` | `Transaksi` | `Siswa` |
| `Category` | `KategoriKeuangan` | `JenisJadwal` |
| `Record` | `Anggaran` | `Nilai` |
| `UserController` | `TransaksiController` | `SiswaController` |
| `DashboardView` | `laporan-keuangan.blade.php` | `dashboard-sekolah.blade.php` |

---

*Boilerplate ini dirancang untuk dikustomisasi ke domain aplikasi manapun. Baca `README.md` untuk cara memulai.*

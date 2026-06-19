# AI Agent Harness — Laravel Web App Boilerplate

> **Boilerplate AI Agent untuk pengembangan aplikasi web dengan Laravel**

Repositori ini adalah **boilerplate AI Agent Harness** yang terintegrasi penuh dengan **Laravel**. Harness ini menyediakan struktur konfigurasi, standar coding, dan workflow terdefinisi yang dapat digunakan oleh AI agent untuk mengotomatiskan pengembangan aplikasi web Laravel — dari pembuatan model, migrasi, controller, API, hingga testing dan dokumentasi.

---

## 🚀 Quick Start

### 1. Clone atau Copy Boilerplate

```bash
git clone <repository-url> nama-aplikasi-anda
cd nama-aplikasi-anda
```

### 2. Sesuaikan dengan Aplikasi Anda

Jalankan perintah berikut ke AI agent Anda untuk menyesuaikan boilerplate:

```
Sesuaikan file harness engineering config dengan aplikasi saya yaitu 'Aplikasi Perencanaan Keuangan'
```

AI agent akan:
- Membaca `README.md` untuk memahami nama, deskripsi, dan jenis aplikasi
- Membaca semua file di folder `.ai/` (project-rules.md, architecture.md, database-rules.md, coding-standards.md, workflows/)
- **Menyesuaikan konteks, aturan, dan workflow dengan domain aplikasi Anda (bukan generic/web app)**
- Menyesuaikan database schema, validation rules, UI components, dan terminologi sesuai domain bisnis
- Mengajakklarifikasi detail yang diperlukan sebelum memulai development

**Contoh adaptasi domain:**
- Jika aplikasi adalah `Aplikasi Perencanaan Keuangan`, agent akan menghasilkan model seperti `Transaksi`, `Anggaran`, `KategoriKeuangan` dengan relasi dan aturan validasi yang sesuai
- Jika aplikasi adalah `Sistem Informasi Manajemen Sekolah`, agent akan menghasilkan model seperti `Siswa`, `Guru`, `MataPelajaran`, `Jadwal`

### 3. Mulai Development

Setelah harness dikonfigurasi, Anda bisa menggunakan perintah agent seperti:

| Perintah                      | Deskripsi                                          |
|-------------------------------|----------------------------------------------------|
| `/develop <deskripsi fitur>`  | Membuat fitur baru dari requirements               |
| `/create model NamaModel`     | Generate model + migration + seeder + controller   |
| `/review`                     | Review kode secara otomatis                        |
| `/debug <error>`              | Debug dan perbaiki bug                            |
| `/docs`                       | Generate/update dokumentasi                       |

---

## 📁 Struktur Project

```
├── AGENTS.md                   # Entry point — baca file ini PERTAMA
├── .ai/                        # Konfigurasi & rules untuk AI agent
│   ├── project-rules.md        # Scope, authority, security rules
│   ├── architecture.md         # Arsitektur sistem & deployment
│   ├── database-rules.md       # Database design, migration, dan polyglot persistence rules
│   ├── coding-standards.md     # Coding standards (TypeScript, Python, Go)
│   └── workflows/              # Definisi workflow agent
│       ├── agent-lifecycle.yaml   # Initialize → context → tools → execute
│       ├── code-development.yaml  # Requirements → design → implement → tests → PR
│       ├── code-review.yaml       # Static analysis → security → complexity → review
│       ├── debugging.yaml         # Reproduce → RCA → fix → verify → document
│       └── documentation.yaml     # Generate docs → validate → commit
├── app/                        # (Laravel) — aplikasi akan di-generate di sini
├── bootstrap/
├── config/
├── database/
│   ├── migrations/
│   ├── factories/
│   └── seeders/
├── resources/
├── routes/
├── storage/
├── tests/
└── scripts/
```

---

## 🤖 Cara Kerja AI Agent Harness

### Alur Kerja Agent

```
┌─────────────────────────────────────────────────────────┐
│  1. Agent membaca AGENTS.md (file ini)                   │
│  2. Agent memuat semua file di .ai/ sebagai konteks      │
│  3. Agent menyesuaikan rules & workflow dengan           │
│     konteks aplikasi Anda                                │
│  4. Agent siap menerima perintah dari Anda               │
└─────────────────────────────────────────────────────────┘
         │
         ▼
┌─────────────────────────────────────────────────────────┐
│  Contoh Perintah yang Bisa Dijalankan:                  │
│  ─────────────────────────────────────────────────────  │
│  • /develop Fitur Penagihan Otomatis                    │
│  • /create model Transaksi dengan relasi ke User        │
│  • /review PR #42                                       │
│  • /debug Error 500 di halaman laporan                  │
│  • /docs generate API documentation                     │
└─────────────────────────────────────────────────────────┘
```

### Modes of Operation

| Mode        | Deskripsi                                                       |
|-------------|-----------------------------------------------------------------|
| **PLAN**    | Agent menganalisis requirements dan membuat rencana kerja       |
| **ACT**     | Agent menjalankan rencana — create files, run commands, dll.  |

---

## 🔧 Konfigurasi Awal — Template Prompt

Untuk menyesuaikan boilerplate ini dengan aplikasi Anda, kirim prompt berikut ke AI agent Anda:

```
Saya membuat boilerplate AI Agent Harness untuk pengembangan aplikasi web dengan Laravel.

Saya ingin kamu:
1. Baca semua file di folder .ai/ sebagai konteks
2. Sesuaikan konteks, aturan, dan workflow dengan aplikasi saya

Detail aplikasi saya:
- Nama aplikasi: <Nama Aplikasi Anda>
- Deskrpsi: <Deskripsi singkat>
- Jenis: <Web App / API / CMS / E-commerce / dll.>

Contoh prompt yang bisa digunakan:
"Sesuaikan file harness engineering config dengan aplikasi saya yaitu 'Aplikasi Perencanaan Keuangan'"
" Sesuaikan file harness engineering config dengan aplikasi saya yaitu 'Sistem Informasi Manajemen Sekolah'"
" Sesuaikan file harness engineering config dengan aplikasi saya yaitu 'Marketplace Produk Kerajinan'"
```

AI agent akan:
- Membaca `.ai/project-rules.md`, `.ai/architecture.md`, `.ai/database-rules.md`, `.ai/coding-standards.md`
- Membaca semua workflow di `.ai/workflows/`
- Menyesuaikan rules, constraints, dan workflow dengan domain aplikasi Anda
- Meminta klarifikasi jika ada informasi yang kurang

---

## 📋 File Konfigurasi — Penjelasan Singkat

| File                              | Fungsi                                                                 |
|-----------------------------------|-----------------------------------------------------------------------|
| `.ai/project-rules.md`            | Aturan agent — scope, siapa yang bisa diubah, quality standards      |
| `.ai/architecture.md`             | Arsitektur 4-layer (Presentation → Orchestration → Core → Infra)     |
| `.ai/database-rules.md`           | Aturan database — schema, migration, indexing, backup                |
| `.ai/coding-standards.md`         | Coding style — TS, Python, Go, Git workflow                          |
| `.ai/workflows/*.yaml`            | Workflow terdefinisi — lifecycle, development, review, debug, docs   |

---

## 🎯 Domain Adaptation

Ketika Anda menjalankan prompt konfigurasi awal, AI agent akan menyesuaikan seluruh boilerplate dengan domain aplikasi Anda:

- **Membaca `README.md`** untuk memahami nama, deskripsi, dan jenis aplikasi
- **Menyesuaikan database schema** — tabel, kolom, relasi sesuai domain bisnis
- **Menyesuaikan validation rules** — aturan validasi yang relevan dengan domain
- **Menyesuaikan UI components** — komponen Blade/Inertia/Livewire yang sesuai
- **Menggunakan terminologi domain** di seluruh generated code (models, controllers, views, tests)

**Contoh: Aplikasi Perencanaan Keuangan**
- Models: `Transaksi`, `Anggaran`, `KategoriKeuangan`, `Rekening`
- Controllers: `LaporanKeuanganController`, `TransaksiController`
- Validation: `jumlah harus positif`, `tanggal tidak boleh di masa depan`
- UI: `halaman laporan keuangan`, `form input transaksi`

---

## 🛠️ Teknologi yang Didukung

| Layer              | Teknologi                                         |
|--------------------|---------------------------------------------------|
| Backend            | Laravel 11+, PHP 8.3+                             |
| Frontend           | Blade, Inertia.js (Vue/React), Livewire, Flux     |
| Database           | PostgreSQL, MySQL, SQLite                         |
| Cache              | Redis                                             |
| Vector Store       | Chroma, Qdrant (untuk AI memory)                  |
| Testing            | PHPUnit, Pest, Dusk                               |
| Package Manager   | Composer, npm/pnpm                               |
| Containerization   | Docker, Docker Compose                           |

---

## 📝 Laravel Conventions yang Diikuti

Agent akan selalu mengikuti konvensi Laravel:
- **MVC Pattern**: Controller → Model → View
- **Eloquent ORM**: Relationships, accessors, mutators, scopes, policies
- **Artisan Commands**: `make:model`, `make:controller`, `make:migration`, dll.
- **Route Definitions**: `routes/web.php`, `routes/api.php`, route model binding
- **Form Requests**: Validation via `php artisan make:request`
- **API Resources**: `php artisan make:resource`
- **Testing**: Feature tests & Unit tests via PHPUnit/Pest
- **Domain-Specific**: Nama model, controller, dan view disesuaikan dengan domain aplikasi

---

## 🔐 Keamanan

- Semua credentials menggunakan environment variables (`.env`)
- Tidak ada secrets yang dicommit ke repository
- RBAC untuk authorization
- Input sanitization via Form Requests
- Audit logging untuk agent actions

---

## 🤝 Kontribusi

1. Fork repository
2. Buat branch: `git checkout -b feature/nama-fitur`
3. Commit dengan Conventional Commits: `feat:`, `fix:`, `chore:`, `docs:`
4. Push ke branch: `git push origin feature/nama-fitur`
5. Buka Pull Request

---

## 📄 License

MIT License

---

## 💡 Contoh Penggunaan — Perintah untuk Agent

### Membuat Fitur Baru
```
/create fitur registrasi user dengan email verification
```

### Membuat Model
```
/create model Transaksi dengan kolom: nama, jumlah, tanggal, kategori_id
```

### Generate API
```
/create API endpoint untuk laporan keuangan bulanan
```

### Review PR
```
/review PR #15
```

### Debug Error
```
/debug Error 500 di halaman dashboard
```

### Update Dokumentasi
```
/docs update README dengan cara menjalankan aplikasi
```

---

*Built with ❤️ using AI Agent Harness for Laravel*
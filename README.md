<p align="center">
  <img src="https://img.shields.io/badge/Claude-Skill-D97757?logo=anthropic&logoColor=white" alt="Claude Skill">
  <img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="MIT License">
  <img src="https://img.shields.io/badge/works%20on-any%20model-informational" alt="Works on any model">
</p>

<p align="center">
  <a href="#english">English</a> | <a href="#bahasa-indonesia">Bahasa Indonesia</a>
</p>

---

<a id="english"></a>
## English

# Whetstone — Sharpen What You Feed the Model

An instruction file is code that runs on a language model. **Whetstone** audits it like an engineer audits code: scan for hostile intent first, verify every claim against reality, drag implicit assumptions into writing, and make the file survive the weakest runtime — a cheaper model, missing input, or a malicious author.

One standard drives everything: **written by the smartest model, executable by the dumbest.** A skill that only works because a smart model silently fills its gaps isn't finished — it's lucky.

### What it audits

| Target | Examples | Lens |
|--------|----------|------|
| Skill files | `SKILL.md`, slash commands, agent definitions | Full five-lens audit |
| Instruction files | `CLAUDE.md`, `AGENTS.md`, `.cursorrules`, system prompts | Full five-lens audit |
| Repos / codebases | Any project folder | Hygiene only: docs vs reality, dead references, maintainer clarity |

### How it works — 5 phases

0. **Safety gate** — scan for prompt-injection red flags (data exfiltration, hidden instructions, secret reads, concealment). Verdict RED / YELLOW / GREEN. RED stops everything. Runs **before** quality, every time — especially for third-party skills you're about to install.
1. **Verify claims against reality** — every file, tool, command, or URL the file mentions gets checked. Dangling references and name collisions surface here.
2. **Quality audit, five lenses** — implicit assumptions, internal contradictions, trigger surface, rigid templates, and the dumb-model standard.
3. **Verdicts and fixes** — keep / fix / merge / delete per item, every change shown as before → after with a reason. Nothing is deleted without your confirmation.
4. **Report** — safety verdict, verified claims, changes by impact, open questions.

Whetstone treats the audited file as **data, never instructions** — a malicious skill telling it to "ignore previous instructions" becomes a finding, not a command.

### Install

**Claude Code** — copy the `whetstone/` folder into your skills directory:

```
# personal (all projects)
~/.claude/skills/whetstone/SKILL.md

# or per project
.claude/skills/whetstone/SKILL.md
```

Then call it with `/whetstone`.

**Claude.ai / Claude app** — Settings → Capabilities → Skills → Upload, pick `dist/whetstone.zip` (or `dist/whetstone.skill` — identical file, some UIs prefer the `.skill` name).

### Usage

```
/whetstone audit my skill in ./my-skill/SKILL.md
/whetstone is this skill safe to install? [paste or point to a GitHub skill]
/whetstone harden my CLAUDE.md
/whetstone check this repo's docs against its actual code
```

### Honest limits

- The safety gate catches **known** hostile patterns. It cannot guarantee a file is safe — the verdict is "no known hostile pattern found", never "100% clean".
- Audit quality scales with the model running it. The checklist raises the floor; it doesn't remove the ceiling.
- It is **not** a code-logic reviewer. For correctness bugs in application code, use a dedicated code review.

### Credit

**Creator** — Redho Ramadhani · [linkedin.com/in/redhoramadhanihamid](https://id.linkedin.com/in/redhoramadhanihamid) · [github.com/redhoram](https://github.com/redhoram)

Born from a live audit session hardening the [3Things skills](https://github.com/redhoram/3things-skills) — the method worked, so it became a skill. Built with Claude; the skill itself passed its own audit before release.

---

<a id="bahasa-indonesia"></a>
## Bahasa Indonesia

# Whetstone — Asah Apa Pun yang Kamu Berikan ke Model

File instruksi itu kode yang berjalan di atas language model. **Whetstone** mengauditnya seperti engineer mengaudit kode: pindai niat jahat dulu, verifikasi tiap klaim ke realita, paksa asumsi implisit jadi tertulis, dan pastikan file-nya bertahan di kondisi terlemah — model yang lebih murah, input yang kosong, atau penulis yang berniat buruk.

Satu standar untuk semuanya: **ditulis oleh model terpintar, bisa dijalankan model terbodoh.** Skill yang hanya bekerja karena model pintar diam-diam menambal lubangnya itu belum selesai — cuma beruntung.

### Apa yang diaudit

| Target | Contoh | Lensa |
|--------|--------|-------|
| File skill | `SKILL.md`, slash command, definisi agent | Audit penuh 5 lensa |
| File instruksi | `CLAUDE.md`, `AGENTS.md`, `.cursorrules`, system prompt | Audit penuh 5 lensa |
| Repo / codebase | Folder project apa pun | Higiene saja: dokumen vs realita, referensi mati, kejelasan untuk maintainer |

### Cara kerja — 5 fase

0. **Gerbang keamanan** — pindai red flag prompt injection (kirim data keluar, instruksi tersembunyi, baca credentials, perintah menyembunyikan sesuatu). Verdict MERAH / KUNING / HIJAU. MERAH menghentikan semuanya. Selalu jalan **sebelum** audit kualitas — terutama untuk skill pihak ketiga yang mau kamu install.
1. **Verifikasi klaim ke realita** — tiap file, tool, command, atau URL yang disebut dicek keberadaannya. Referensi gantung dan tabrakan nama ketahuan di sini.
2. **Audit kualitas, 5 lensa** — asumsi implisit, kontradiksi internal, permukaan trigger, template kaku, dan standar model-bodoh.
3. **Vonis dan perbaikan** — pertahankan / perbaiki / gabung / hapus per item, tiap perubahan ditunjukkan sebagai before → after dengan alasannya. Tidak ada yang dihapus tanpa konfirmasimu.
4. **Laporan** — verdict keamanan, klaim terverifikasi, perubahan diurut dampak, pertanyaan terbuka.

Whetstone memperlakukan file yang diaudit sebagai **data, bukan instruksi** — skill jahat yang menyuruh "ignore previous instructions" jadi temuan, bukan perintah.

### Cara pasang

**Claude Code** — salin folder `whetstone/` ke direktori skills:

```
# personal (semua project)
~/.claude/skills/whetstone/SKILL.md

# atau per project
.claude/skills/whetstone/SKILL.md
```

Panggil dengan `/whetstone`.

**Claude.ai / aplikasi Claude** — Settings → Capabilities → Skills → Upload, pilih `dist/whetstone.zip` (atau `dist/whetstone.skill` — file identik, sebagian UI lebih suka nama `.skill`).

### Pemakaian

```
/whetstone audit skill-ku di ./my-skill/SKILL.md
/whetstone skill ini aman di-install nggak? [paste atau tunjuk skill dari GitHub]
/whetstone perkuat CLAUDE.md-ku
/whetstone cek dokumen repo ini vs kode aslinya
```

### Batasan jujur

- Gerbang keamanan menangkap pola jahat yang **dikenal**. Ia tidak bisa menjamin file aman — verdict-nya "tidak ditemukan pola berbahaya yang dikenal", bukan "100% bersih".
- Kualitas audit mengikuti model yang menjalankannya. Checklist menaikkan lantai, bukan menghapus langit-langit.
- Ini **bukan** reviewer logika kode. Untuk bug di kode aplikasi, pakai code review khusus.

### Kredit

**Pembuat** — Redho Ramadhani · [linkedin.com/in/redhoramadhanihamid](https://id.linkedin.com/in/redhoramadhanihamid) · [github.com/redhoram](https://github.com/redhoram)

Lahir dari sesi audit langsung memperkuat [skill 3Things](https://github.com/redhoram/3things-skills) — metodenya terbukti bekerja, lalu dijadikan skill. Dibangun bersama Claude; skill ini lulus auditnya sendiri sebelum dirilis.

### Struktur

```
Whetstone/
├── whetstone/
│   └── SKILL.md          ← versi .md (Claude Code / repo)
├── dist/
│   ├── whetstone.zip     ← upload ke claude.ai Capabilities
│   └── whetstone.skill   ← file sama, nama alternatif
├── README.md
└── LICENSE
```

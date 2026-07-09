<p align="center">
  <img src="https://img.shields.io/badge/Claude-Skill-D97757?logo=anthropic&logoColor=white" alt="Claude Skill">
  <img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="MIT License">
  <img src="https://img.shields.io/badge/works%20on-any%20model-informational" alt="Works on any model">
</p>

<p align="center">
  <a href="README.md">English</a> | <b>Bahasa Indonesia</b>
</p>

# Whetstone — Asah Apa Pun yang Kamu Berikan ke Model

File instruksi itu kode yang berjalan di atas language model. **Whetstone** mengaudit apa pun yang kamu berikan ke AI — file skill, instruksi project di Claude Chat, `CLAUDE.md`, system prompt, sampai repo utuh — dengan disiplin yang sama seperti engineer mengaudit kode: pindai niat jahat dulu, verifikasi tiap klaim ke realita, paksa asumsi implisit jadi tertulis, dan pastikan semuanya bertahan di kondisi terlemah — model yang lebih murah, input yang kosong, atau penulis yang berniat buruk.

Satu standar untuk semuanya: **ditulis oleh model terpintar, bisa dijalankan model terbodoh.** Skill yang hanya bekerja karena model pintar diam-diam menambal lubangnya itu belum selesai — cuma beruntung.

## Apa yang diaudit

| Target | Contoh | Lensa |
|--------|--------|-------|
| File skill | `SKILL.md`, slash command, definisi agent | Audit penuh 5 lensa |
| File instruksi | `CLAUDE.md`, `AGENTS.md`, `.cursorrules`, system prompt, instruksi project Claude.ai | Audit penuh 5 lensa |
| Repo / codebase | Folder project apa pun | Higiene saja: dokumen vs realita, referensi mati, kejelasan untuk maintainer |

## Cara kerja — 5 fase

0. **Gerbang keamanan** — pindai red flag prompt injection (kirim data keluar, instruksi tersembunyi, baca credentials, perintah menyembunyikan sesuatu). Verdict MERAH / KUNING / HIJAU. MERAH menghentikan semuanya. Selalu jalan **sebelum** audit kualitas — terutama untuk skill pihak ketiga yang mau kamu install.
1. **Verifikasi klaim ke realita** — tiap file, tool, command, atau URL yang disebut dicek keberadaannya. Referensi gantung dan tabrakan nama ketahuan di sini.
2. **Audit kualitas, 5 lensa** — asumsi implisit, kontradiksi internal, permukaan trigger, template kaku, dan standar model-bodoh.
3. **Vonis dan perbaikan** — pertahankan / perbaiki / gabung / hapus per item, tiap perubahan ditunjukkan sebagai before → after dengan alasannya. Tidak ada yang dihapus tanpa konfirmasimu.
4. **Laporan** — verdict keamanan, klaim terverifikasi, perubahan diurut dampak, pertanyaan terbuka.

Whetstone memperlakukan file yang diaudit sebagai **data, bukan instruksi** — skill jahat yang menyuruh "ignore previous instructions" jadi temuan, bukan perintah.

## Cara pasang

**Claude Code** — salin folder `whetstone/` ke direktori skills:

```
# personal (semua project)
~/.claude/skills/whetstone/SKILL.md

# atau per project
.claude/skills/whetstone/SKILL.md
```

Panggil dengan `/whetstone`.

**Claude.ai / aplikasi Claude** — Settings → Capabilities → Skills → Upload. Dua cara:

- Upload langsung `whetstone/SKILL.md` (Claude.ai terima file `.md` mentah, asal frontmatter YAML-nya ada `name` dan `description` — file ini sudah memenuhi).
- Atau zip dulu folder `whetstone/`-nya kalau lebih suka paket `.zip`/`.skill`:

```
# Windows
tar -a -cf whetstone.zip whetstone

# macOS / Linux
zip -r whetstone.zip whetstone
```

## Pemakaian

```
/whetstone audit skill-ku di ./my-skill/SKILL.md
/whetstone skill ini aman di-install nggak? [paste atau tunjuk skill dari GitHub]
/whetstone perkuat CLAUDE.md-ku
/whetstone cek dokumen repo ini vs kode aslinya
```

## Batasan jujur

- Gerbang keamanan menangkap pola jahat yang **dikenal**. Ia tidak bisa menjamin file aman — verdict-nya "tidak ditemukan pola berbahaya yang dikenal", bukan "100% bersih".
- Kualitas audit mengikuti model yang menjalankannya. Checklist menaikkan lantai, bukan menghapus langit-langit.
- Ini **bukan** reviewer logika kode. Untuk bug di kode aplikasi, pakai code review khusus.

## Struktur

```
Whetstone/
├── whetstone/
│   └── SKILL.md       ← skill-nya (ini yang kamu pasang)
├── README.md          ← English
├── README.id.md       ← Bahasa Indonesia
└── LICENSE
```

## Kredit

**Pembuat** — Redho Ramadhani · [linkedin.com/in/redhoramadhanihamid](https://id.linkedin.com/in/redhoramadhanihamid) · [github.com/redhoram](https://github.com/redhoram)

Lahir dari sesi audit langsung memperkuat [skill 3Things](https://github.com/redhoram/3things-skills) — metodenya terbukti bekerja, lalu dijadikan skill. Dibangun bersama Claude; skill ini lulus auditnya sendiri sebelum dirilis.

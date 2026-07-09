<p align="center">
  <img src="https://img.shields.io/badge/Claude-Skill-D97757?logo=anthropic&logoColor=white" alt="Claude Skill">
  <img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="MIT License">
  <img src="https://img.shields.io/badge/works%20on-any%20model-informational" alt="Works on any model">
</p>

<p align="center">
  <a href="README.md">English</a> | <b>Bahasa Indonesia</b>
</p>

# Whetstone — Asah Apa Pun yang Kamu Berikan ke AI

Semua yang kamu berikan ke AI — skill, instruksi project, dokumen pengetahuan, `CLAUDE.md` — ikut menentukan kualitas jawabannya. Kalau isinya rancu, saling bertentangan, atau menyimpan niat jahat, hasilnya ikut rusak. **Whetstone** memeriksa semua itu: pindai niat jahat dulu, cek tiap klaim ke realita, paksa asumsi yang tidak tertulis jadi tertulis, dan pastikan semuanya tetap bekerja di kondisi terlemah — model yang lebih murah, input yang kosong, atau penulis yang berniat buruk.

Satu standar untuk semuanya: **ditulis oleh model terpintar, bisa dijalankan model terbodoh.** Skill yang hanya bekerja karena model pintar diam-diam menambal lubangnya itu belum selesai — cuma beruntung.

## Apa yang diaudit

| Target | Contoh | Cakupan audit |
|--------|--------|---------------|
| File skill | `SKILL.md`, slash command, definisi agent | Audit penuh 5 lensa |
| File instruksi | Instruksi project di Claude.ai, `CLAUDE.md`, `AGENTS.md`, system prompt | Audit penuh 5 lensa |
| Project knowledge | Dokumen yang di-upload ke Project Claude.ai — SOP, panduan, referensi | Audit penuh 5 lensa |
| Repo / folder project | Project software apa pun | Kebersihan dasar: dokumen vs realita, referensi mati, kejelasan untuk orang berikutnya |

## Cara kerja — 5 fase

0. **Gerbang keamanan** — sebelum apa pun, periksa apakah file-nya menyimpan niat jahat: menyuruh kirim data keluar, membaca password/credentials, menyembunyikan instruksi, atau melarang memberi tahu kamu. Verdict MERAH / KUNING / HIJAU — MERAH langsung berhenti. Penting terutama untuk skill buatan orang lain yang mau kamu pasang.
1. **Verifikasi klaim ke realita** — semua yang disebut di dalam file dicek benar-benar ada: file lain, tool, command, link, langkah yang dirujuk. Referensi mati dan nama yang tabrakan ketahuan di sini.
2. **Audit kualitas, 5 lensa** — asumsi yang tidak tertulis, aturan yang saling bertentangan, kapan skill harusnya aktif (dan kapan tidak), template yang memaksa mengarang-ngarang, dan ujian utamanya: apakah model yang jauh lebih bodoh bisa menjalankan ini persis sama.
3. **Vonis dan perbaikan** — tiap bagian divonis: pertahankan / perbaiki / gabung / hapus. Tiap usulan ditunjukkan sebagai sebelum → sesudah dengan alasannya. Tidak ada yang dihapus tanpa persetujuanmu.
4. **Laporan** — hasil pemeriksaan keamanan, klaim yang terbukti (dan yang tidak), daftar perubahan diurut dari dampak terbesar, plus pertanyaan yang hanya kamu yang bisa jawab.

Whetstone memperlakukan file yang diaudit sebagai **data, bukan perintah** — file jahat yang menyuruh "abaikan instruksi sebelumnya" jadi temuan di laporan, bukan perintah yang dituruti.

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

- Upload langsung `whetstone/SKILL.md` (file `.md` mentah diterima, asal frontmatter YAML-nya ada `name` dan `description` — file ini sudah memenuhi).
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
/whetstone periksa instruksi & dokumen project-ku, ada yang rancu nggak?
```

## Batasan jujur

- Gerbang keamanan menangkap pola jahat yang **sudah dikenal**. Tidak ada jaminan 100% aman — verdict-nya selalu "tidak ditemukan pola berbahaya yang dikenal", bukan "pasti bersih".
- Hasil audit mengikuti kepintaran model yang menjalankannya. Checklist ini membuat model biasa bekerja jauh lebih teliti — tapi bukan sulap.
- Mencari bug di logika kode aplikasi bukan tugasnya — untuk itu pakai code review biasa.

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

Dibangun bersama Claude. Skill ini lulus auditnya sendiri sebelum dirilis.

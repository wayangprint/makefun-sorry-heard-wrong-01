# BUILD REPORT — makefun-sorry-heard-wrong-01

## Kompetisi

- Slug: `u-kiencx-sorry-i-heard-that-wrong-1858c729`
- Judul: "Sorry, I Heard That Wrong"
- Hadiah: $2 (3 tempat), tutup 26 Nov 2026 21:50 WIB
- Repo GitHub (dibuat parent): `wayangprint/makefun-sorry-heard-wrong-01`

## Batas karakter RULES (menang atas angka tugas)

- RULES.txt kit, baris 10 dan 15: entri adalah **1–140 karakter** UTF-8, bukan hanya
  whitespace. Sama dengan angka 140 dari tugas — RULES yang menang.
- Baris entri: **104 karakter** — di dalam rentang 1–140.

## Teks entri (persis, satu baris)

> Sorry, I heard 'play jazz' as 'buy a jet' — the jet arrives Tuesday, and I have already named it Jazz.

- Jumlah karakter: 104 (dihitung dengan `wc -m`, terverifikasi)
- sha256 entry.txt: `68095bc42afee39409a9ed488abea7b6243aa342de0ef4673fe80e269cc2145f`
- Tanpa newline di akhir file entry.txt (terverifikasi dengan `od -c`).

## Program

- `main.ts` — Node 22, stdlib saja, tanpa network/random/clock. Menulis satu baris
  ke entry.txt (hormat `MAKEFUN_OUTPUT_DIR`, fallback `/output` bila ada, kalau
  tidak di samping script) + echo ke stdout. Guard `checkLineLength` menolak
  menulis bila panjang di luar 1–140 karakter.
- Revisi (thinking_revised): setelah main.ts pertama jalan, dilakukan revisi nyata
  — struktur diubah dari konstanta APOLOGY_SETUP/APOLOGY_PUNCHLINE +
  `buildLine`/`resolveOutputDir`/`writeEntry` menjadi objek `apologyBeats`
  (mishearing/consequence/punchline) + `assembleLine`/`checkLineLength`/
  `outputFolder`/`publishLine`, plus guard validasi panjang dan komentar baru.
  Bukan sekadar ganti string.

## Verifikasi determinisme (2x run)

- Run 1: `MAKEFUN_OUTPUT_DIR=/tmp/scratch-sorry-a node main.ts`
- Run 2: `MAKEFUN_OUTPUT_DIR=/tmp/scratch-sorry-b node main.ts`
- sha256 kedua entry.txt: `68095bc42afee39409a9ed488abea7b6243aa342de0ef4673fe80e269cc2145f`
  (identik dengan entry.txt di repo) — `cmp` mengonfirmasi byte-identik.
- Catatan: direktori scratch generik `/tmp/scratch-a` dan `/tmp/scratch-b`
  sempat tertimpa entri builder lain yang berjalan paralel di VM yang sama
  (isi 90 byte, bukan entri ini); verifikasi diulang dengan direktori
  unik `scratch-sorry-a`/`scratch-sorry-b` dan lolos.

## Kit

- Kit: `~/workspace/superteam-raenest/makefun/sorry-heard-wrong-01/u-kiencx-sorry-i-heard-that-wrong-1858c729-kit/`
- kit.json `bundle_sha256`: `5fffd6054323f63a9408a6d2de561dbca3c960961ac4cbbf287198f0ea1b8437`
- sha256 tarball kit (artefak berbeda dari bundle_sha256):
  `7aba569d506fadb94171a8d1094b05300ae88d2d8362046864fd956c85be2858`

## Commit lokal

- Commit SHA (entry commit): `0bc23d7a92b2ac71000a335a1c808df84b297015`
  BUILD-REPORT.md kemudian diperbarui dengan SHA ini dalam commit lanjutan —
  lihat `git log` untuk HEAD final.

## Daftar file

- `main.ts`
- `entry.txt`
- `README.md`
- `LICENSE` (MIT, baris pertama `SPDX-License-Identifier: MIT`)
- `.makefun/owner.json` (wallet `2cy7DSBQwGoXa3w7qEr9VgtxhjLCF8KqpCRc3opcpFTt`)
- `requirements.json`
- `BUILD-REPORT.md`
- `prompt.txt`
- `bundle-staging/` (kosong)
- `parent-chats/` (kosong)

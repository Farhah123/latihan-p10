# Latihan P10 — Detektif Bug (Katalog Karya)

Praktikum Pemrograman Visual (TB033109), Tugas P10.

## Cara menjalankan
Buka `index.html` di Chrome. Butuh internet untuk Bootstrap (CDN).

## Ringkasan perbaikan
| Bug | Commit | Pesan |
|---|---|---|
| G1 | ab9ed80 | chore(aset): folder assets, nama logo.svg, path logo |
| G2 | af20ff3 | fix(layout): class row pada #galeri |
| G3 | f18aea5 | fix(filter): pakai variabel filterKategori |
| G4 | f1eb084 | fix(jumlah): hitung dari hasil saringan |
| G5 | 520b527 | fix(detail): event delegation |
| G6 | 3ddb7b6 | fix(cari): pencarian tidak peka huruf besar-kecil |

Cabang `fix/katalog` digabung ke `main` lewat merge `b629094`.
Catatan lengkap bukti ada di [DEBUG_LOG.md](DEBUG_LOG.md).

## Catatan riwayat
- `9c6eb3d` adalah commit pertama (kode asli dari lampiran).
- `e003f29` hanya merapikan spasi dan akhir baris `index.html`; tidak ada perbaikan.

## Bantuan AI
Saya memakai Claude (Anthropic) sebagai pemandu belajar: menjelaskan cara memakai DevTools dan git, dan memberi contoh kode perbaikan G3–G6 yang saya uji sendiri.
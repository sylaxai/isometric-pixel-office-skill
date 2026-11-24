# Isometric Pixel Office — skill

Skill untuk membangun **ruang kantor isometrik 3D bergaya pixel-art** sebagai halaman web (Three.js): lantai kayu, meja + monitor CRT, whiteboard, jalan + mobil, gedung tetangga berbalkon, dan hero chibi kantor yang menari dengan koreografi keyframe.

Skill ini **generik** — hanya mengajari cara membuat *ruangannya*. Siapa yang bekerja di ruangan itu, data apa yang tampil di papan status, dan dari mana datanya berasal, semuanya diputuskan pemakai skill.

## Isi
- `SKILL.md` — panduan utama (prinsip, alur kerja, aturan).
- `references/room-layout.md` — susunan ruangan, palet, proporsi.
- `references/rendering.md` — aturan gambar tajam (anti-buram).
- `references/dance-choreography.md` — sistem tari keyframe hero chibi.
- `template/index.html` — starter minimal yang langsung jalan di browser (Three.js via CDN): ruangan isometrik + 1 hero dengan 2 gerakan tari (Ombak, Putar) + kontrol.

## Pakai
1. Salin folder ini ke `~/workspace/custom-skills/isometric-pixel-office/` (atau lokasi skill lain).
2. Minta agen membangun ruangan mengikuti `SKILL.md`, dengan gambar referensi bila ada.
3. Kembangkan dari `template/index.html` — jangan mulai dari nol.

## Pelajaran yang diabadikan
- **Jangan downscale lalu upscale** — menggambar adegan di 1/3 resolusi lalu diperbesar dengan `image-rendering: pixelated` membuat semuanya buram. Render di resolusi penuh, pixel ratio perangkat, antialiasing aktif.
- **Tari itu koreografi** — gerakan bernama + tempo + keyframe, bukan goyang satu sumbu.
- **Referensi menang** — bila pemakai memberi gambar, ruangan harus semirip mungkin dari semua aspek, termasuk palet dan elemen luar (mobil, AC, poster, balkon).

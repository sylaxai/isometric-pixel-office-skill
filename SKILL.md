---
name: isometric-pixel-office
description: Bangun ruang kantor isometrik 3D bergaya pixel-art sebagai halaman web (Three.js): lantai kayu, meja + monitor CRT, whiteboard, jalan + mobil, gedung tetangga berbalkon, dan hero chibi kantor yang menari dengan koreografi keyframe. Generik — tanpa kaitan dengan proyek atau data apa pun; isi ruangan (agen, status, data) dipasok pemakai skill.
---

# Isometric Pixel Office — ruang kantor isometrik 3D pixel-art

Skill untuk membangun SATU ruangan kantor isometrik 3D bergaya pixel-art sebagai halaman web interaktif. Hasilnya diorama kantor yang bisa diputar/diperbesar, berisi meja kerja, hero chibi yang menari, dan papan status. Skill ini generik: ia hanya mengajari cara membuat RUANGANNYA. Siapa yang bekerja di ruangan itu, data apa yang tampil di papan status, dan dari mana datanya berasal — semuanya diputuskan pemakai skill, bukan skill ini.

## Kapan dipakai
- Pemakai minta "ruang kantor", "kantor isometrik", "kantor 3D pixel-art", "ruangan untuk tim/agen bekerja", atau menunjuk gambar referensi kantor isometrik.
- Bukan untuk kantor 2D top-down (itu ranah my-virtual-office), bukan untuk dashboard data (itu ranah data_dashboard), bukan untuk ruangan non-kantor.

## Hasil yang dibangun
- Satu halaman web (artifact web fullstack bila ada data live / refresh terjadwal; static bila isi tetap).
- Diorama isometrik 3D: kamera isometrik (azimuth ~45°, elevasi ~35°), bisa orbit + zoom.
- Elemen ruangan (lihat `references/room-layout.md`): lantai kayu plank terang, dinding krem + jendela, meja putih + monitor CRT putih, whiteboard, meja rapat, tumpukan kertas/kotak, karpet merah di pintu, tanaman/semak hijau di tepi, unit AC dinding, poster berbingkai, jalan di luar dengan mobil, gedung tetangga (balkon + jendela biru), pohon hijau.
- Hero: pekerja kantor chibi (topi, jaket) yang MENARI di tengah ruangan — koreografi keyframe betulan, bukan goyang asal-asalan (lihat `references/dance-choreography.md`).
- Kontrol: pilih agen/hero (sorot + papan status), ganti gerakan tari, jeda tari, putar kamera, cek data (bila ada sumber live).

## Prinsip desain
1. **Referensi dulu.** Bila pemakai memberi gambar referensi, ruangan HARUS semirip mungkin dengan gambar itu dari semua aspek: palet warna, perabot, susunan, dan elemen luar (jalan, mobil, gedung). Jangan mengganti palet terang referensi dengan palet gelap/cokelat.
2. **Tari itu koreografi, bukan goyang.** Setiap gerakan tari punya nama, tempo (BPM), dan keyframe yang jelas (lihat `references/dance-choreography.md`). Gerakan asal-asalan (satu sumbu bolak-balik) tidak cukup.
3. **Tajam, jangan buram.** Rendering HARUS tajam (lihat `references/rendering.md`). Pelajaran pahit: menggambar adegan di 1/3 resolusi lalu diperbesar dengan gaya pixelated membuat semuanya buram — jangan pernah lakukan itu.
4. **Data live hanya dari sumber yang pemakai tunjuk.** Papan status menampilkan data sungguhan dari sumber yang pemakai beri (API, file, action). Jangan mengarang angka. Bila tidak ada sumber, papan status menampilkan "belum ada data", bukan angka palsu.
5. **Satu ruangan, satu tujuan.** Skill ini membangun ruangannya saja. Logika bisnis (apa yang dikerjakan agen, dari mana datanya) milik pemakai / skill lain.

## Alur kerja
1. **Kumpulkan brief:** gambar referensi (bila ada), siapa hero/agennya (nama + peran + warna topi/pakaian), gerakan tari apa saja, data apa yang tampil di papan status + sumbernya, perlu refresh berkala atau tidak.
2. **Bangun ruangan** mengikuti `references/room-layout.md` — mulai dari lantai + dinding, lalu perabot besar (meja, whiteboard), lalu detail (AC, poster, tanaman), lalu luar ruangan (jalan, mobil, gedung tetangga, pohon).
3. **Bangun hero + tari** mengikuti `references/dance-choreography.md` — model chibi sederhana (kepala, topi, badan, lengan, kaki), 2–3 gerakan bernama dengan keyframe, kontrol ganti/jeda.
4. **Rendering tajam** mengikuti `references/rendering.md` — resolusi penuh, pixel ratio perangkat, antialiasing, filter tekstur linear + anisotropik, soft shadow.
5. **Kontrol + papan status:** pilih hero (klik atau panel), ganti gerakan, jeda, orbit/zoom kamera, tombol cek data manual bila ada sumber live.
6. **Verifikasi:** buka halaman, periksa (a) semua elemen referensi ada, (b) teks terbaca tajam, (c) tari bergerak sebagai koreografi (bukan goyang), (d) semua kontrol merespons, (e) tidak ada error konsol. Bandingkan dengan gambar referensi berdampingan bila ada.

## Template
`template/index.html` — starter minimal yang langsung jalan: adegan isometrik Three.js (lantai kayu, 2 meja + CRT, whiteboard, jalan + 1 mobil, gedung tetangga), satu hero chibi dengan 2 gerakan tari (Ombak, Putar), kontrol ganti/jeda + orbit. Salin dan kembangkan — jangan mulai dari nol.

## Yang TIDAK dilakukan skill ini
- Tidak menentukan siapa agen/pekerjanya, tidak mengambil data dari sumber mana pun, tidak memutuskan logika bisnis.
- Tidak memakai Docker (berjalan sebagai halaman web biasa).
- Tidak mengunggah/menerbitkan apa pun tanpa perintah pemakai.

# Rendering — aturan gambar tajam (anti-buram)

Pelajaran dari build nyata: adegan yang digambar di 1/3 resolusi lalu diperbesar dengan `image-rendering: pixelated` tampak BURAM di layar pemakai, walau di layar pembuatnya terlihat "pixel-art". Jangan ulangi.

## Wajib
- **Resolusi penuh:** renderer menggambar pada ukuran penuh kontainer (`setSize` pada ukuran kontainer asli, tanpa faktor downscale).
- **Pixel ratio perangkat:** `setPixelRatio(Math.min(window.devicePixelRatio, 2))` — tajam di layar retina tanpa biaya berlebih.
- **Antialiasing aktif:** `antialias: true` pada renderer.
- **Tekstur kanvas linear:** tekstur yang digambar via canvas (lantai kayu, whiteboard, poster, layar CRT, wajah agen) memakai `LinearFilter` + `LinearMipmapLinearFilter` dan `anisotropy` 8 — BUKAN `NearestFilter`.
- **Bayangan lembut:** `PCFSoftShadowMap`.
- **Tanpa `image-rendering: pixelated`** pada kanvas WebGL, dan tanpa filter `blur()` di CSS adegan.

## Jangan
- Jangan downscale lalu upscale (sumber utama buram).
- Jangan memakai `NearestFilter` untuk tekstur kanvas yang dibaca dari dekat.
- Jangan menutup kekurangan resolusi dengan efek blur / depth-of-field.
- Jangan mengecilkan kanvas lewat CSS di bawah ukuran rendernya (membuat teks dan garis kabur).

## Cek sebelum serah
- Perbesar (zoom) adegan: garis lantai, teks whiteboard, dan wajah hero tetap terbaca.
- Bandingkan tangkapan layar dengan gambar referensi berdampingan: tidak ada bagian yang kabur.
- Di layar ponsel (portrait): ruangan tetap tajam; bila framing memotong tepi, pastikan zoom/orbit bisa menampilkan seluruh adegan.

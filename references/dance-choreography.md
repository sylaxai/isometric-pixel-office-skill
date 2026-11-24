# Dance Choreography — hero menari dengan koreografi keyframe

Hero kantor menari dengan koreografi betulan, bukan goyang asal-asalan. Setiap gerakan punya nama, tempo, dan keyframe.

## Model hero (chibi, sederhana)
- Kepala besar (~40% tinggi), topi (warna khas hero), badan/jaket, lengan, kaki.
- Bagian tubuh dipisah sebagai grup agar bisa dianimasikan sendiri-sendiri: kepala, lengan kiri, lengan kanan, badan, kaki kiri, kaki kanan.
- Tinggi total ~1,2 satuan; hero berdiri di tengah ruangan (di depan cluster meja).

## Gerakan (minimal 2–3, masing-masing bernama)
- **Ombak:** badan bergoyang kiri–kanan seperti ombak, lengan mengikuti berlawanan arah, kepala mengangguk halus. Tempo 118 BPM.
- **Putar:** hero berputar 360° sambil lengan terangkat, lalu kembali menghadap kamera. Tempo 118 BPM.
- **Goyang:** langkah kecil ke kiri–kanan bergantian, lutut menekuk, lengan mengayun. Tempo 118 BPM.
- Setiap gerakan didefinisikan sebagai keyframe per bagian tubuh (rotasi/posisi pada ketukan), diulang (loop) mulus — akhir loop kembali ke pose awal tanpa lompatan.

## Kontrol
- Tombol ganti gerakan (nama gerakan tampil di tombol/label).
- Tombol jeda / lanjut tari (status berubah, mis. "Menari" → "Istirahat").
- Memilih hero/agen (klik hero atau panel) menyorot hero itu dan memperbarui papan status.
- Transisi antar gerakan: potong di ketukan (tidak ada pose membeku di tengah).

## Aturan
- Jangan membuat "tari" satu sumbu bolak-balik — itu goyang, bukan koreografi.
- Gerakan harus terlihat benar di tangkapan diam sekalipun (pose di tengah gerakan tetap masuk akal).
- Tempo konsisten antar gerakan (satu BPM untuk semua gerakan) supaya pergantian terasa mulus.
- Bila ada beberapa hero, masing-masing bisa punya gerakan aktif sendiri; hero yang tidak dipilih tetap menari (atau istirahat sesuai statusnya).

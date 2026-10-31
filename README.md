# Remi Fotoku

Game kartu remi di browser (HP maupun komputer) dengan foto sendiri di punggung kartu, As, J, Q, dan K. Satu file `index.html`, tanpa build, tanpa dependensi.

## Cara pasang di GitHub Pages

1. Buat repo baru, unggah `index.html` dan folder `foto/`.
2. Settings → Pages → Source: branch `main`, folder `/ (root)`.
3. Tunggu satu-dua menit, lalu buka `https://USERNAME.github.io/NAMA-REPO/`.

## Mengganti foto untuk semua pemain

Taruh file gambar di folder `foto/` dengan nama persis berikut (format `.jpg`, `.jpeg`, `.png`, atau `.webp`):

| File | Dipakai untuk |
|------|---------------|
| `back` | punggung kartu |
| `as` | kartu As |
| `j` | kartu J |
| `q` | kartu Q |
| `k` | kartu K |

Contoh: `foto/back.jpg`, `foto/q.png`. File yang tidak ada akan tampil sebagai kartu klasik. Setelah commit, perubahan muncul bagi semua pemain (kalau belum berubah, refresh paksa karena cache browser).

Saran ukuran: potret rasio 5:7, misalnya 500×700 piksel, di bawah 300 KB per file.

## Panel Admin di dalam game

Tombol **Admin** (PIN awal `1234`) dipakai untuk mencoba foto langsung dari galeri HP **hanya di perangkat itu**, berguna sebagai pratinjau sebelum kamu commit ke repo. Tombol **Reset** menghapus foto coba itu dan kembali ke foto dari repo.

PIN hanya tersimpan di browser, jadi bukan pengaman sungguhan. Kontrol yang sebenarnya adalah siapa yang boleh commit ke repo. Untuk mengganti PIN bawaan, cari `'1234'` di fungsi `getPin` pada `index.html`.

## Multiplayer online

Dari layar awal: satu orang menekan **Buat ruang online** dan mendapat kode 5 karakter. Teman memasukkan kode itu lalu menekan **Gabung**. Maksimal 4 pemain, dan tuan rumah bisa menambah Bot untuk mengisi kursi. Tuan rumah menekan **Mulai** saat semua sudah masuk.

Cara kerjanya: koneksi langsung antar-HP lewat WebRTC dengan [PeerJS](https://peerjs.com) (dimuat dari CDN jsDelivr, versi 1.5.4), jadi tidak perlu server sendiri dan GitHub Pages cukup. Tuan rumah memegang dek dan aturan; pemain lain hanya melihat kartunya sendiri. Catatan:

- Tuan rumah harus tetap membuka halaman. Kalau tuan rumah keluar, permainan berakhir untuk semua. Kalau pemain lain keluar, posisinya diganti Bot.
- Server perantara PeerJS gratis dan bersifat publik, tanpa jaminan layanan. Pada jaringan yang ketat (sebagian wifi kantor atau kampus) koneksi bisa gagal karena tidak ada server TURN.
- Kode ruang hanya berlaku selama tuan rumah online.

## Aturan main

Masing-masing 7 kartu. Tiap giliran ambil 1 kartu (dari dek atau tumpukan buang), lalu buang 1. Menang bila 7 kartu tersisa terbagi jadi set (angka sama, 3–4 kartu beda jenis) atau urutan (satu jenis, berurutan, minimal 3). As bisa di bawah 2 atau di atas K.

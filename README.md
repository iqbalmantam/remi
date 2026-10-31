# Remi Fotoku

Kumpulan permainan kartu remi di browser (HP maupun komputer) dengan foto sendiri di kartu. Satu file `index.html`, tanpa build.

## Pilihan permainan

| Permainan | Pemain | Ringkas | Skor ronde |
|-----------|--------|---------|------------|
| Remi Klasik | 2–4 | 7 kartu, ambil 1 buang 1, menang bila semua kartu jadi set/urutan | 10 + total poin sisa kartu lawan |
| Remi Joker | 2–4 | Seperti Klasik + 2 Joker pengganti kartu apa saja | 10 + sisa poin lawan (Joker sisa = 15) |
| Gin Remi | 2 | 10 kartu, **Ketuk** bila poin tak berpasangan ≤ 10 | Selisih poin; Gin (0) +25; disalip +25 untuk lawan |
| Delapan Gila | 2–4 | Cocokkan angka/jenis; 8 ganti jenis, 2 = lawan ambil 2, As = lewati | Total nilai kartu sisa lawan (8 = 50, J/Q/K = 10, As = 1) |

Semua permainan memakai skor kumulatif per pemain. Match selesai saat ada yang mencapai **100 poin** (ubah nilai `tg` pada objek `MODES` di `index.html`). Nilai kartu: As 1, 2–10 sesuai angka, J/Q/K 10.

## Pasang di GitHub Pages

Ganti `index.html` di repo dengan file ini, lalu commit. Pages memperbarui sendiri dalam 1–2 menit (refresh paksa bila masih tampilan lama).

## Foto kartu

Taruh gambar di folder `foto/` dengan nama persis berikut (`.jpg`, `.jpeg`, `.png`, atau `.webp`):

| File | Dipakai untuk |
|------|---------------|
| `back` | punggung kartu |
| `as` | As |
| `j` | J |
| `q` | Q |
| `k` | K |
| `joker` | Joker (mode Remi Joker) |

Slot kosong tampil sebagai kartu klasik. Saran ukuran: potret 5:7, misalnya 500×700 piksel, di bawah 300 KB.

Tombol **Admin** (PIN awal `1234`) dipakai untuk mencoba foto dari galeri hanya di perangkat itu. PIN tersimpan di browser dan bukan pengaman sungguhan. Untuk mengganti PIN bawaan, cari `'1234'` di fungsi `getPin`.

## Simpan foto ke GitHub dari panel Admin

1. Di GitHub: Settings → Developer settings → Personal access tokens → Fine-grained tokens → Generate new token. Pilih *Only select repositories* → `remi`, izin **Contents: Read and write**, masa berlaku pendek (misalnya 30 hari).
2. Di panel Admin tempel token, tekan **Simpan**, pilih foto, lalu tekan **Unggah foto ke GitHub**.
3. Foto terunggah ke folder `foto/` dan muncul untuk semua pemain dalam 1–2 menit.

Token hanya disimpan di browser perangkat itu, tidak ada di kode. Jangan dibagikan ke siapa pun dan jangan dipakai di perangkat bersama. Ganti `GH` di `index.html` bila nama repo berbeda.

## Multiplayer online

Pilih permainan, tekan **Buat ruang online**, lalu bagikan kode 5 karakter. Teman memasukkan kode dan menekan **Gabung**. Tuan rumah bisa menambah Bot, lalu menekan **Mulai**.

Koneksi langsung antar-HP lewat [PeerJS](https://peerjs.com) (jsDelivr, versi 1.5.4). Tuan rumah memegang dek dan aturan. Bila tuan rumah keluar, permainan berakhir; bila pemain lain keluar, posisinya diganti Bot. Server perantara PeerJS gratis tanpa jaminan layanan, dan jaringan yang ketat bisa menggagalkan koneksi.

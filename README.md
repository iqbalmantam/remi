# Remi Fotoku

Kumpulan permainan kartu remi di browser (HP maupun komputer) dengan foto sendiri di kartu. Satu file `index.html`, tanpa build.

## Pilihan permainan

| Permainan | Pemain | Ringkas | Skor ronde |
|-----------|--------|---------|------------|
| Remi Klasik | 2–6 | 7 kartu, ambil 1 buang 1, menang bila semua kartu jadi set/urutan | 10 + total poin sisa kartu lawan |
| Remi Joker | 2–6 | Seperti Klasik + 2 Joker pengganti kartu apa saja | 10 + sisa poin lawan (Joker sisa = 15) |
| Gin Remi | 2 | 10 kartu, **Ketuk** bila poin tak berpasangan ≤ 10 | Selisih poin; Gin (0) +25; disalip +25 untuk lawan |
| Delapan Gila | 2–6 | Cocokkan angka/jenis; 8 ganti jenis, 2 = lawan ambil 2, As = lewati | Total nilai kartu sisa lawan (8 = 50, J/Q/K = 10, As = 1) |
| Texas Hold'em | 2–8 | Poker sungguhan: 2 kartu pribadi + 5 kartu bersama, taruhan Fold/Check/Call/Raise/All-in, side pot | Chip (mulai 1000, blind 10/20 naik tiap 5 tangan); juara = pemain terakhir yang punya chip |
| Omaha | 2–8 | 4 kartu pribadi, wajib pakai tepat 2 + 3 kartu bersama, taruhan pot-limit | Chip, sama seperti Hold'em |
| Short Deck (6+) | 2–8 | Hold'em dengan dek 36 kartu (tanpa 2–5); Flush > Full House, Tiga Sejenis > Straight | Chip |
| Poker 5 Kartu | 2–8 | 5 kartu, taruhan, tukar hingga 3 kartu, taruhan terakhir, adu kartu | Chip |

Permainan remi memakai skor kumulatif per pemain; Hold'em memakai chip. Match selesai saat ada yang mencapai **100 poin** (ubah nilai `tg` pada objek `MODES` di `index.html`). Nilai kartu: As 1, 2–10 sesuai angka, J/Q/K 10.

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

## Tampilan

Meja berbentuk pil dengan bingkai abu gelap dan felt bertekstur yang warnanya berbeda tiap permainan. Tiap kursi menampilkan nama di atas avatar bercincin emas (cincin terisi mengikuti kemajuan skor), jumlah chip di bawahnya, dan kartu pemain di dekatnya. Di akhir ronde kartu semua pemain terbuka dan muncul gelembung skor (+119, -20, ±0) di tiap kursi, dengan mahkota untuk pemenang.

Kartu di tanganmu bertumpuk dalam satu baris. Pada Remi Klasik, Remi Joker, dan Gin Remi, kartu yang sudah membentuk set atau urutan otomatis dikelompokkan dan diberi pita warna di bawahnya (oranye, biru, hijau, dan seterusnya), sedangkan kartu sisa ada di ujung. Kartu angka memakai susunan pip seperti kartu asli, J/Q/K bergambar tokoh, dan punggung kartu bermonogram R.

Tombol gir di kiri atas membuka suara dan keluar, tombol **Skor** menampilkan papan skor kapan saja, dan pojok kanan atas menunjukkan chip atau poinmu. Semua gambar dibuat dengan SVG/CSS di dalam `index.html`. Animasi mati otomatis bila perangkat memakai pengaturan "kurangi gerakan".

## Suara

Semua suara dibuat langsung oleh browser (Web Audio), jadi tidak ada file audio tambahan. Efek yang ada: kocok dan bagi kartu, kartu diletakkan, chip jatuh (lebih ramai saat raise atau all-in), ketukan check, fold, lonceng saat giliranmu, serta nada menang, kalah, dan juara match. Musik latar lounge pelan bisa dinyalakan, bawaannya mati. Dua tombol bulat di pojok kanan atas layar awal dan layar permainan mengatur **efek suara** dan **musik**; pilihannya diingat di perangkat. Browser baru mengizinkan suara setelah layar disentuh pertama kali, dan suara berhenti otomatis saat tab disembunyikan.

## Karakter pemain

Di layar awal tiap pemain memilih salah satu dari 12 karakter bergambar (ada topi, kacamata, hijab, dan lainnya), atau memakai fotonya sendiri lewat tombol **Foto**. Karakter tampil di kursi meja dan di daftar ruang, dan pilihannya diingat di perangkat. Bot mendapat karakter acak yang tidak kembar. Foto avatar diperkecil menjadi 96×96 piksel sebelum dikirim ke pemain lain.

## Simpan foto ke GitHub dari panel Admin

1. Di GitHub: Settings → Developer settings → Personal access tokens → Fine-grained tokens → Generate new token. Pilih *Only select repositories* → `remi`, izin **Contents: Read and write**, masa berlaku pendek (misalnya 30 hari).
2. Di panel Admin tempel token, tekan **Simpan**, pilih foto, lalu tekan **Unggah foto ke GitHub**.
3. Foto terunggah ke folder `foto/` dan muncul untuk semua pemain dalam 1–2 menit.

Token hanya disimpan di browser perangkat itu, tidak ada di kode. Jangan dibagikan ke siapa pun dan jangan dipakai di perangkat bersama. Ganti `GH` di `index.html` bila nama repo berbeda.

## Multiplayer online

Pilih permainan, tekan **Buat ruang online**, lalu bagikan kode 5 karakter. Teman memasukkan kode dan menekan **Gabung**. Tuan rumah bisa menambah Bot, lalu menekan **Mulai**.

Koneksi langsung antar-HP lewat [PeerJS](https://peerjs.com) (jsDelivr, versi 1.5.4). Tuan rumah memegang dek dan aturan. Bila tuan rumah keluar, permainan berakhir; bila pemain lain keluar, posisinya diganti Bot. Server perantara PeerJS gratis tanpa jaminan layanan, dan jaringan yang ketat bisa menggagalkan koneksi.

# Catatan Pembacaan Referensi — Tahap 5

**Topik Tugas Akhir:** Optimasi Rute Evakuasi Dinamis pada Lingkungan Gedung Kampus Menggunakan ST-HGAT dan PPO.

**Tanggal pemeriksaan:** 10 November 2026

## Cakupan

Tahap ini melanjutkan pembacaan dari folder `Jurnal-Pendukung-Lainnya/` karena folder `2.9-Evaluasi-Kinerja-Evakuasi/` dan `2.10-Penelitian-Terdahulu/` pada repository saat diperiksa hanya berisi `.gitkeep` dan belum memiliki PDF.

Dua publikasi yang ditelaah:
1. Marliza dan Ahmad (2024), model Cellular Automata untuk evakuasi pedestrian di Gedung Terpadu FMIPA UNP dengan mempertimbangkan kepanikan.
2. Muttaqien et al. (2024), tinjauan penggunaan AnyLogic/Agent-Based Model untuk evaluasi akses dan rute evakuasi.

Kedua artikel dapat dibaca dari PDF yang tersedia secara publik melalui laman penerbit. Pembacaan ini tidak berarti PDF telah dipindahkan atau ditambahkan ke folder 2.9/2.10.

## A. R-27 — Marliza dan Ahmad (2024)

**Judul:** Model Cellular Automata untuk Masalah Evakuasi Pedestrian di Gedung Terpadu FMIPA UNP dengan Mempertimbangkan Kepanikan  
**Publikasi:** *MATHunesa: Jurnal Ilmiah Matematika*, Vol. 12, No. 1, hlm. 101–109 (2024).  
**DOI:** https://doi.org/10.26740/mathunesa.v12n1.p101-109  
**Lokasi repository:** `Jurnal-Pendukung-Lainnya/`  
**Status:** Dibaca dari PDF lengkap yang tersedia pada laman penerbit (9 halaman).

### Tujuan dan data
Penelitian menyusun model Cellular Automata untuk mengamati dinamika evakuasi pedestrian dengan memperhatikan kondisi normal dan panik. Data lingkungan berupa gambar detail Gedung Terpadu FMIPA UNP yang diperoleh dari pihak Rektorat UNP. Denah dimodelkan menjadi representasi 2D dan simulasi dibuat menggunakan MATLAB.

### Representasi dan metode
- Ruang direpresentasikan sebagai grid sel persegi.
- Setiap sel dapat berstatus sebagai hambatan, pintu keluar, ruang kosong, atau pejalan kaki.
- Status sel pada tabel penelitian: -2 untuk hambatan, -1 untuk pintu keluar, 0 untuk kosong, dan 1 untuk pejalan kaki.
- Pergerakan lokal mempertimbangkan Moore Neighborhood.
- Model memakai static floor field yang dihitung berdasarkan jarak sel ke pintu keluar terdekat.
- Dynamic floor field merepresentasikan kepadatan pejalan kaki pada sel.
- Probabilitas transisi memperhitungkan preferensi gerak, dynamic floor field, static floor field, dan status keterisian sel.
- Parameter (k_s) dan (k_d) digunakan untuk mengatur pengaruh bidang lantai statis dan dinamis terhadap kecenderungan pergerakan.

Persamaan probabilitas transisi yang dicantumkan:
[
p_{ij}=Nexp(k_DD_{ij})exp(k_SS_{ij})(1-n_{ij})
]
dengan (N) sebagai normalisasi, (D_{ij}) nilai dynamic floor field, (S_{ij}) nilai static floor field, dan (n_{ij}) indikator keterisian sel.

### Skenario dan hasil
- Simulasi menggunakan 50 orang.
- Denah yang dijelaskan memiliki luas 44 × 21 meter persegi dan dua pintu keluar; ilustrasi hasil menampilkan lantai 1.
- Pada skenario normal, parameter yang digunakan adalah (k_s=2) dan (k_d=1).
- Pada skenario panik dalam eksperimen penelitian ini, parameter yang digunakan adalah (k_s=1) dan (k_d=0).
- Waktu evakuasi simulasi kondisi normal sekitar 42 detik.
- Waktu evakuasi simulasi kondisi panik sekitar 68 detik.
- Penulis mengamati perbedaan pola pergerakan: kondisi normal terlihat bergerak berkelompok, sedangkan kondisi panik bergerak tanpa pola kelompok yang sama dan mengikuti jejak pejalan kaki sebelumnya.

### Catatan parameter yang harus dibaca hati-hati
Pada bagian pembahasan, penulis juga mengutip pengaturan dari penelitian terdahulu Mu’arifin et al.: kondisi panik (k_s=1, k_d=2), sedangkan kondisi normal (k_s=2, k_d=1). Namun, eksperimen Marliza dan Ahmad sendiri menyebut (k_s=1, k_d=0) untuk kondisi panik. Kedua pengaturan itu tidak boleh dicampur; jika angka parameter akan dikutip, sebutkan apakah angka tersebut berasal dari penelitian terdahulu yang mereka rujuk atau dari eksperimen Marliza dan Ahmad.

### Keterbatasan dan kehati-hatian
- Penelitian merupakan simulasi CA berbasis grid, bukan pengujian lapangan evakuasi aktual.
- Eksperimen yang dijelaskan menggunakan 50 pejalan kaki dan representasi denah 2D.
- Model CA mengasumsikan ruang diskret dan interaksi lokal; representasi ini berbeda dari graf heterogen pada rancangan penelitian kita.
- Artikel tidak menguji ST-HGAT, GNN, PPO, atau pembelajaran policy.
- Waktu 42 dan 68 detik hanya hasil simulasi untuk konfigurasi studi kasus tersebut; angka ini tidak dapat dijadikan target atau pembanding langsung untuk gedung kampus yang berbeda.

### Relevansi untuk Tugas Akhir
- Mendukung bahwa waktu evakuasi dapat berubah akibat perubahan perilaku/parameter kepanikan.
- Memberikan contoh penggunaan waktu evakuasi sebagai salah satu metrik evaluasi.
- Menunjukkan bahwa kepadatan, keterisian ruang, jarak ke pintu keluar, dan probabilitas perpindahan dapat memengaruhi hasil simulasi.
- Dapat menjadi referensi untuk membahas perilaku penghuni dan evaluasi kinerja evakuasi, tetapi bukan metode yang harus diadopsi.

## B. R-28 — Muttaqien et al. (2024)

**Judul:** Evaluation of Emergency Access Evacuation Routes Using Agent-Based Model Application  
**Publikasi:** *JARINA: Journal of Artificial Intelligence in Architecture*, hlm. 71–80 (2024).  
**DOI:** https://doi.org/10.24002/jarina.v3i2.8308  
**Lokasi repository:** `Jurnal-Pendukung-Lainnya/`  
**Status:** Dibaca dari PDF lengkap yang tersedia pada laman penerbit (10 halaman).

### Tujuan dan metode
Artikel bertujuan meninjau penggunaan Agent-Based Artificial Intelligence/Agent-Based Modelling pada perangkat lunak AnyLogic untuk mengevaluasi akses dan rute evakuasi. Metode utama yang dinyatakan adalah journal review, yaitu mengumpulkan dan membahas penelitian-penelitian terkait. Artikel ini bukan eksperimen baru yang menjalankan simulasi pada satu gedung dan menghasilkan data evakuasi primer.

### Konsep ABM dan alur pemodelan
- ABMS merepresentasikan entitas sebagai agent dengan aturan perilaku; agent dapat berinteraksi dan memengaruhi perilaku satu sama lain.
- Dalam simulasi evakuasi AnyLogic, orang di dalam bangunan dapat direpresentasikan sebagai agent individual.
- Artikel menjelaskan tiga tahap umum: membangun model fisik sesuai layout lingkungan, mengatur alur/perilaku pedestrian, dan menetapkan parameter simulasi.
- Parameter dapat mencakup proporsi umur/jenis kelamin serta kecepatan berjalan yang disesuaikan dengan kelompok.
- AnyLogic menyediakan komponen untuk merepresentasikan ruang, pedestrian, agent, proses, resource, dan queue.

### Sintesis faktor dan evaluasi
Artikel merangkum penelitian terdahulu yang menggunakan AnyLogic pada berbagai konteks, seperti stasiun, nightclub, fasilitas kesehatan, museum, bandara, dan kerumunan besar.
Faktor yang dibahas sebagai berpengaruh terhadap efisiensi evakuasi meliputi:
- jumlah orang;
- kepadatan;
- kecepatan pergerakan;
- jumlah dan aksesibilitas pintu keluar;
- tangga darurat;
- pencahayaan;
- hambatan fisik, pintu terkunci/terhalang, dan overcrowding.

Artikel juga menyebut bahwa simulasi dapat dipakai untuk memeriksa waktu yang dibutuhkan agent mencapai rute atau titik aman serta mengidentifikasi potensi bottleneck.

### Kesimpulan dan keterbatasan sebagai sumber
- Kesimpulan penulis menyatakan AnyLogic dapat membantu mengevaluasi rute dan waktu evakuasi dalam berbagai konteks.
- Karena metode artikel berupa tinjauan literatur, klaim tersebut merupakan sintesis dari studi-studi yang dirujuk, bukan hasil eksperimen AnyLogic baru yang dilakukan oleh penulis artikel.
- Artikel tidak menyajikan satu protokol evaluasi kuantitatif yang terstandar untuk semua gedung.
- Artikel tidak menguji ST-HGAT, GNN, PPO, atau optimasi policy.
- Beberapa isi tabel hasil merupakan ringkasan singkat dari studi terdahulu; untuk mengutip angka spesifik dari studi-studi tersebut, sumber primer yang dirujuk perlu dibaca langsung.

### Catatan metadata
Terdapat ketidaksesuaian informasi volume pada dokumen yang tersedia:
- Header PDF menampilkan *Vol. 2, No. 2, August 2024*.
- Halaman OJS dan informasi sitasi artikel menampilkan *Vol. 3, No. 2, 2024*, hlm. 71–80.
- DOI dan rentang halaman cocok dengan artikel pada laman OJS, tetapi perbedaan volume ini perlu diverifikasi ke metadata penerbit sebelum daftar pustaka final ditetapkan. Jangan mengoreksinya diam-diam.

### Relevansi untuk Tugas Akhir
- Berguna sebagai referensi pendukung untuk faktor-faktor yang perlu dipertimbangkan saat mengevaluasi rute evakuasi.
- Mendukung pemakaian waktu mencapai titik aman dan identifikasi bottleneck sebagai aspek analisis.
- Menjadi contoh bahwa model pergerakan penghuni dapat menggunakan agent individual dengan atribut dan aturan perilaku.
- Karena sifatnya review, bobotnya lebih tepat sebagai referensi konseptual/pendukung, bukan penelitian terdahulu utama yang dibandingkan berdasarkan hasil eksperimen.

## C. Sintesis awal untuk subbab 2.9 Evaluasi Kinerja Evakuasi

Berdasarkan dua artikel tahap ini dan studi evakuasi yang telah dibaca pada tahap sebelumnya, indikator yang memiliki dukungan sumber antara lain:

1. **Waktu evakuasi:** Marliza dan Ahmad melaporkan durasi total pada skenario normal dan panik; Arifati et al. dan Hardiansyah et al. juga melaporkan waktu evakuasi pada studi simulasi masing-masing.
2. **Keberhasilan mencapai titik aman/keluar:** dapat dilaporkan sebagai jumlah atau proporsi penghuni yang berhasil mencapai tujuan, selama definisi keberhasilan dan kondisi terminasi ditetapkan dengan jelas.
3. **Kepadatan dan bottleneck:** beberapa sumber membahas kepadatan, konflik pergerakan, antrean, dan titik penyempitan sebagai faktor yang menghambat evakuasi.
4. **Keselamatan dan aksesibilitas rute:** perlu diperiksa apakah rute dapat dilalui dan apakah pintu/tangga/koridor tersedia; indikator keselamatan perlu didefinisikan secara operasional sebelum digunakan.
5. **Panjang/jarak rute:** relevan untuk membandingkan efisiensi jalur, tetapi dua artikel tahap ini tidak menyediakan definisi metrik panjang rute yang terstandardisasi.

Catatan: daftar di atas merupakan sintesis awal dari referensi yang telah dibaca, bukan standar evaluasi yang dinyatakan secara seragam oleh semua artikel. BAB III perlu menetapkan rumus, satuan, cara agregasi, dan skenario pengukuran setiap metrik.

## D. Kegunaan untuk subbab 2.10 Penelitian Terdahulu

- Marliza dan Ahmad dapat dimasukkan sebagai studi simulasi evakuasi gedung dengan CA dan faktor kepanikan. Informasi pembanding yang tersedia: objek Gedung Terpadu FMIPA UNP, 50 pejalan kaki, dua exit pada denah yang dijelaskan, MATLAB, dan hasil waktu 42 detik (normal) serta 68 detik (panik).
- Muttaqien et al. lebih tepat dimasukkan sebagai studi tinjauan pendukung tentang ABM/AnyLogic, bukan sebagai studi eksperimen dengan hasil kuantitatif baru.
- Untuk tabel penelitian terdahulu utama, prioritaskan artikel empiris/simulasi yang menjelaskan objek, metode, skenario, dan hasil terukur. Artikel review dapat ditempatkan sebagai pendukung atau dikecualikan dari tabel utama jika tabel difokuskan pada eksperimen.

## E. Status pembacaan setelah tahap 5

Berdasarkan inventarisasi 30 PDF:
- Dibaca penuh/isi utama: 17 publikasi.
- Dibaca sebagian: 3 publikasi (Rizian et al. 2026; Wang et al. 2024; Gao et al. 2022).
- Belum dibaca: 10 publikasi.

Tahap 5 menambahkan dua publikasi yang berada di folder `Jurnal-Pendukung-Lainnya/`. Folder `2.9-Evaluasi-Kinerja-Evakuasi/` dan `2.10-Penelitian-Terdahulu/` masih kosong pada saat pemeriksaan.

## F. Referensi tahap 5

- S. P. Marliza and D. Ahmad, “Model Cellular Automata untuk Masalah Evakuasi Pedestrian di Gedung Terpadu FMIPA UNP dengan Mempertimbangkan Kepanikan,” *MATHunesa: Jurnal Ilmiah Matematika*, vol. 12, no. 1, pp. 101–109, 2024, doi: 10.26740/mathunesa.v12n1.p101-109.
- I. Y. Muttaqien, S. Tanugraha, J. E. Puspitaningrum, and H. A. W. Manik, “Evaluation of Emergency Access Evacuation Routes Using Agent-Based Model Application,” *JARINA: Journal of Artificial Intelligence in Architecture*, pp. 71–80, 2024, doi: 10.24002/jarina.v3i2.8308. Volume metadata requires verification because the PDF header and OJS citation disagree.

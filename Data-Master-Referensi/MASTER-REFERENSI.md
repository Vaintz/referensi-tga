# Master Referensi Tugas Akhir

Dokumen ini menjadi indeks utama seluruh publikasi yang digunakan dalam penyusunan Tugas Akhir.

**Topik:** Optimasi Rute Evakuasi Dinamis pada Lingkungan Gedung Kampus Menggunakan ST-HGAT dan PPO.

## Petunjuk
- Satu baris untuk satu publikasi.
- Cantumkan nama file PDF dan lokasi foldernya.
- Tandai status pembacaan secara jujur: Belum dibaca, Metadata diperiksa, Dibaca sebagian, atau Dibaca penuh.
- Catat nomor halaman untuk temuan atau kutipan penting.
- Bedakan isi yang dinyatakan langsung oleh sumber dengan interpretasi penulis.
- Jangan menetapkan nomor sitasi IEEE final sebelum urutan kemunculan referensi dalam naskah ditetapkan.

## Daftar Referensi

| ID | Judul publikasi | Penulis | Tahun | Jurnal/konferensi | DOI/URL | Metode | Hasil utama | Relevansi subbab | File PDF/folder | Status pembacaan | Catatan halaman |
|---|---|---|---:|---|---|---|---|---|---|---|---|
| R001 |  |  |  |  |  |  |  |  |  | Belum dibaca |  |

## Catatan Sintesis per Subbab

### 2.1 Evakuasi Bencana pada Lingkungan Gedung
Pembacaan awal tersedia pada laporan tahap 1, khususnya tentang pengaruh tata letak gedung, pintu/tangga, kepanikan, pengetahuan penghuni, dan kepadatan.

### 2.2 Simulasi dan Pemodelan Pergerakan Penghuni
Pembacaan tersedia pada laporan tahap 1 dan tahap 5. Contoh yang dibaca meliputi ABM, CA, representasi grid, static/dynamic floor field, dan perilaku penghuni.

### 2.3 Teori Graf dan Pemodelan Lingkungan Evakuasi
Pembacaan tersedia pada laporan tahap 2. Sharma et al. membahas adjacency matrix/list/edge list; Jaeger membahas graf beratribut dan multi-relasional; Jiawei et al. membahas agregasi multi-hop pada GraphSAGE++.

### 2.4 Graph Neural Network
Pembacaan tersedia pada laporan tahap 2. Fathinezhad et al. membahas message passing dan integrasi GNN-DRL; Rizian et al. menjadi contoh aplikasi GAT pada klasifikasi dokumen, tetapi baru dibaca sebagian dari halaman artikel/abstrak.

### 2.5 ST-HGAT
Pembacaan tersedia pada laporan tahap 3. Zheng et al. membahas Dynamic GNN dan pembedaan DTDG/CTDG; Corradini et al. meninjau ST-GNN untuk forecasting/classification; Yang dan Peng mengusulkan STC-HGAT untuk rekomendasi sesi. Catatan penting: STC-HGAT bukan otomatis arsitektur ST-HGAT penelitian ini, dan pada paper Yang & Peng istilah ST-HGAT adalah varian ablation tanpa contrastive learning.

### 2.6 Reinforcement Learning
Pembacaan tersedia pada laporan tahap 4. Vidyasagar membahas MDP, reward, policy, Bellman, TD, dan Q-learning. Wang et al. (2024) baru ditelaah dari abstrak/metadata penerbit, belum PDF lengkap.

### 2.7 Proximal Policy Optimization
Pembacaan tersedia pada laporan tahap 4. Darmawan et al. dan Machmudi et al. memberi contoh penerapan PPO pada domain lain, tetapi keduanya bukan sumber primer yang memperkenalkan PPO. Machmudi et al. memiliki perbedaan angka hasil antara abstrak/kesimpulan dan tabel. Perlu menambahkan sumber primer PPO untuk landasan teori yang kuat.

### 2.8 Graph Reinforcement Learning
Pembacaan tersedia pada laporan tahap 4. Darvariu et al. membedakan optimasi struktur graf dan optimasi proses pada graf tetap; Nie et al. mengulas integrasi RL dan graph mining; Gao et al. memberi contoh GCN dengan Q-learning untuk pengambilan keputusan lalu lintas, tetapi PDF lengkap belum dibaca utuh.

### 2.9 Evaluasi Kinerja Evakuasi
Pembacaan awal tersedia pada laporan tahap 5. Marliza dan Ahmad melaporkan waktu evakuasi simulasi normal/panik serta menggunakan kepadatan dan probabilitas transisi. Muttaqien et al. merupakan tinjauan ABM/AnyLogic yang membahas waktu, kepadatan, bottleneck, aksesibilitas, pintu, tangga, dan hambatan. Metrik final dan rumusnya tetap harus ditetapkan pada BAB III.

### 2.10 Penelitian Terdahulu
Pembacaan dan seleksi awal tersedia pada laporan tahap 5 serta laporan tahap 1–4. Prioritaskan studi empiris/simulasi yang menyebut objek, metode, skenario, dan hasil terukur. Artikel review dapat dipakai sebagai pendukung, bukan diperlakukan sebagai eksperimen primer.

## Log Verifikasi
| Tanggal | ID referensi | Bagian yang diperiksa | Hasil/masalah |
|---|---|---|---|
| 10 November 2026 | Sharma2025 | PDF penerbit, 7 halaman | PDF mencantumkan 7 penulis; entri BibTeX hanya 4 penulis. |
| 10 November 2026 | Jaeger2023 | Halaman artikel Frontiers | Entri BibTeX sebaiknya bertipe @article, bukan @misc. |
| 10 November 2026 | Rizian2026 | Halaman artikel dan issue JUTIF | Sitasi artikel menampilkan Jan 2026, issue menyebut Desember 2025; PDF lengkap belum diperiksa. |
| 10 November 2026 | Zheng2025 | PDF penerbit, 18 halaman | Survei Dynamic GNN mengecualikan graf spatio-temporal dengan struktur tetap dan atribut node yang berubah. |
| 10 November 2026 | Corradini2026 | Preprint arXiv v4, bagian definisi/taksonomi/konstruksi graf/diskusi; metadata versi jurnal | Versi jurnal Neural Networks Vol. 195, Article 108269, Maret 2026; teks penuh yang ditelaah adalah preprint v4. |
| 10 November 2026 | Yang2024 | PDF penerbit, 16 halaman | Model utama bernama STC-HGAT; ST-HGAT adalah varian ablation tanpa contrastive learning. |
| 10 November 2026 | Wang2024 | Abstrak dan metadata PubMed/IEEE | PDF lengkap belum diperiksa; klaim dibatasi pada abstrak. |
| 10 November 2026 | Machmudi2025 | PDF JUTIF, 11 halaman | Angka latency dan responsiveness berbeda antara abstrak/kesimpulan dan tabel hasil. |
| 10 November 2026 | Darvariu2024 | PDF TMLR, 46 halaman | Membahas graph process optimization pada graf tetap, termasuk routing dan navigation. |
| 10 November 2026 | Nie2023 | Preprint arXiv v4, 22 halaman; metadata versi jurnal | Versi jurnal IEEE TETCI Vol. 7 No. 4, pp. 1065–1082, 2023. |
| 10 November 2026 | Gao2022 | Abstrak, metode, hasil, tabel dan kesimpulan yang terindeks pada halaman penerbit | PDF lengkap belum diperiksa utuh; status dibaca sebagian. |
| 10 November 2026 | Marliza2024 | PDF penerbit, 9 halaman | 50 pedestrian; waktu simulasi normal 42 detik dan panik 68 detik. Parameter panik dalam eksperimen paper berbeda dari parameter panik studi Mu’arifin yang dikutip. |
| 10 November 2026 | Muttaqien2024 | PDF penerbit, 10 halaman | Artikel menggunakan metode journal review, bukan eksperimen evakuasi baru. Header PDF menyebut Vol. 2 No. 2, sedangkan metadata OJS menyebut Vol. 3 No. 2. |

## Catatan Pembacaan

- [Laporan pembacaan tahap 1](./PEMBACAAN-REFERENSI-TAHAP-1.md).
- [Laporan pembacaan tahap 2](./PEMBACAAN-REFERENSI-TAHAP-2.md).
- [Laporan pembacaan tahap 3](./PEMBACAAN-REFERENSI-TAHAP-3.md).
- [Laporan pembacaan tahap 4](./PEMBACAAN-REFERENSI-TAHAP-4.md).
- [Laporan pembacaan tahap 5](./PEMBACAAN-REFERENSI-TAHAP-5.md).

**Status keseluruhan berdasarkan pemeriksaan sampai tahap 5:**
- Total PDF terinventarisasi di repository: 30.
- Dibaca penuh/isi utama: 17 publikasi.
- Dibaca sebagian: 3 publikasi (Rizian et al. 2026; Wang et al. 2024; Gao et al. 2022).
- Belum dibaca: 10 publikasi.
- Tahap 5 mencakup dua referensi pendukung terkait simulasi evakuasi dan evaluasi jalur.

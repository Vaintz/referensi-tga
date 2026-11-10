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
Pembacaan awal tersedia pada laporan tahap 1, dengan contoh ABM dan CA untuk merepresentasikan penghuni serta perilakunya.

### 2.3 Teori Graf dan Pemodelan Lingkungan Evakuasi
Pembacaan tersedia pada laporan tahap 2. Sharma et al. membahas adjacency matrix/list/edge list; Jaeger membahas graf beratribut dan multi-relasional; Jiawei et al. membahas agregasi multi-hop pada GraphSAGE++.

### 2.4 Graph Neural Network
Pembacaan tersedia pada laporan tahap 2. Fathinezhad et al. membahas message passing dan integrasi GNN-DRL; Rizian et al. menjadi contoh aplikasi GAT pada klasifikasi dokumen, tetapi baru dibaca sebagian dari halaman artikel/abstrak.

### 2.5 ST-HGAT
Pembacaan tersedia pada laporan tahap 3. Zheng et al. membahas Dynamic GNN dan pembedaan DTDG/CTDG; Corradini et al. meninjau ST-GNN untuk forecasting/classification; Yang dan Peng mengusulkan STC-HGAT untuk rekomendasi sesi. Catatan penting: STC-HGAT bukan otomatis arsitektur ST-HGAT penelitian ini, dan pada paper Yang & Peng istilah ST-HGAT adalah varian ablation tanpa contrastive learning.

### 2.6 Reinforcement Learning
Belum disusun.

### 2.7 Proximal Policy Optimization
Belum disusun.

### 2.8 Graph Reinforcement Learning
Belum disusun.

### 2.9 Evaluasi Kinerja Evakuasi
Belum disusun.

### 2.10 Penelitian Terdahulu
Belum disusun.

## Log Verifikasi
| Tanggal | ID referensi | Bagian yang diperiksa | Hasil/masalah |
|---|---|---|---|
| 10 November 2026 | Sharma2025 | PDF penerbit, 7 halaman | PDF mencantumkan 7 penulis; entri BibTeX hanya 4 penulis. |
| 10 November 2026 | Jaeger2023 | Halaman artikel Frontiers | Entri BibTeX sebaiknya bertipe @article, bukan @misc. |
| 10 November 2026 | Rizian2026 | Halaman artikel dan issue JUTIF | Sitasi artikel menampilkan Jan 2026, issue menyebut Desember 2025; PDF lengkap belum diperiksa. |
| 10 November 2026 | Zheng2025 | PDF penerbit, 18 halaman | Survei Dynamic GNN mengecualikan graf spatio-temporal dengan struktur tetap dan atribut node yang berubah. |
| 10 November 2026 | Corradini2026 | Preprint arXiv v4, bagian definisi/taksonomi/konstruksi graf/diskusi; metadata versi jurnal | Versi jurnal Neural Networks Vol. 195, Article 108269, Maret 2026; teks penuh yang ditelaah adalah preprint v4. |
| 10 November 2026 | Yang2024 | PDF penerbit, 16 halaman | Model utama bernama STC-HGAT; ST-HGAT adalah varian ablation tanpa contrastive learning. |

## Catatan Pembacaan

- [Laporan pembacaan tahap 1](./PEMBACAAN-REFERENSI-TAHAP-1.md).
- [Laporan pembacaan tahap 2](./PEMBACAAN-REFERENSI-TAHAP-2.md).
- [Laporan pembacaan tahap 3](./PEMBACAAN-REFERENSI-TAHAP-3.md).

**Status keseluruhan berdasarkan pemeriksaan sampai tahap 3:**
- Total PDF terinventarisasi di repository: 30.
- Dibaca penuh/isi utama: 10 publikasi.
- Dibaca sebagian: 1 publikasi (Rizian et al.; halaman artikel/abstrak dan metadata, belum PDF lengkap).
- Belum dibaca: 18 publikasi.
- Tahap 3 menyelesaikan pembacaan tiga referensi pada subbab 2.5 ST-HGAT.

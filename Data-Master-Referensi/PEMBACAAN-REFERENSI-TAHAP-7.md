# Catatan Pembacaan Referensi — Tahap 7

**Topik Tugas Akhir:** Optimasi Rute Evakuasi Dinamis pada Lingkungan Gedung Kampus Menggunakan ST-HGAT dan PPO.

**Tanggal:** 10 November 2026

## Cakupan
Tahap ini menelaah lima publikasi yang sebelumnya masuk inventarisasi belum dibaca, dengan prioritas referensi BAB I dan studi yang relevan untuk pembanding metode:
1. Umahuk et al. (2025) — Dijkstra untuk jalur evakuasi gedung kampus.
2. Alrahma et al. (2024) — Q-learning untuk jalur evakuasi gedung kampus.
3. Halisah et al. (2025) — ACO dibandingkan BFS dan DFS untuk rute evakuasi.
4. Zhang et al. (2023) — GNN untuk rekomendasi rute evakuasi wisata.
5. Gebreyesus et al. (2025) — ST-GNN dan PPO untuk job shop scheduling.

Sumber dibaca dari PDF penerbit atau teks lengkap artikel open-access yang tersedia di laman penerbit. Catatan di bawah membedakan hasil yang dinyatakan penulis dengan implikasi untuk topik Tugas Akhir.

## A. Umahuk, Buyang, dan Oppier (2025)

**Judul:** “Analisis Jalur Evakuasi pada Gedung Fakultas Teknik Universitas Pattimura dengan Metode Algoritma Dijkstra.”
**Publikasi:** Jurnal Sipil KOKOH, Vol. 23, No. 1, 2025, hlm. 1–16.
**DOI:** https://doi.org/10.17509/k.v23i1.77056
**Status:** Isi utama artikel (pendahuluan, metode, data objek, hasil pengukuran, dan kesimpulan) ditelaah dari PDF penerbit.

### Tujuan dan objek
Penelitian menyusun jalur evakuasi pada Gedung Fakultas Teknik Universitas Pattimura. Gedung yang diteliti memiliki tiga lantai, luas 2.419,42 m², dan 70 ruangan yang digunakan. Penulis menyoroti belum tersedianya jalur evakuasi dan titik kumpul yang jelas.

### Metode dan data
- Lokasi penelitian berada di Fakultas Teknik Universitas Pattimura, Ambon.
- Pengumpulan data meliputi dimensi ruangan, pengukuran jarak, layout gedung, serta standar dan literatur terkait.
- Pengukuran dilakukan dari ruangan menuju tangga dan dari tangga menuju titik kumpul.
- Algoritma Dijkstra digunakan untuk menentukan lintasan terpendek berdasarkan jarak yang diukur.
- Artikel juga menyusun site plan jalur evakuasi, titik kumpul sementara, dan titik kumpul akhir.

### Hasil yang dilaporkan
- Abstrak menyebut jarak terpendek dari lantai 1, 2, dan 3 menuju titik kumpul masing-masing 12,5 m; 35,4 m; dan 46,5 m.
- Bagian hasil menyebut rata-rata waktu evakuasi dari ruangan menuju titik kumpul sebesar 10 detik untuk lantai 1, 53 detik untuk lantai 2, dan 86 detik untuk lantai 3.
- Kesimpulan menyebut rentang jarak terpendek dari ruangan tiap lantai menuju area titik kumpul sebesar 12,8–46,5 m, sedangkan jarak dari titik kumpul sementara ke titik kumpul akhir sebesar 170–220 m.

### Catatan kritis
- Ada ketidaksesuaian angka antara abstrak (12,5 m untuk lantai 1) dan kesimpulan (rentang 12,8–46,5 m). Jangan memilih salah satunya tanpa verifikasi tabel/denah rinci.
- Artikel berfokus pada perhitungan jarak dan perancangan jalur statis. Tidak terlihat pengujian perubahan okupansi, kepadatan dinamis, penutupan akses saat simulasi berlangsung, atau pembelajaran policy.
- Angka waktu 10/53/86 detik disebut sebagai rata-rata waktu evakuasi, tetapi dasar asumsi kecepatan/perhitungan waktu perlu ditelusuri lebih lanjut sebelum dijadikan pembanding kuantitatif.
- Dijkstra menjadi baseline shortest-path yang relevan, tetapi tidak menyelesaikan keputusan adaptif terhadap perubahan kondisi secara otomatis.

### Relevansi
Sumber ini relevan sebagai studi evakuasi gedung kampus Indonesia dan contoh penentuan lintasan berbobot jarak dari ruangan melalui tangga menuju titik kumpul. Dapat menjadi pembanding baseline statis, bukan bukti optimasi dinamis.

## B. Alrahma et al. (2024)

**Judul:** “Application of Q-learning Method for Disaster Evacuation Route Design Case Study: Digital Center Building UNNES.”
**Publikasi:** Jurnal Ilmu Komputer dan Informasi, Vol. 17, No. 2, Juni 2024, hlm. 145–158.
**DOI:** https://doi.org/10.21609/jiki.v17i2.1236
**Status:** Isi utama artikel (pendahuluan, formulasi Q-learning, lingkungan, pengujian, hasil, dan kesimpulan) ditelaah dari PDF lengkap yang tersedia.

### Tujuan dan objek
Penelitian menerapkan Q-learning untuk menentukan jalur terpendek dari 11 ruangan di lantai pertama Digital Center (DC) UNNES menuju pintu keluar. Gedung DC secara keseluruhan disebut memiliki empat lantai dan 44 ruangan, tetapi eksperimen penelitian dibatasi pada 11 ruangan di lantai pertama.

### Metode
- Denah lantai pertama direpresentasikan sebagai lingkungan berbasis grid.
- Agen mempelajari jalur menuju lokasi target melalui interaksi dengan lingkungan dan pembaruan Q-value.
- Lingkungan membedakan lokasi tujuan, hambatan, dan sel biasa.
- Reward yang diuji mencakup pemberian reward positif ketika mencapai target, penalti ketika memasuki hambatan, serta reward/penalti untuk posisi lain.
- Parameter eksplorasi epsilon dan konfigurasi reward diuji.
- Pengujian dilakukan pada lingkungan tanpa hambatan tambahan (11 ruangan) dan lingkungan dengan hambatan tambahan (5 ruangan).
- Artikel juga membandingkan Q-learning dengan SARSA.

### Hasil yang dilaporkan
- Pada lingkungan tanpa hambatan tambahan, jalur Q-learning memiliki panjang yang sama dengan jalur acuan yang dibuat secara manual; penulis menyebut kesesuaian 100%.
- Waktu komputasi rata-rata yang dilaporkan untuk lingkungan tanpa hambatan tambahan adalah 0,54 detik.
- Pada lingkungan dengan hambatan tambahan, agen masih dapat menemukan jalur terpendek; waktu komputasi rata-rata yang dilaporkan adalah 0,76 detik.
- Kesimpulan menyebut pengujian hingga maksimum 3.000 episode. Tabel per ruangan menunjukkan jumlah episode yang berbeda-beda.
- Hasil menunjukkan jarak awal yang lebih jauh dari tujuan dapat memerlukan episode dan waktu komputasi lebih besar.

### Catatan kritis
- Abstrak menyatakan rata-rata episode konvergensi kurang dari 1.000, sedangkan kesimpulan menyebut episode di bawah 3.000. Tabel eksperimen memperlihatkan variasi jumlah episode antar-ruangan; sebaiknya kutip angka per tabel/skenario, bukan menyederhanakan menjadi satu angka universal.
- Model menggunakan representasi grid dan rute terpendek; belum memodelkan interaksi banyak penghuni, antrean, atau kepadatan pedestrian.
- Uji hambatan tambahan merupakan perubahan lingkungan pada eksperimen, bukan sistem sensor real-time atau bukti bahwa model memantau perubahan gedung aktual.
- Hasil 100% merujuk kesamaan jalur yang ditemukan dengan jalur acuan pada konfigurasi uji, bukan akurasi umum untuk seluruh gedung atau kondisi evakuasi.

### Relevansi
Ini merupakan pembanding penting karena sama-sama membahas gedung kampus dan RL untuk jalur evakuasi. Namun, pendekatannya Q-learning berbasis grid untuk shortest path, sedangkan penelitian Tugas Akhir berfokus pada representasi graf heterogen spatio-temporal dan policy PPO. Artikel ini dapat dipakai untuk menjelaskan perbedaan antara rute yang dipelajari pada lingkungan sederhana dan keputusan adaptif dengan informasi kondisi dinamis.

## C. Halisah et al. (2025)

**Judul:** “Metode Optimasi Cerdas untuk Pencarian Jalur Evakuasi Bencana di Kabupaten Mamuju Menggunakan Ant Colony Optimization.”
**Publikasi:** Journal of Computer and Information System (J-CIS), Vol. 8, No. 2, Oktober 2025, hlm. 119–131.
**DOI yang benar:** https://doi.org/10.31605/jcis.v8i2.5120
**Status:** Isi utama artikel (pendahuluan, data, representasi jaringan, algoritma pembanding, hasil, dan kesimpulan) ditelaah dari PDF penerbit.

### Tujuan dan metode
Penelitian membandingkan BFS, DFS, dan ACO untuk pencarian jalur evakuasi di Kabupaten Mamuju.
- Data jaringan jalan diperoleh menggunakan Google Maps.
- Titik awal, persimpangan (vertex), dan tujuan evakuasi diidentifikasi untuk membentuk dataset jaringan.
- Terdapat 20 dataset.
- Dua skenario yang dijelaskan adalah Single Vertex Single Goal (SVSG), yaitu satu titik awal dan satu tujuan, serta Single Vertex Multi Goals (SVMG), yaitu satu titik awal dan beberapa tujuan.
- Matriks adjacency digunakan untuk merepresentasikan konektivitas dan bobot jarak. Nilai 0 menunjukkan tidak ada koneksi langsung, sedangkan -1 menunjukkan jalur terputus/tidak dapat dilalui.
- ACO menggunakan semut virtual dan jejak feromon untuk mengeksplorasi jalur; hasil dibandingkan dengan jalur optimal yang dihitung/dibuat secara manual.

### Hasil
- ACO menghasilkan jalur yang sama dengan jalur optimal pada pengujian yang dilaporkan.
- RMSE ACO = 0,00; DFS = 4,72; BFS = 6,91.
- Pada grafik rata-rata, ACO menghasilkan jarak sekitar 24,0 km pada SVSG dan 27,0 km pada SVMG, sama dengan jarak optimal yang ditampilkan.
- DFS dan BFS menghasilkan jarak rata-rata lebih tinggi daripada ACO pada kedua skenario.

### Catatan kritis
- Abstrak dan kesimpulan menyatakan dua skenario, meskipun satu bagian abstrak pada metadata lama menyebut tiga skenario. Gunakan dua skenario yang dijelaskan pada metode dan hasil PDF.
- Klaim bahwa BFS/DFS kurang adaptif terhadap perubahan kondisi jalan merupakan latar belakang penulis; eksperimen yang dilaporkan terutama membandingkan jarak pada 20 dataset. Tidak ada bukti yang cukup untuk menyatakan ACO telah diuji pada perubahan kondisi jalan secara real-time.
- Artikel menyebut parameter jarak, waktu, atau risiko secara umum dalam penjelasan pengujian, tetapi hasil utama yang ditampilkan adalah jarak dan RMSE jarak.
- ACO bukan metode pembelajaran representasi graf spatio-temporal atau policy RL.

### Relevansi
Sumber ini dapat menjadi pembanding algoritma optimasi jalur berbasis graf/jaringan dan contoh evaluasi terhadap rute acuan. Hasilnya tidak membuktikan ACO selalu lebih baik pada masalah evakuasi gedung dinamis; objek, skala jaringan, dan metriknya berbeda.

## D. Zhang et al. (2023)

**Judul:** “Visual Analytics of Route Recommendation for Tourist Evacuation Based on Graph Neural Network.”
**Publikasi:** Scientific Reports, Vol. 13, Article 17240, 2023.
**DOI:** https://doi.org/10.1038/s41598-023-42862-z
**Status:** Isi utama artikel open-access (pendahuluan, model GNN, perhitungan rekomendasi rute, eksperimen, dan kesimpulan) ditelaah dari PDF penerbit.

### Tujuan dan objek
Penelitian mengusulkan PER-GCN untuk rekomendasi rute evakuasi wisatawan dengan mempertimbangkan kemiripan gaya wisata, kompleksitas rute, dan kapasitas tampung objek wisata. Studi kasus adalah kawasan West Lake, Hangzhou, Tiongkok.

### Data dan metode
- Data dari administrasi West Lake; setelah pembersihan diperoleh 5.000 data wisatawan/kunjungan yang tersedia untuk analisis.
- Sistem memuat 36 objek wisata.
- Interaksi wisatawan dan objek wisata direpresentasikan sebagai graf bipartit/relasi wisatawan–objek wisata.
- GNN melakukan propagasi informasi antarnode dan agregasi embedding beberapa orde untuk memprediksi kecocokan wisatawan dengan objek wisata.
- Model rekomendasi menggunakan Bayesian Personalized Ranking (BPR) loss.
- Rute kemudian dipertimbangkan dengan kompleksitas/jarak, kapasitas tampung aktual objek wisata, kemauan wisatawan untuk bekerja sama, dan jumlah batch evakuasi.
- Sistem visualisasi menampilkan kapasitas objek wisata, hasil rekomendasi, aliran wisatawan, dan profil wisatawan.

### Hasil
- PER-GCN dibandingkan dengan GCN dan user-based collaborative filtering (uCF), dengan 30 kali eksperimen dan cross-validation 10 iterasi.
- Rata-rata precision: PER-GCN 71,673; GCN 65,579; uCF 59,935.
- Rata-rata recall: PER-GCN 58,47; GCN 50,42; uCF 48,671.
- Uji Wilcoxon yang dilaporkan menunjukkan perbedaan signifikan pada precision dan recall untuk perbandingan yang dilakukan.
- Analisis parameter sistem menyatakan efisiensi evakuasi lebih tinggi ketika willingness to cooperate berada pada rentang 60–75% dan batch 10 atau lebih.

### Catatan kritis
- Graf yang dipelajari adalah hubungan wisatawan–objek wisata untuk rekomendasi, bukan graf topologi ruang, koridor, tangga, dan pintu gedung.
- Fokus GNN terutama pada rekomendasi objek tujuan dan preferensi, bukan PPO atau policy yang memilih tindakan tiap langkah berdasarkan keadaan graf gedung.
- Hasil precision/recall mengukur kualitas rekomendasi, bukan waktu evakuasi atau keselamatan penghuni gedung.
- Konteks wisata terbuka berbeda dari evakuasi indoor kampus; angka hasil tidak dapat dipindahkan sebagai target kinerja penelitian ini.

### Relevansi
Sumber ini relevan untuk menunjukkan penggunaan GNN pada rekomendasi rute evakuasi dan pemanfaatan informasi kapasitas serta distribusi orang. Namun, perbedaan struktur graf dan tujuan prediksi harus dinyatakan secara eksplisit jika dipakai dalam tinjauan penelitian terdahulu.

## E. Gebreyesus et al. (2025)

**Judul:** “Deep Reinforcement Learning-Based Spatio-Temporal Graph Neural Network for Solving Job Shop Scheduling Problem.”
**Publikasi:** Evolutionary Intelligence, Vol. 18, Article 6, 2025. Artikel tersedia open-access; pertama kali tersedia online 16 November 2024.
**DOI:** https://doi.org/10.1007/s12065-024-00989-6
**Status:** Isi utama artikel open-access (pendahuluan, formulasi masalah, arsitektur, PPO, eksperimen, ablation, dan kesimpulan) ditelaah dari laman penerbit.

### Tujuan dan arsitektur
Penelitian mengembangkan DRL-STGNN untuk menyelesaikan Job Shop Scheduling Problem (JSSP), yaitu penjadwalan operasi pada mesin dengan kendala urutan dan sumber daya.
- JSSP direpresentasikan sebagai disjunctive graph yang atribut node-nya berubah pada setiap langkah keputusan.
- Spatial block menggunakan Attentive-GIN untuk mengagregasi informasi tetangga dan menangkap dependensi struktural.
- Temporal block memodelkan evolusi fitur node sepanjang langkah keputusan.
- Fusion block berbasis mekanisme gating menggabungkan representasi spasial dan temporal.
- Representasi graf global diperoleh melalui graph pooling.
- PPO digunakan untuk melatih policy pengambilan keputusan penjadwalan.
- Objective PPO mencakup clipped surrogate objective, value-function loss, dan entropy regularization.

### Eksperimen dan hasil
- Pengujian menggunakan instance JSSP yang dibangkitkan serta benchmark publik.
- Ukuran instance pelatihan mencakup 6×6, 10×10, 15×15, dan 20×20; evaluasi juga menggunakan ukuran yang lebih besar dan benchmark Taillard serta DMU.
- Pembanding mencakup heuristic dispatching rules (SPT, MWKR, MOPNR, FDD/MWKR), model DRL/GNN lain, serta Google OR-Tools.
- Hasil menunjukkan performa relatif bergantung pada ukuran instance. Pada beberapa instance kecil/menengah, GA atau MBO dapat mengungguli DRL-STGNN; pada instance benchmark yang lebih besar, DRL-STGNN menunjukkan keunggulan pada sebagian kelompok.
- Ablation study menunjukkan penghilangan temporal encoding, attention pada ekstraksi atribut spasial, atau gated fusion menurunkan sample efficiency dan performa.

### Catatan kritis
- JSSP adalah masalah penjadwalan manufaktur, bukan simulasi evakuasi manusia. Node, edge, state, action, dan reward didesain untuk operasi dan mesin.
- Artikel ini bukan arsitektur ST-HGAT yang sama dengan rancangan penelitian Tugas Akhir. Spatial block-nya menggunakan Attentive-GIN, bukan HGAT.
- Artikel mendukung kelayakan konseptual menggabungkan representasi graf spasial-temporal dengan PPO pada masalah keputusan dinamis, tetapi tidak membuktikan metode tersebut efektif untuk evakuasi gedung.
- Hasil benchmark JSSP tidak dapat dipakai sebagai klaim performa evakuasi.

### Relevansi
Ini adalah referensi pendukung yang kuat untuk argumen bahwa representasi graf yang berubah dari langkah ke langkah dapat digabungkan dengan temporal encoding, attention, fusion, dan PPO. Penggunaan dalam latar belakang harus disertai batasan domain: penjadwalan mesin berbeda dari navigasi penghuni gedung.

## F. Sintesis lintas lima publikasi

1. **Baseline shortest path:** Umahuk et al. menggunakan Dijkstra pada gedung kampus; Alrahma et al. menggunakan Q-learning dan membandingkan dengan jalur manual; keduanya relevan untuk baseline rute statis/terbatas.
2. **Optimasi jalur non-RL:** Halisah et al. membandingkan ACO, BFS, dan DFS pada jaringan jalan. Hasil ACO cocok dengan rute optimal pada dataset mereka, tetapi tidak menguji adaptasi real-time.
3. **GNN untuk rute evakuasi:** Zhang et al. memakai GNN untuk rekomendasi tujuan wisata berdasarkan graf interaksi wisatawan–objek wisata. Ini relevan sebagai bukti penerapan GNN dalam konteks evakuasi, tetapi bukan graf topologi gedung.
4. **ST-GNN + PPO:** Gebreyesus et al. menggabungkan Attentive-GIN, temporal block, gated fusion, dan PPO pada JSSP. Ini mendukung kemungkinan integrasi representasi spasio-temporal graf dan PPO, bukan bukti langsung untuk domain evakuasi.
5. **Research gap yang dapat dipertajam:** referensi yang dibaca memperlihatkan contoh Dijkstra/Q-learning/ACO untuk pencarian rute, GNN untuk rekomendasi rute wisata, serta ST-GNN+PPO untuk penjadwalan. Masih perlu ditunjukkan secara hati-hati bagaimana penelitian Tugas Akhir menggabungkan graf heterogen gedung, perubahan kondisi ruang/penghuni dari waktu ke waktu, dan keputusan rute PPO dalam satu simulasi evakuasi kampus.

## G. Perbaikan metadata dan status

- Perbaiki DOI Halisah2025 pada `library.bib` menjadi `10.31605/jcis.v8i2.5120`; halaman penerbit menyebut volume 8 nomor 2, Oktober 2025, hlm. 119–131.
- Periksa kembali angka jarak Umahuk et al. karena abstrak dan kesimpulan berbeda.
- Pastikan judul Umahuk mengikuti halaman PDF penerbit; ada salah ketik “APDA” pada judul yang tercetak di PDF, sedangkan metadata OJS menampilkan “PADA”.
- Tahun online Gebreyesus tercatat 16 November 2024, sedangkan volume/issue bibliografis adalah Evolutionary Intelligence Vol. 18 (2025), Article 6. Untuk daftar pustaka gunakan format versi jurnal final sesuai pedoman prodi.

## H. Status pembacaan setelah tahap 7

Berdasarkan inventarisasi 30 PDF:
- Dibaca penuh/isi utama: 24 publikasi.
- Dibaca sebagian: 1 publikasi (Wang et al. 2024).
- Belum dibaca: 5 publikasi.

Lima publikasi pada tahap ini telah ditelaah pada bagian isi utama. Pembacaan ini tidak berarti semua lampiran/suplemen atau setiap baris referensi yang dikutip dalam artikel telah diverifikasi.

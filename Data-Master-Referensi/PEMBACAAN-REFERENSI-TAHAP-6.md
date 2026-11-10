# Catatan Pembacaan Referensi — Tahap 6

**Topik Tugas Akhir:** Optimasi Rute Evakuasi Dinamis pada Lingkungan Gedung Kampus Menggunakan ST-HGAT dan PPO.

**Tanggal:** 10 November 2026

## Cakupan
Tahap ini menuntaskan dua publikasi yang sebelumnya berstatus dibaca sebagian, yaitu Rizian et al. dan Gao et al. Sumber yang digunakan adalah PDF penerbit yang dapat diakses secara publik. Wang et al. masih belum dapat dituntaskan karena PDF IEEE tidak tersedia secara terbuka; halaman abstrak dan metadata saja yang dapat diperiksa.

## A. R-19 — Rizian et al. (2025/2026)

**Judul:** “Enhancing Classification of Self-Reported Monkeypox Symptoms on Social Media Using Term Frequency-Inverse Document Frequency Features and Graph Attention Networks.”

**Publikasi:** Jurnal Teknik Informatika (JUTIF), Vol. 6, No. 6, hlm. 5865–5881. DOI: https://doi.org/10.52436/1.jutif.2025.6.6.5482

**Status:** Dibaca penuh dari PDF penerbit (17 halaman).

### Tujuan
Penelitian mengembangkan klasifikasi gejala Monkeypox yang dilaporkan pengguna media sosial berbahasa Indonesia. Penulis menggabungkan representasi TF-IDF dengan GAT untuk memanfaatkan fitur teks dan relasi kemiripan antartulisan.

### Data dan metode
- Data sekitar 3.200 tweet dikumpulkan menggunakan Tweet-Harvest dengan kata kunci terkait Monkeypox/Mpox dan filter bahasa Indonesia.
- Tweet diberi label manual positif/negatif dengan proporsi sekitar 51% dan 49%.
- Teks dibersihkan melalui tahapan preprocessing, kemudian dibagi menjadi data latih, validasi, dan uji dengan rasio 80:10:10.
- TF-IDF menghasilkan vektor fitur untuk setiap tweet.
- Setiap tweet direpresentasikan sebagai node. Hubungan antar-node dibentuk menggunakan cosine similarity dan k-nearest neighbors (k-NN), sehingga terbentuk graf tak berarah.
- GAT menghitung bobot perhatian terhadap tetangga, lalu mengagregasikan representasi tetangga untuk klasifikasi.
- Parameter yang diuji mencakup n-gram, min_df, jumlah tetangga K, jumlah attention head, hidden units, dropout, learning rate, weight decay, dan epoch.

### Hasil
- Konfigurasi terbaik yang dilaporkan menggunakan n-gram (1,2), min_df=1, K=9, hidden units 32, 2 attention heads, dropout 0,3, learning rate 0,008, weight decay 0,0005, dan maksimum 400 epoch.
- Konfigurasi tersebut menghasilkan accuracy 93,07%, precision 93,26%, recall 93,07%, dan macro-F1 93,06%.
- Pada K=7, macro-F1 tertinggi yang dilaporkan adalah 85,48%; pada K=9 mencapai 93,06%; pada K=11 turun menjadi 90,96%. Penulis mengaitkan penurunan saat graf semakin padat dengan kemungkinan over-smoothing.
- CNN + TF-IDF dilaporkan memiliki macro-F1 92,16%, SVM + TF-IDF 85,73%, dan Logistic Regression + TF-IDF 84,89%.
- Kurva loss turun dari sekitar 0,7029 menjadi 0,2324 pada epoch ke-140.

### Keterbatasan dan catatan kritis
- Domain penelitian adalah klasifikasi teks, bukan pemodelan pergerakan manusia atau pengambilan keputusan rute.
- Graf dibangun berdasarkan kemiripan dokumen; ini berbeda secara mendasar dari graf gedung yang dibentuk berdasarkan konektivitas fisik ruang.
- Hasil akurasi/macro-F1 tidak dapat digunakan sebagai bukti efektivitas GAT untuk evakuasi.
- Ada ketidaktepatan redaksi di bagian diskusi: setelah menyebut accuracy 93,07%, kalimat berikutnya menyebut “accuracy” 93,26%, padahal tabel mengidentifikasi 93,26% sebagai precision. Gunakan tabel hasil untuk menyebut metrik.
- Metadata tanggal berbeda: PDF mencantumkan terbit 31 Desember 2025 dan issue Vol. 6 No. 6 (December 2025), sedangkan halaman OJS mencantumkan Published 5 Januari 2026 dan sitasi Januari 2026. Untuk daftar pustaka, verifikasi gaya metadata institusi; volume/issue dan halaman pada PDF adalah Vol. 6 No. 6, 2025, hlm. 5865–5881.

### Relevansi untuk penelitian
Sumber ini mendukung penjelasan teknis bahwa GAT dapat mempelajari bobot perhatian antar-tetangga pada graf dan bahwa konstruksi graf serta kepadatan koneksi memengaruhi hasil model. Namun, sumber ini hanya contoh aplikasi GAT pada klasifikasi, bukan dasar untuk menentukan fitur, relasi, atau arsitektur ST-HGAT pada graf evakuasi.

**Halaman penting:** tujuan dan gap (5865–5867); data dan preprocessing (5867–5870); TF-IDF, konstruksi graf, GAT (5870–5872); hasil konfigurasi dan performa (5873–5877); kesimpulan (5878).

## B. R-26 — Gao et al. (2022)

**Judul:** “Multi-Agent Decision-Making Modes in Uncertain Interactive Traffic Scenarios via Graph Convolution-Based Deep Reinforcement Learning.”

**Publikasi:** Sensors, Vol. 22, No. 12, Article 4586, 2022. DOI: https://doi.org/10.3390/s22124586

**Status:** Dibaca penuh dari PDF versi terbitan (18 halaman). Salinan versi terbitan juga tersedia melalui repositori TU Delft.

### Temuan utama
- Graf tak berarah digunakan untuk merepresentasikan kendaraan sebagai node dan interaksi/informasi antar-kendaraan sebagai edge.
- Fitur node meliputi kecepatan, posisi longitudinal, lajur, dan intensi kendaraan.
- GCN memproses representasi graf, sedangkan keputusan dipelajari menggunakan Graph Convolutional Q-Network (GQN) dan Multi-Step Double Graph Convolutional Q-Network (MDGQN).
- Penelitian menggunakan deep Q-learning, bukan PPO.
- Simulasi menggunakan SUMO pada jalan raya tiga lajur dengan dua exit dan interaksi kendaraan otonom serta kendaraan manusia.
- Reward terdiri atas empat aspek: hasil tugas, efisiensi lalu lintas, kenyamanan, dan keselamatan.
- Metrik evaluasi meliputi kecepatan rata-rata, collision rate, jumlah pengereman darurat, dan tingkat penyelesaian tugas.

### Hasil
- MDGQN secara umum mengungguli GQN pada skenario yang diuji: collision rate lebih rendah dan tingkat keberhasilan mencapai tujuan lebih tinggi pada sebagian besar mode.
- AGGI memiliki efisiensi dan tingkat kedatangan tertinggi, tetapi juga collision rate dan pengereman darurat tertinggi.
- CONP memiliki collision rate dan pengereman darurat terendah, tetapi efisiensi dan tingkat kedatangan terendah.
- Setelah episode ke-200, rata-rata reward ternormalisasi untuk baseline 0,7399, CONP-GQN 0,9882, dan CONP-MDGQN 0,9886.
- Penulis menyimpulkan adanya trade-off antara peningkatan insentif/efisiensi dan penurunan keselamatan.

### Keterbatasan dan relevansi
- Lingkungan yang diuji adalah lalu lintas kendaraan di jalan raya, bukan gedung dan penghuni yang berjalan kaki.
- Model graf dan action space dirancang khusus untuk kendaraan, termasuk perpindahan lajur dan akselerasi.
- Sumber ini tidak membuktikan bahwa GCN-Q-learning lebih tepat daripada ST-HGAT-PPO untuk evakuasi.
- Relevansinya adalah sebagai contoh desain reward multi-tujuan dan evaluasi trade-off keselamatan, efisiensi, kenyamanan, dan keberhasilan tugas pada sistem dinamis berbasis graf.

**Halaman penting:** representasi graf/state (hlm. 6); GCN, GQN, MDGQN (hlm. 6–8); reward (hlm. 8–10); metrik dan hasil (hlm. 11–16).

## C. R-21 — Wang et al. (2024)

**Judul:** “Deep Reinforcement Learning: A Survey.”

**Publikasi:** IEEE Transactions on Neural Networks and Learning Systems, Vol. 35, No. 4, hlm. 5064–5078. DOI: https://doi.org/10.1109/TNNLS.2022.3207346

**Status:** Masih dibaca sebagian. Halaman PubMed dan IEEE serta abstrak/metadata diperiksa; PDF penuh tidak dapat diakses dari sumber publik yang tersedia pada pemeriksaan ini.

### Informasi yang didukung abstrak
- DRL menggabungkan kemampuan representasi fitur deep learning dengan kemampuan pengambilan keputusan reinforcement learning.
- Survey mencakup algoritma value-based, policy-based, dan maximum-entropy DRL.
- Abstrak menyoroti tantangan keterbatasan sampel, sparse reward, dan multi-agent.
- Subbidang yang disebut meliputi hierarchical RL, multi-agent RL, dan imitation learning.

**Batas penggunaan:** jangan mengutip uraian rinci taksonomi, algoritma, tabel perbandingan, atau kesimpulan bagian tertentu sebelum PDF lengkap diperiksa. Status tetap dibaca sebagian.

## D. Sintesis tahap ini
1. Rizian et al. memberi contoh penggunaan attention untuk memberi bobot berbeda pada hubungan antarnode, tetapi graf kemiripan dokumen tidak sama dengan graf konektivitas gedung.
2. Gao et al. memberi contoh bahwa representasi graf dapat digabungkan dengan RL dan reward multi-tujuan; hasilnya menunjukkan trade-off keselamatan dan efisiensi.
3. Kedua paper tersebut tidak menjadi bukti langsung bahwa ST-HGAT dan PPO efektif untuk evakuasi gedung.
4. Wang et al. tetap membutuhkan PDF lengkap agar dapat dipakai sebagai sumber rinci untuk subbab 2.6.

## E. Status pembacaan
- Rizian et al.: dibaca penuh.
- Gao et al.: dibaca penuh.
- Wang et al.: dibaca sebagian; PDF penuh belum tersedia.

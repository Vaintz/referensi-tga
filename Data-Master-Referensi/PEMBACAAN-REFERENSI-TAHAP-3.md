# Catatan Pembacaan Referensi — Tahap 3

**Topik Tugas Akhir:** Optimasi Rute Evakuasi Dinamis pada Lingkungan Gedung Kampus Menggunakan ST-HGAT dan PPO.

**Tanggal pemeriksaan:** 10 November 2026

## Cakupan dan status pembacaan

Tahap ini berfokus pada tiga publikasi dalam folder `2.5-ST-HGAT/`:
1. Zheng, Yi, dan Wei (2025), *A Survey of Dynamic Graph Neural Networks*.
2. Corradini et al. (2026), *A Systematic Literature Review of Spatio-Temporal Graph Neural Network Models for Time Series Forecasting and Classification*.
3. Yang dan Peng (2024), *Spatio-Temporal Contrastive Heterogeneous Graph Attention Networks for Session-Based Recommendation*.

Naskah lengkap Zheng (PDF open access 18 halaman) dan Yang & Peng (PDF open access 16 halaman) ditelaah pada bagian definisi, metode, hasil, dan kesimpulan. Untuk Corradini et al., naskah lengkap preprint arXiv versi 4 (119 halaman, 3 November 2025) ditelaah pada bagian definisi, taksonomi, konstruksi graf, domain aplikasi, diskusi, dan keterbatasan; metadata dan abstrak dicocokkan dengan versi jurnal *Neural Networks* Vol. 195 (Maret 2026), Article 108269. Perlu dicatat bahwa versi preprint dan versi terbitan dapat memiliki perubahan editorial.

## A. Publikasi yang ditelaah

### R-17 — Zheng, Yi, dan Wei (2025)

**Judul:** A Survey of Dynamic Graph Neural Networks  
**Publikasi:** *Frontiers of Computer Science*, Vol. 19, Issue 6, Article 196323 (2025). Diterbitkan online 12 Desember 2024.  
**DOI:** https://doi.org/10.1007/s11704-024-3853-2  
**Lokasi repository:** `2.5-ST-HGAT/`  
**Status:** Dibaca dari PDF lengkap (18 halaman).

**Tujuan dan ruang lingkup**
Artikel ini merupakan survei tentang Dynamic Graph Neural Networks (Dynamic GNN), yang menggabungkan GNN dengan pemodelan urutan/waktu untuk menangkap perubahan struktur maupun atribut graf. Penulis membahas konsep dasar, teknik representasi, model utama, dataset, benchmark, serta tantangan penelitian.

**Definisi dan pembedaan graf dinamis**
- Dynamic graph menggambarkan graf yang mengalami evolusi temporal; simpul, sisi, dan/atau atributnya dapat berubah.
- Penulis membedakan Discrete-Time Dynamic Graph (DTDG), yang merepresentasikan perubahan melalui snapshot graf pada interval tertentu, dan Continuous-Time Dynamic Graph (CTDG), yang merepresentasikan perubahan melalui event dengan timestamp.
- Pada DTDG, setiap snapshot dapat diproses sebagai graf pada satu titik waktu, lalu urutan representasinya dipelajari oleh modul temporal.
- Pada CTDG, event dan timestamp dipertahankan sehingga urutan serta jarak waktu antarinteraksi dapat dipertimbangkan.
- Penulis secara eksplisit menyebut bahwa graf dengan struktur tetap tetapi atribut simpul berubah dari waktu ke waktu disebut spatio-temporal graphs dan berada di luar cakupan survei ini. Ini merupakan batasan ruang lingkup yang penting saat mengutip artikel untuk penelitian evakuasi.

**Taksonomi pendekatan**
- Untuk DTDG, penulis mengelompokkan pendekatan utama menjadi arsitektur stacked dan integrated.
- Arsitektur stacked memproses setiap snapshot dengan GNN untuk memperoleh fitur spasial, lalu mengirimkan urutan representasi tersebut ke modul temporal seperti RNN.
- Arsitektur integrated menggabungkan komponen GNN dan RNN dalam satu kerangka pemrosesan.
- DySAT merupakan contoh penggunaan attention pada dua dimensi: GAT untuk dimensi spasial dan Transformer untuk dimensi temporal.
- ROLAND menggabungkan beberapa layer GNN dengan model urutan dan mempertahankan state node secara hierarkis dari waktu sebelumnya.
- EvolveGCN menggunakan RNN untuk memperbarui parameter GCN antar-snapshot, bukan sekadar memperbarui embedding node.

**Temuan dan pembahasan**
Artikel ini merupakan survei, bukan eksperimen tunggal yang menguji satu model pada satu dataset. Penulis membandingkan keluarga metode berdasarkan jenis graf, cara memasukkan informasi temporal, dan event graf yang dapat ditangani. Model-model yang dibahas mencakup metode snapshot-based maupun event-based.

**Tantangan yang dibahas**
- Skalabilitas dan kebutuhan komputasi.
- Keterbatasan dataset graf dinamis yang beragam.
- Penanganan informasi heterogen.
- Kebutuhan metode adaptif dan memory-enhanced.
- Generalisasi/inductive learning serta analisis teoretis.

**Relevansi untuk penelitian ini**
- Berguna untuk membedakan graf statis, graf dinamis diskret, dan graf dinamis kontinu.
- Mendukung pembahasan bahwa pemodelan temporal dapat dilakukan melalui snapshot dan modul temporal, atau melalui event bertimestamp.
- Contoh DySAT menunjukkan bahwa attention dapat digunakan untuk mengolah informasi spasial dan temporal secara terpisah.
- Namun, karena survei ini mengecualikan graf spatio-temporal dengan topologi tetap dan atribut node yang berubah, sumber ini tidak boleh dijadikan satu-satunya landasan bagi skenario graf gedung yang topologinya relatif tetap tetapi kondisi kepadatan/penghuninya berubah.
- Tidak membahas evakuasi gedung atau membuktikan efektivitas ST-HGAT untuk navigasi evakuasi.

**Catatan kritis**
Jangan menyamakan Dynamic GNN dan Spatio-Temporal GNN. Dalam artikel ini, istilah dynamic graph terutama terkait perubahan node/edge/atribut graf, sedangkan graf spatio-temporal dengan topologi tetap dan fitur yang berubah secara eksplisit dikecualikan dari ruang lingkup surveinya.

### R-18 — Corradini et al. (2026)

**Judul:** A Systematic Literature Review of Spatio-Temporal Graph Neural Network Models for Time Series Forecasting and Classification  
**Publikasi:** *Neural Networks*, Vol. 195, Article 108269 (Maret 2026).  
**DOI:** https://doi.org/10.1016/j.neunet.2025.108269  
**Lokasi repository:** `2.5-ST-HGAT/`  
**Status:** Naskah lengkap preprint arXiv versi 4 ditelaah pada bagian-bagian relevan; metadata dan abstrak dicocokkan dengan versi jurnal 2026.

**Tujuan dan metodologi review**
- Review membahas ST-GNN untuk klasifikasi time series dan forecasting.
- Penulis mencari publikasi melalui Scopus, IEEE Xplore, Web of Science, dan ACM.
- Proses seleksi menghasilkan 366 publikasi: 262 artikel jurnal dan 104 makalah konferensi.
- Kriteria seleksi yang dijelaskan pada preprint meliputi jurnal Q1/Q2 dan konferensi kategori A*/A, serta mengecualikan publikasi tahun 2025 pada saat review disusun, book chapter, workshop, dan tutorial.
- Review menyajikan model, dataset, benchmark, hasil, dan repository pendukung; penulis tidak melakukan eksperimen numerik baru pada dataset.

**Definisi ST-GNN**
- ST-GNN dirancang untuk menangkap ketergantungan antarvariabel dan ketergantungan antarwaktu sekaligus.
- Dalam contoh multivariate time series, node biasanya mewakili variabel pada suatu waktu, sedangkan edge mewakili hubungan antarvariabel.
- Fitur pada node/edge dapat berubah dari waktu ke waktu.
- ST-GNN dapat menggunakan modul spasial dan temporal secara terpisah, atau mengintegrasikan pemrosesan kedua dimensi tersebut.

**Taksonomi komponen spasial**
Review mengelompokkan mekanisme propagasi informasi spasial menjadi:
1. Recurrent GNN.
2. Convolutional GNN.
3. Attentional GNN.
4. Hybrid dan kategori lain.

Kelompok tersebut tidak saling eksklusif. Model dapat menggabungkan lebih dari satu mekanisme. Penulis menekankan bahwa klasifikasi tersebut berfokus pada cara informasi dipropagasikan antar-node pada satu waktu, bukan satu-satunya taksonomi untuk seluruh arsitektur ST-GNN.

**Konstruksi graf**
- Struktur graf dapat sudah tersedia dari domain, misalnya jaringan jalan dan persimpangan.
- Jika tidak tersedia secara alami, struktur graf dapat ditentukan oleh peneliti berdasarkan pengetahuan domain atau metrik tertentu, atau dipelajari oleh model.
- Graf yang ditentukan sebelumnya dapat dibangun berdasarkan jarak fisik atau kemiripan data.
- Bobot edge dapat ditetapkan oleh peneliti atau dipelajari model.
- Review membahas pilihan adjacency statis, adjacency dinamis, dan pendekatan gabungan antara backbone graf statis dengan adjacency dinamis.
- Penulis menyatakan tidak ada satu metode konstruksi graf yang selalu paling baik; pemilihannya bergantung pada domain dan dataset.

**Temuan sintesis**
- Dalam subset model berkinerja tinggi yang dianalisis lintas domain, graph convolution merupakan mekanisme agregasi spasial yang dominan; agregasi spasial berbasis attention lebih jarang.
- Penulis mengaitkan dominasi convolution dengan efisiensi dan stabilitas pelatihan, bukan menyatakan bahwa attention selalu lebih buruk.
- Pada beberapa domain, model memakai adjacency yang ditentukan sebelumnya; pada perkembangan lebih baru, model dengan adjacency yang dipelajari atau pendekatan hybrid semakin banyak digunakan.
- Review mencakup banyak domain, termasuk mobility/traffic, energy, environment, finance, health, dan predictive monitoring. Fokusnya tetap pada forecasting dan classification time series, bukan optimasi evakuasi secara langsung.

**Tantangan yang dinyatakan penulis**
- Comparability: belum tersedia benchmark ST-GNN yang terstandarisasi sehingga hasil antarpenelitian sulit dibandingkan.
- Reproducibility: deskripsi model, struktur graf, jumlah node, bobot edge, kode, dan dataset kadang tidak lengkap.
- Poor information capacity: struktur graf yang tidak representatif atau terlalu jarang, serta kurangnya batasan fisik, dapat menurunkan performa.
- Scalability: perhitungan adjacency dan embedding dapat membutuhkan memori dan komputasi besar.
- Heterogeneity: mayoritas model dirancang untuk graf homogen; pemrosesan graf dengan tipe node, edge, atau input berbeda masih menjadi tantangan.
- Explainability: banyak model tetap sulit dijelaskan dan dipahami proses pengambilan keputusannya.

**Relevansi untuk penelitian ini**
- Ini merupakan referensi paling langsung di antara tiga publikasi tahap 3 untuk menjelaskan konsep umum ST-GNN.
- Mendukung pembahasan pemisahan/penggabungan komponen spasial dan temporal, pilihan mekanisme spasial, serta strategi konstruksi graf.
- Dapat menjadi dasar untuk menjelaskan mengapa graf gedung perlu dirancang sesuai pengetahuan domain: konektivitas ruang, koridor, tangga, dan pintu bukan sekadar korelasi statistik.
- Pembahasan heterogeneity mendukung alasan perlunya memperhatikan perbedaan jenis node/edge, tetapi artikel juga mengingatkan bahwa pemrosesan heterogen masih merupakan tantangan.
- Tidak membuktikan bahwa satu arsitektur ST-HGAT tertentu unggul pada simulasi evakuasi. Klaim kinerja harus diuji pada lingkungan dan metrik penelitian sendiri.

**Catatan versi dan metadata**
- Versi jurnal: *Neural Networks*, Vol. 195, Article 108269, Maret 2026, DOI 10.1016/j.neunet.2025.108269.
- Naskah lengkap yang dapat ditelaah pada tahap ini adalah preprint arXiv:2410.22377v4 bertanggal 3 November 2025. Gunakan metadata versi jurnal untuk daftar pustaka, dan periksa kembali apakah ada perubahan isi pada versi final jika PDF final repository berbeda.

### R-19 — Yang dan Peng (2024)

**Judul:** Spatio-Temporal Contrastive Heterogeneous Graph Attention Networks for Session-Based Recommendation  
**Publikasi:** *Mathematics*, Vol. 12, Issue 8, Article 1193 (2024), diterbitkan 16 April 2024.  
**DOI:** https://doi.org/10.3390/math12081193  
**Lokasi repository:** `2.5-ST-HGAT/`  
**Status:** Dibaca dari PDF lengkap (16 halaman).

**Tujuan dan masalah**
Penelitian mengembangkan STC-HGAT untuk session-based recommendation. Penulis menilai model rekomendasi berbasis graf sebelumnya cenderung memanfaatkan struktur spasial item tetapi mengabaikan informasi temporal dan menghadapi masalah sparsity pada urutan interaksi.

**Metode dan arsitektur STC-HGAT**
1. **Spatial heterogeneous hypergraph**
   - Urutan sesi dimodelkan sebagai hypergraph.
   - Sliding window membentuk hyperedge yang menghubungkan item-item dalam jendela tersebut.
   - LDA digunakan untuk membentuk category nodes berdasarkan kategori/topik item sehingga informasi konteks pada hypergraph bertambah.
   - HyperGAT mempelajari tingkat kepentingan hubungan node dan hyperedge untuk menangkap informasi spasial/struktur urutan.
2. **Temporal heterogeneous graph**
   - Graf temporal dibangun untuk mengagregasi informasi urutan/waktu interaksi item.
   - HGAT digunakan untuk memberi bobot pada hubungan item dan sesi serta mengagregasi informasi temporal.
3. **Information fusion**
   - Representasi spasial dan temporal digabungkan menggunakan sumpooling dan mekanisme attention.
4. **Contrastive learning**
   - Contrastive learning digunakan sebagai tugas tambahan untuk meningkatkan mutual information antara representasi spasial dan temporal serta mengurangi dampak sparsity.
5. **Adaptive-weight loss**
   - Penulis menambahkan modulation factor pada cross-entropy loss untuk membentuk adaptive-weight loss.

**Data dan evaluasi**
- Dataset yang digunakan adalah Diginetica, Yoochoose1/64, dan Yoochoose1/4.
- Metrik yang digunakan adalah Precision@20 (P@20) dan Mean Reciprocal Rank@20 (MRR@20).
- Baseline meliputi FPMC, GRU4Rec, STAMP, SR-GNN, GCE-GNN, SHARE, HIDE, COTREC, HCCF, STAM, dan TMI-GNN.
- Pada Tabel 2, STC-HGAT memperoleh:
  - Diginetica: P@20 55,40 dan MRR@20 19,01.
  - Yoochoose1/64: P@20 72,12 dan MRR@20 31,57.
  - Yoochoose1/4: P@20 72,62 dan MRR@20 31,19.
- Penulis melaporkan p-value 0,001; 0,001; 0,001; 0,01; 0,001; dan 0,001 untuk pasangan metrik/dataset yang dibandingkan dengan baseline terbaik, semuanya di bawah 0,05.
- Ablation study menunjukkan penghapusan komponen spasial, temporal, contrastive learning, category nodes, atau adaptive-weight loss memengaruhi hasil. Secara umum, model lengkap menghasilkan hasil terbaik pada mayoritas metrik, walaupun terdapat pengecualian pada salah satu hasil Yoochoose1/64 untuk varian tanpa category nodes.

**Catatan penting mengenai nama ST-HGAT**
Di dalam paper, model utama bernama **STC-HGAT** (Spatio-Temporal Contrastive Heterogeneous Graph Attention Network). Istilah **ST-HGAT** pada paper muncul sebagai salah satu varian ablation yang menghilangkan contrastive learning. Jadi, ST-HGAT dalam judul/rancangan Tugas Akhir kita tidak boleh dianggap identik dengan model utama STC-HGAT milik Yang dan Peng.

**Keterbatasan yang dinyatakan penulis**
- Domain penelitian adalah rekomendasi item berdasarkan urutan interaksi, bukan navigasi atau evakuasi.
- Penulis menyatakan real-time performance hasil rekomendasi masih perlu dipertimbangkan.
- Graph compression seperti low-rank factorization disebut sebagai kemungkinan untuk menekan kompleksitas.
- Noise pada urutan interaksi masih dapat memengaruhi performa.

**Relevansi untuk penelitian ini**
- Memberikan contoh implementasi yang menggabungkan struktur heterogen, representasi spasial, representasi temporal, attention, dan fusi fitur.
- Dapat dijadikan referensi pembanding untuk menjelaskan bagaimana komponen spasial dan temporal bisa dirancang secara terpisah lalu digabungkan.
- Konsep hypergraph dan LDA tidak otomatis perlu digunakan dalam penelitian evakuasi; pemakaiannya harus didasarkan pada kebutuhan relasi dan data yang tersedia.
- Hasil P@20/MRR@20 tidak dapat dibandingkan langsung dengan metrik evakuasi seperti waktu evakuasi, panjang rute, kepadatan, atau jumlah konflik.
- Paper ini bukan bukti langsung bahwa STC-HGAT atau ST-HGAT sesuai untuk optimasi rute evakuasi gedung.

## B. Sintesis untuk subbab 2.5 ST-HGAT

### 1. Perbedaan istilah yang harus dijaga
- **Dynamic GNN**: dalam survei Zheng et al., fokus pada graf yang node, edge, atau atributnya berkembang dari waktu ke waktu; dibedakan menjadi snapshot diskret dan event kontinu.
- **Spatio-Temporal GNN**: dalam review Corradini et al., memodelkan keterkaitan spasial antar-node dan ketergantungan temporal pada fitur/observasi.
- **Heterogeneous GNN**: menangani tipe node, edge, atau input yang berbeda.
- **STC-HGAT**: arsitektur spesifik Yang dan Peng untuk rekomendasi sesi; bukan nama generik untuk semua ST-HGAT.

### 2. Dasar konseptual yang dapat digunakan
- ST-GNN dapat memisahkan pemrosesan spasial dan temporal atau mengintegrasikannya.
- Pemrosesan spasial dapat menggunakan convolution, attention, recurrent, atau hybrid.
- Attention dapat memberi bobot berbeda pada informasi tetangga/relasi.
- Pemrosesan heterogen dibutuhkan ketika graf memiliki tipe node dan/atau relasi yang berbeda.
- Representasi spasial dan temporal dapat digabungkan setelah masing-masing diproses.

### 3. Implikasi untuk graf evakuasi kampus
Sebagai interpretasi desain penelitian (bukan hasil langsung dari ketiga artikel):
- Topologi ruang gedung dapat dimodelkan sebagai graf yang relatif tetap selama satu skenario, sementara fitur dinamis seperti okupansi, kepadatan, antrean, dan status akses diperbarui pada setiap langkah simulasi.
- Node dapat merepresentasikan jenis lokasi berbeda, misalnya ruang, koridor, tangga, dan pintu/exit, apabila rancangan graf memang mendefinisikan tipe-tipe tersebut.
- Edge dapat merepresentasikan konektivitas atau jenis perpindahan antarlokasi; atribut edge dapat memuat jarak, kapasitas, atau status akses jika tersedia dan didefinisikan dalam metodologi.
- Komponen spasial mempelajari hubungan antar lokasi; komponen temporal mempelajari perubahan kondisi lokasi antar waktu.
- Representasi yang dihasilkan dapat diteruskan ke PPO sebagai state/observasi untuk pemilihan aksi, tetapi detail antarmuka ST-HGAT–PPO harus dijelaskan dan diuji pada BAB III.

### 4. Hal yang belum boleh diklaim
- Belum ada bukti dari ketiga publikasi bahwa ST-HGAT adalah arsitektur terbaik untuk evakuasi.
- Belum ditetapkan bahwa penelitian perlu menggunakan hypergraph, LDA, contrastive learning, atau dynamic adjacency.
- Belum ditetapkan apakah topologi graf harus berubah saat simulasi; perubahan status pintu/koridor dapat direpresentasikan sebagai atribut/edge availability tanpa mengubah definisi node dan koneksi permanen, jika memang itu yang dipilih dalam model.
- Tidak boleh mengutip hasil rekomendasi STC-HGAT sebagai hasil kinerja evakuasi.
- Istilah ST-HGAT harus didefinisikan secara operasional dalam penelitian, termasuk modul spasial, modul temporal, tipe node/edge, fusi representasi, dan keluaran ke PPO.

## C. Catatan bibliografi

1. Zheng et al. (2025): metadata BibTeX pada repository sesuai dengan artikel jurnal Vol. 19, Issue 6, Article 196323; tanggal publikasi online 12 Desember 2024.
2. Corradini et al. (2026): metadata jurnal Vol. 195, Article 108269, Maret 2026, DOI 10.1016/j.neunet.2025.108269 sesuai dengan versi jurnal. Naskah lengkap yang dibaca adalah preprint arXiv versi 4.
3. Yang dan Peng (2024): metadata *Mathematics*, Vol. 12, Issue 8, Article 1193, DOI 10.3390/math12081193 sesuai.

## D. Status pembacaan setelah tahap 3

- Total PDF terinventarisasi di repository: 30.
- Publikasi yang telah dibaca penuh/isi utama pada tahap 1–3: 10.
- Publikasi yang dibaca sebagian: 1 (Rizian et al.; halaman artikel/abstrak dan metadata, belum PDF lengkap).
- Publikasi yang belum dibaca: 18.
- Tahap 3 menyelesaikan tiga referensi pada folder 2.5-ST-HGAT.

## E. Referensi tahap 3

- Y. Zheng, L. Yi, and Z. Wei, “A survey of dynamic graph neural networks,” *Frontiers of Computer Science*, vol. 19, no. 6, art. 196323, 2025, doi: 10.1007/s11704-024-3853-2.
- F. Corradini, F. Gerosa, M. Gori, C. Lucheroni, M. Piangerelli, and M. Zannotti, “A systematic literature review of spatio-temporal graph neural network models for time series forecasting and classification,” *Neural Networks*, vol. 195, art. 108269, 2026, doi: 10.1016/j.neunet.2025.108269.
- F. Yang and D. Peng, “Spatio-temporal contrastive heterogeneous graph attention networks for session-based recommendation,” *Mathematics*, vol. 12, no. 8, art. 1193, 2024, doi: 10.3390/math12081193.

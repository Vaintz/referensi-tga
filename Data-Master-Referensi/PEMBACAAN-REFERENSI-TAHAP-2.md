# Catatan Pembacaan Referensi — Tahap 2

**Topik Tugas Akhir:** Optimasi Rute Evakuasi Dinamis pada Lingkungan Gedung Kampus Menggunakan ST-HGAT dan PPO.

**Tanggal pemeriksaan:** 10 November 2026

## Cakupan dan cara pemeriksaan

Tahap ini menelaah lima publikasi yang berada pada kategori BAB II 2.3 (Teori Graf dan Pemodelan Lingkungan Evakuasi) dan 2.4 (Graph Neural Network). Isi artikel diperiksa melalui naskah lengkap/halaman penerbit yang dapat diakses secara terbuka, lalu dicocokkan dengan judul dan DOI pada entri repository. Jadi, catatan ini berbasis isi publikasi yang cocok dengan referensi di repository, bukan sekadar abstrak BibTeX. Untuk naskah Sharma, teks PDF penerbit tersedia; untuk Jaeger, GraphSAGE++, Fathinezhad, dan Rizian, isi utama diperiksa dari halaman teks penerbit yang memuat bagian artikel.

## A. Publikasi yang ditelaah

### R-12 — Sharma et al. (2025)

**Judul:** Graph Representation Techniques And Their Applications  
**Publikasi:** International Journal of Creative Research Thoughts (IJCRT), Vol. 13, Issue 6, Juni 2025, hlm. d444–d450.  
**DOI:** Tidak tercantum pada PDF/halaman artikel yang diperiksa.  
**Lokasi repository:** `2.3-Teori-Graf-dan-Pemodelan-Lingkungan-Evakuasi/`  
**Status:** Dibaca dari PDF lengkap (7 halaman).

**Fokus dan isi**
Artikel membahas cara merepresentasikan graf di memori dan dampaknya terhadap efisiensi algoritma. Bentuk yang dibahas meliputi adjacency matrix, adjacency list, dan edge list. Artikel juga memperkenalkan jenis graf seperti directed, undirected, weighted, unweighted, cyclic, dan acyclic, serta kaitannya dengan BFS, DFS, Dijkstra, dan A*.

**Temuan teknis yang dinyatakan**
- Adjacency matrix berukuran V × V, dengan nilai sel menunjukkan ada/tidaknya sisi atau bobot sisi.
- Untuk graf tak berarah, matriks adjacency bersifat simetris; untuk graf berarah, nilainya dapat tidak simetris.
- Penyimpanan adjacency matrix membutuhkan ruang O(V²), sehingga dapat boros untuk graf sparse.
- Adjacency list menyimpan daftar tetangga tiap simpul; traversal BFS/DFS pada representasi ini memiliki kompleksitas O(V + E) untuk graf sparse.
- Artikel menyimpulkan adjacency list lebih sesuai untuk graf sparse, sedangkan adjacency matrix bermanfaat pada graf dense atau saat pemeriksaan keberadaan sisi perlu dilakukan secara sering.
- Untuk algoritma shortest path seperti Dijkstra atau A*, artikel menyebut adjacency list yang dipasangkan dengan priority queue umumnya lebih efisien.

**Relevansi untuk penelitian ini**
- Dapat menjadi pengantar sederhana untuk menjelaskan representasi graf dan pilihan struktur penyimpanan.
- Mendukung penjelasan bahwa graf gedung dapat direpresentasikan melalui simpul dan sisi, lalu dipilih representasi data sesuai kepadatan graf dan operasi yang dibutuhkan.
- Untuk graf layout gedung yang cenderung memiliki koneksi lokal terbatas dibanding seluruh pasangan simpul, adjacency list layak dipertimbangkan; ini merupakan implikasi desain untuk penelitian, bukan hasil eksperimen Sharma pada graf gedung.
- Artikel tidak membahas pemodelan gedung, GNN, ST-HGAT, atau PPO secara khusus.

**Catatan kritis dan verifikasi metadata**
- PDF menampilkan tujuh penulis: Om Santosh Sharma, Akhilesh Ghatage, Rohan Thosar, Devamsh Kumar, Kunal Naik, Kushagra Singh, dan Reshma Sonar. Entri `library.bib` saat ini hanya mencantumkan empat penulis, sehingga perlu diperbaiki.
- Judul dan halaman pada PDF adalah d444–d450, Juni 2025, Vol. 13 Issue 6.
- Artikel bersifat pengantar/perbandingan representasi graf. Untuk definisi formal graf dan teori algoritma yang lebih kuat, sebaiknya dilengkapi sumber buku atau publikasi dasar yang lebih mapan; jangan menjadikan artikel ini satu-satunya landasan teori graf.

### R-13 — Jiawei et al. (2024)

**Judul:** GraphSAGE++: Weighted Multi-scale GNN for Graph Representation Learning  
**Publikasi:** Neural Processing Letters, Vol. 56, Article 24 (2024).  
**DOI:** https://doi.org/10.1007/s11063-024-11496-1  
**Lokasi repository:** `2.3-Teori-Graf-dan-Pemodelan-Lingkungan-Evakuasi/`  
**Status:** Dibaca dari naskah lengkap pada laman penerbit (open access).

**Tujuan dan masalah**
Penulis menyoroti dua keterbatasan pada beberapa GNN: over-smoothing ketika kedalaman jaringan bertambah dan dominasi informasi tetangga lokal yang dapat mengabaikan struktur global. Kondisi tersebut dapat membuat representasi simpul sulit dibedakan.

**Metode**
- Mengembangkan GraphSAGE++ dari GraphSAGE.
- Pada setiap layer, representasi simpul disimpan sehingga informasi dari tetangga dengan jarak hop berbeda tetap tersedia.
- Representasi dari beberapa layer digabungkan dengan weighted concatenation, dengan bobot berbeda untuk informasi pada hop berbeda.
- Penulis mengembangkan varian double aggregation, yaitu kombinasi agregasi Mean dan Max: GraphSAGE++DA, GraphSAGE++DAC, dan GraphSAGE++DAMC.
- Eksperimen menggunakan beberapa dataset graf, antara lain Cora, Citeseer, Amazon, PubMed, PPI, ENZYMES, dan KarateClub.
- Implementasi menggunakan PyTorch Geometric; pengaturan eksperimen yang dilaporkan antara lain dimensi 128, learning rate 0,001, batch size 64, maksimum K=8 hop, Adam, dan regularisasi L2.

**Hasil utama**
- Pada klasifikasi simpul, GraphSAGE++DAC dan GraphSAGE++DAMC secara umum menunjukkan hasil lebih baik dibanding beberapa baseline pada dataset yang diuji.
- Pada PPI, GraphSAGE++DAMC dilaporkan meningkat sekitar 7% dibanding GraphSAGE pada kondisi training set 50%.
- Pada Amazon, GraphSAGE++DAC meningkat sekitar 13% dibanding GraphSAGE pada training set 90%.
- Pada link prediction, GraphSAGE++DAMC meningkat sekitar 7% dibanding GraphSAGE pada Cora dengan training set 50%; GraphSAGE++DAC meningkat sekitar 20% pada PubMed dengan training set 70%.
- Penulis juga menyatakan adanya overhead waktu komputasi karena operasi concatenation; model usulan tidak selalu paling cepat dibanding SVD-GCN, GraphSNN, dan DGCN.

**Relevansi untuk penelitian ini**
- Berguna untuk memahami agregasi informasi tetangga dan representasi multi-hop dalam GNN.
- Dapat membantu menjelaskan mengapa representasi graf tidak hanya bergantung pada tetangga langsung, tetapi juga dapat memanfaatkan informasi dari beberapa hop.
- Memberi konteks tentang trade-off antara kualitas representasi dan biaya komputasi.
- Bukan arsitektur ST-HGAT dan bukan studi evakuasi. Hasilnya pada dataset klasifikasi/link prediction umum tidak dapat dijadikan bukti bahwa arsitektur ST-HGAT akan efektif untuk evakuasi.

**Catatan kritis**
GraphSAGE++ adalah varian GraphSAGE, bukan HGAT. Jangan menyamakan weighted concatenation antar-layer dengan mekanisme attention pada heterogenous graph. Konsepnya dapat dibandingkan, tetapi fungsi dan mekanismenya berbeda.

### R-14 — Jaeger (2023)

**Judul:** Learning and Reasoning with Graph Data  
**Publikasi:** Frontiers in Artificial Intelligence, Vol. 6, Article 1124718, diterbitkan 22 Agustus 2023.  
**DOI:** https://doi.org/10.3389/frai.2023.1124718  
**Lokasi repository:** `2.3-Teori-Graf-dan-Pemodelan-Lingkungan-Evakuasi/`  
**Status:** Dibaca dari artikel lengkap open access.

**Fokus dan ruang lingkup**
Artikel merupakan review konseptual yang memberikan peta umum tentang pembelajaran dan penalaran menggunakan data graf. Pembahasan mencakup graph representation learning, GNN, statistical relational learning, graph kernels, serta pendekatan berbasis logika. Penulis menyatakan bahwa cakupan artikel bersifat luas dan konseptual, bukan tutorial teknis mendalam untuk satu arsitektur GNN.

**Pokok isi**
- Graf digunakan sebagai abstraksi untuk jaringan dunia nyata seperti jaringan sosial, sensor, biologi, dan lalu lintas.
- Representasi graf dapat diperluas dengan atribut simpul dan beberapa jenis relasi sisi (multi-relational, attributed graphs).
- Penulis membedakan tugas pembelajaran dan penalaran pada graf; contoh tugas pembelajaran termasuk node classification.
- Dalam node classification, model memprediksi label simpul yang belum diketahui dari struktur graf dan atribut simpul.
- Artikel membedakan setting inductive dan transductive: inductive berkaitan dengan prediksi pada simpul/graf baru yang tidak ada pada graf pelatihan, sedangkan transductive memprediksi label simpul yang belum diketahui dalam graf yang sudah tersedia saat pelatihan.
- Pembelajaran model dijelaskan melalui kerangka probabilistik dan prinsip maximum likelihood; dalam praktik, objective dapat dimodifikasi dengan regularisasi atau prior.
- Artikel juga membahas bahwa GNN membangun representasi fitur simpul secara berurutan dan berada dalam spektrum metode pembelajaran graf bersama pendekatan lain.

**Relevansi untuk penelitian ini**
- Berguna sebagai sumber konseptual untuk memahami graf beratribut dan multi-relasional.
- Dapat mendukung penjelasan bahwa lingkungan evakuasi tidak harus direpresentasikan sebagai graf sederhana dengan satu jenis relasi saja; secara konseptual, tipe simpul dan relasi dapat dibedakan.
- Berguna untuk membedakan setting inductive dan transductive jika hal tersebut memang relevan dengan rancangan eksperimen penelitian.
- Tidak memberikan rancangan khusus untuk graf gedung, ST-HGAT, atau optimasi evakuasi.

**Catatan kritis**
Artikel merupakan review konseptual yang luas. Gunakan untuk kerangka umum dan istilah, bukan sebagai sumber utama untuk persamaan operasional ST-HGAT atau implementasi PPO.

### R-15 — Rizian et al. (terbitan/issue 2025; sitasi jurnal menampilkan Januari 2026)

**Judul:** Enhancing Classification of Self-Reported Monkeypox Symptoms on Social Media Using Term Frequency-Inverse Document Frequency Features and Graph Attention Networks  
**Publikasi:** Jurnal Teknik Informatika (JUTIF), Vol. 6, No. 6, hlm. 5865–5881. Halaman sitasi jurnal menampilkan Januari 2026, sementara metadata issue menyebut Vol. 6 No. 6 (2025), Desember 2025.  
**DOI:** https://doi.org/10.52436/1.jutif.2025.6.6.5482  
**Lokasi repository:** `2.4-Graph-Neural-Network/`  
**Status:** Dibaca dari halaman artikel lengkap/abstrak dan metadata penerbit; PDF lengkap tidak tersedia melalui halaman yang diperiksa.

**Tujuan dan metode**
- Penelitian mengembangkan klasifikasi gejala monkeypox yang dilaporkan pengguna media sosial Indonesia.
- Dataset terdiri dari 3.200 tweet, diproses dan diberi label manual; distribusi label positif 51% dan negatif 49%.
- TF-IDF digunakan untuk membentuk fitur teks.
- Vektor TF-IDF digunakan untuk membangun graf kemiripan dokumen dengan k-Nearest Neighbors (k-NN) dan cosine similarity.
- GAT digunakan untuk memanfaatkan informasi teks dan hubungan antardokumen pada graf.
- Evaluasi menggunakan accuracy, precision, recall, dan macro-F1; macro-F1 dinyatakan sebagai indikator utama.

**Hasil utama**
Model TF-IDF + GAT memperoleh accuracy 93,07% dan macro-F1 93,06%. Pada macro-F1, hasil ini dilaporkan lebih tinggi dibanding CNN (92,16%), SVM (85,73%), dan Logistic Regression (84,89%).

**Relevansi untuk penelitian ini**
- Memberikan contoh penerapan GAT pada graf yang dibangun dari kemiripan fitur, dengan perhatian terhadap relasi antar-node.
- Dapat digunakan sebagai contoh empiris bahwa GAT dapat memanfaatkan fitur node dan struktur hubungan graf secara bersamaan.
- Domainnya adalah klasifikasi teks media sosial, bukan jaringan ruang gedung atau pergerakan penghuni. Karena itu, hasil akurasi 93,07% tidak relevan untuk mengklaim performa GAT/ST-HGAT pada evakuasi.
- Untuk subbab 2.4, sumber ini hanya pendukung contoh aplikasi GAT, bukan referensi utama teori GAT.

**Catatan metadata dan akses**
- Entri BibTeX bernama `Rizian2026` sesuai dengan tahun pada format sitasi artikel yang menampilkan Januari 2026.
- Halaman issue menyebut Vol. 6 No. 6 (2025), Desember 2025, dan DOI mengandung 2025. Ada perbedaan antara tahun issue dan tanggal sitasi yang ditampilkan; pertahankan metadata sesuai format sitasi resmi penerbit yang dipakai, lalu verifikasi dari PDF final jika tersedia.
- Halaman penerbit menyatakan unduhan data belum tersedia; pemeriksaan tahap ini tidak mencakup keseluruhan PDF.

### R-16 — Fathinezhad et al. (2023)

**Judul:** Graph Neural Networks and Reinforcement Learning: A Survey  
**Publikasi:** Chapter dalam buku *Deep Learning and Reinforcement Learning*, IntechOpen, diterbitkan 23 Mei 2023.  
**DOI:** https://doi.org/10.5772/intechopen.111651  
**Lokasi repository:** `2.4-Graph-Neural-Network/`  
**Status:** Dibaca dari naskah lengkap bab open access.

**Fokus dan metode pembahasan**
Bab ini merupakan survey tentang hubungan GNN dan deep reinforcement learning (DRL), khususnya pada masalah berbasis graf dan multi-agent. Penulis membahas GNN, latar belakang DRL/MARL, interaksi antar-agent dengan arsitektur GNN, serta penggunaan DRL untuk mengembangkan GNN.

**Pokok isi**
- GNN ditujukan untuk data non-Euclidean yang memiliki struktur graf; representasi dapat dipelajari pada tingkat node, edge, maupun graph.
- Message passing merupakan komponen utama GNN: node memperbarui representasinya dengan bertukar/mengagregasi informasi dari tetangga.
- Secara umum, GNN terdiri atas proses message passing untuk mengekstraksi fitur lokal dan readout untuk merangkum representasi graf.
- Kombinasi GNN dan DRL dapat membantu pemodelan relasi pada masalah berbasis jaringan serta generalisasi pada topologi yang berbeda atau belum pernah dilihat.
- Survey membahas dua arah integrasi: GNN digunakan untuk meningkatkan representasi/performa DRL; atau DRL digunakan untuk meningkatkan GNN, misalnya neural architecture search, interpretabilitas, dan adversarial graph modification.
- Pada contoh arsitektur yang dijelaskan, embedding observasi agen diproses oleh attention untuk membentuk bobot relasi, lalu graph convolution melakukan message passing, dan DQN menghasilkan nilai aksi.
- Penulis juga membahas masalah multi-agent seperti non-stationarity, koordinasi, credit assignment, dan pertumbuhan ruang state-action seiring bertambahnya jumlah agen.
- Bab ini menyinggung contoh job-shop scheduling yang menggunakan GNN untuk struktur spasial dan PPO untuk keputusan berurutan; contoh tersebut merupakan domain penjadwalan, bukan evakuasi.

**Relevansi untuk penelitian ini**
- Sumber penting untuk menjelaskan alasan konseptual penggabungan GNN dan RL pada masalah yang memiliki struktur graf dan keputusan berurutan.
- Mendukung peran GNN sebagai encoder/representasi struktur dan RL sebagai komponen pembelajaran keputusan.
- Dapat digunakan untuk membahas kemungkinan perhatian (attention) dalam memodelkan bobot hubungan antar-node/agen.
- Pembahasan multi-agent tidak berarti penelitian ini harus menggunakan MARL. Pilihan jumlah agen/policy pada penelitian tetap harus ditentukan dari rancangan sistem sendiri.
- Tidak membuktikan bahwa ST-HGAT + PPO paling baik untuk evakuasi gedung kampus.

**Keterbatasan/catatan kritis**
- Ini adalah survey, bukan eksperimen evakuasi.
- Sebagian besar contoh integrasi GNN-RL yang dibahas berfokus pada multi-agent; jangan mengadopsi asumsi multi-agent ke rancangan penelitian tanpa kebutuhan dan formulasi yang jelas.
- Penulis mengidentifikasi tantangan berupa state space yang besar, waktu konvergensi yang lama, koordinasi, dan kesulitan menentukan objective/reward yang sesuai.

## B. Sintesis sementara untuk subbab 2.3 dan 2.4

### 2.3 Teori Graf dan Pemodelan Lingkungan Evakuasi
- Sharma et al. dapat menjadi pengantar struktur penyimpanan graf (adjacency matrix/list/edge list) dan trade-off kompleksitasnya, tetapi perlu didampingi sumber teori graf yang lebih kuat.
- Jaeger memberikan landasan konseptual untuk graf beratribut dan multi-relasional, serta menjelaskan bahwa simpul dapat memiliki atribut dan relasi graf dapat terdiri atas beberapa tipe.
- Jiawei et al. memberikan contoh GNN yang mengagregasi informasi tetangga multi-hop dan menggabungkan representasi dari beberapa layer.
- Untuk model lingkungan gedung, interpretasi yang mungkin adalah simpul mewakili ruang/lokasi (ruangan, koridor, tangga, pintu/exit) dan sisi mewakili konektivitas/perpindahan. Ini merupakan rancangan representasi penelitian, bukan klaim yang diuji oleh ketiga artikel graf tersebut.

### 2.4 Graph Neural Network
- Fathinezhad et al. mendukung konsep message passing, representasi node/edge/graph, dan hubungan umum antara GNN dan DRL.
- Rizian et al. memberikan contoh penerapan GAT yang menggabungkan fitur node dengan hubungan graf, tetapi konteksnya klasifikasi dokumen media sosial.
- Jiawei et al. menjelaskan agregasi multi-hop dan weighted concatenation, namun bukan attention.
- Secara keseluruhan, kelima sumber ini memberi dasar konsep graf dan GNN, tetapi belum cukup untuk menjelaskan secara rinci mekanisme ST-HGAT yang akan digunakan. Subbab 2.5 tetap memerlukan pembacaan khusus atas sumber ST-GNN, dynamic graph, dan heterogeneous graph attention.

## C. Perbaikan metadata yang perlu dilakukan pada library.bib

1. **Sharma2025:** daftar penulis di BibTeX tidak lengkap. PDF mencantumkan tujuh penulis, sedangkan BibTeX hanya empat.
2. **Jaeger2023:** tipe entri saat ini `@misc`, sebaiknya diperbaiki menjadi `@article` dengan jurnal *Frontiers in Artificial Intelligence*, volume 6, article 1124718, DOI 10.3389/frai.2023.1124718.
3. **Rizian2026:** perbedaan tahun issue (2025) dan format sitasi penerbit (Jan 2026) perlu dipertahankan sebagai catatan verifikasi sampai PDF final dipastikan.
4. **Fathinezhad2023:** tipe `@inbook` sesuai karena sumber merupakan bab buku, bukan artikel jurnal.
5. **Jiawei2024:** data penerbit mencantumkan Vol. 56, Article 24, 2024, DOI 10.1007/s11063-024-11496-1.

## D. Implikasi bagi penelitian

1. Struktur graf lingkungan dapat dirancang untuk menampung atribut simpul dan beberapa tipe relasi; detail tipe node/edge harus ditentukan berdasarkan denah dan proses evakuasi yang dimodelkan.
2. GNN menyediakan mekanisme agregasi informasi tetangga untuk membentuk representasi graf. Informasi multi-hop berpotensi berguna untuk memahami hubungan lokasi yang tidak hanya bertetangga langsung.
3. Attention dapat dipakai untuk memberi bobot berbeda pada relasi atau informasi tetangga, tetapi mekanisme attention spesifik ST-HGAT harus didukung sumber 2.5, bukan disimpulkan dari contoh GAT pada klasifikasi teks.
4. Integrasi GNN dan RL mempunyai landasan konseptual untuk keputusan pada lingkungan graf. Formulasi state, action, reward, dan policy untuk evakuasi harus tetap diturunkan dari rancangan penelitian sendiri dan sumber PPO/GRL yang relevan.
5. Tidak satu pun dari lima sumber tahap ini menjadi bukti langsung efektivitas ST-HGAT + PPO pada evakuasi gedung kampus.

## E. Status pembacaan setelah tahap 2

- Total PDF di repository: 30.
- Publikasi yang sudah ditelaah penuh/isi utama pada tahap 1 dan 2: 8.
- Publikasi yang baru ditelaah sebagian (metadata/abstrak/halaman artikel, belum PDF lengkap): 1 (Rizian et al.).
- Publikasi yang masih menunggu pembacaan: 21.
- Tahap 2 menambahkan empat sumber yang ditelaah dari naskah lengkap dan satu sumber yang ditelaah sebagian.

## F. Referensi yang diperiksa pada tahap ini

- O. S. Sharma, A. Ghatage, R. Thosar, D. Kumar, K. Naik, K. Singh, and R. Sonar, “Graph Representation Techniques And Their Applications,” *International Journal of Creative Research Thoughts*, vol. 13, no. 6, pp. d444–d450, Jun. 2025.
- E. Jiawei, Y. Zhang, S. Yang, H. Wang, X. Xia, and X. Xu, “GraphSAGE++: Weighted Multi-scale GNN for Graph Representation Learning,” *Neural Processing Letters*, vol. 56, art. 24, 2024, doi: 10.1007/s11063-024-11496-1.
- M. Jaeger, “Learning and reasoning with graph data,” *Frontiers in Artificial Intelligence*, vol. 6, art. 1124718, 2023, doi: 10.3389/frai.2023.1124718.
- R. A. Rizian, I. Budiman, M. R. Faisal, D. Kartini, F. Indriani, and U. A. Ahmad, “Enhancing Classification of Self-Reported Monkeypox Symptoms on Social Media Using Term Frequency-Inverse Document Frequency Features and Graph Attention Networks,” *Jurnal Teknik Informatika (JUTIF)*, vol. 6, no. 6, pp. 5865–5881. Penerbit menampilkan Januari 2026 pada format sitasi, sementara issue tercantum sebagai Desember 2025. doi: 10.52436/1.jutif.2025.6.6.5482.
- F. Fathinezhad, P. Adibi, B. Shoushtarian, and J. Chanussot, “Graph Neural Networks and Reinforcement Learning: A Survey,” in *Deep Learning and Reinforcement Learning*, IntechOpen, 2023, doi: 10.5772/intechopen.111651.

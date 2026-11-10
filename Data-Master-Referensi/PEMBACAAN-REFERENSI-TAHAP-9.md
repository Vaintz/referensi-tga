# Catatan Pembacaan Referensi — Tahap 9

**Topik Tugas Akhir:** Optimasi Rute Evakuasi Dinamis pada Lingkungan Gedung Kampus Menggunakan ST-HGAT dan PPO.

**Tanggal:** 10 November 2026

## Cakupan dan cara memperoleh teks
Tahap ini melanjutkan empat publikasi yang sebelumnya masih berstatus dibaca sebagian. Saya memeriksa kembali berkas pada repository GitHub `Vaintz/referensi-tga`. Keempat PDF memang ada di repository, tetapi konten PDF biner tidak dapat diekstrak oleh konektor GitHub yang tersedia. Untuk menghindari klaim palsu bahwa PDF GitHub sudah dibaca langsung, saya menggunakan salinan teks lengkap/penerbit yang dapat diakses untuk dua publikasi dan mempertahankan status sebagian untuk dua publikasi lainnya.

Hasil tahap ini:
- Wang et al. (2024): isi artikel 15 halaman berhasil ditelaah dari salinan teks lengkap yang tersedia daring; metadata dicocokkan dengan rekaman PubMed dan IEEE. Salinan teks bukan file yang diunduh dari repository GitHub.
- Faisal et al. (2026): PDF lengkap 18 halaman berhasil dibaca dari laman unduhan resmi BAREKENG/Universitas Pattimura.
- Ning dan Xie (2024): halaman penerbit SciOpen dan abstrak dibaca; PDF dinyatakan Open Access tetapi konten PDF lengkap tidak berhasil diambil melalui alat yang tersedia.
- Ghasemi et al. (2026): halaman artikel Springer Open Access dan abstrak dibaca; PDF lengkap tidak berhasil diambil melalui alat yang tersedia.

## A. R-21 — Wang et al. (2024)

**Judul:** “Deep Reinforcement Learning: A Survey.”
**Publikasi:** IEEE Transactions on Neural Networks and Learning Systems, Vol. 35, No. 4, April 2024, hlm. 5064–5078.
**DOI:** https://doi.org/10.1109/TNNLS.2022.3207346
**Status:** Dibaca penuh pada isi artikel yang tersedia (15 halaman). Metadata dicocokkan dengan PubMed/IEEE; teks penuh diperoleh dari salinan daring Scribd, bukan langsung dari file PDF GitHub.

### Tujuan dan kontribusi
Artikel menyajikan tinjauan DRL dengan mengelompokkan algoritma berdasarkan tujuan pembelajaran menjadi tiga kelompok: value-based, policy-based, dan maximum-entropy-based. Penulis juga membahas algoritma yang banyak digunakan, implementasi dalam pustaka DRL, serta arah penelitian untuk mengatasi keterbatasan metode.

### Dasar RL yang dibahas
- RL dirumuskan melalui Markov Decision Process (MDP), dengan state, action, reward, transition probability, dan discount factor.
- Return merupakan akumulasi reward masa depan yang didiskontokan.
- Value function dan action-value function dijelaskan melalui persamaan Bellman.
- Artikel menjelaskan perbedaan on-policy dan off-policy berdasarkan hubungan antara behavior policy dan target policy.
- Actor-critic menggabungkan pembelajaran policy dan value function: actor menghasilkan policy/aksi, sedangkan critic mengevaluasi policy menggunakan value atau advantage.

### Value-based DRL
- DQN mengganti Q-table konvensional dengan deep neural network untuk mengaproksimasi nilai Q pada state-action berukuran besar.
- Artikel membahas peningkatan DQN, termasuk target network dan experience replay, serta varian Double DQN, dueling network, prioritized experience replay, noisy network, distributional RL, DRQN, dan Rainbow.
- DRQN menggabungkan LSTM dengan DQN untuk menangani POMDP.
- Rainbow menggabungkan beberapa komponen peningkatan DQN; artikel mencatat komponen tersebut dapat saling melengkapi dalam eksperimen Atari.

### Policy-based DRL dan PPO
- Policy-gradient mengoptimalkan policy secara langsung, berbeda dari value-based yang mengestimasi nilai aksi untuk memperoleh policy.
- A3C mengumpulkan pengalaman secara paralel melalui beberapa worker dan menggunakan advantage serta n-step return.
- TRPO membatasi perubahan policy menggunakan trust-region/KL divergence untuk menjaga stabilitas pembaruan.
- PPO diperkenalkan sebagai penyederhanaan TRPO dengan objective yang dipotong (clipped objective). Rasio probabilitas policy baru terhadap policy lama dibatasi pada rentang [1−epsilon, 1+epsilon], lalu objective menggunakan nilai minimum antara objective biasa dan objective yang telah di-clip.
- Artikel juga membahas dual-clipped PPO sebagai pengembangan untuk mengatasi isu tertentu pada lingkungan off-policy berskala besar; ini bukan berarti PPO standar selalu gagal.
- DDPG dibahas sebagai deterministic actor-critic untuk continuous action space; TD3 menambahkan clipped double Q-learning, delayed policy update, dan target policy smoothing.

### Maximum-entropy DRL
- Maximum-entropy RL menambahkan entropy policy ke objective reward.
- Parameter temperature mengatur bobot antara reward dan entropy.
- Penulis mengaitkan entropy dengan stochastic policy dan eksplorasi yang lebih luas.
- Soft Actor-Critic (SAC) dijelaskan sebagai gabungan off-policy, actor-critic, dan maximum entropy.

### Arah penelitian yang dibahas
- Model-based RL: mempelajari model dinamika lingkungan agar dapat digunakan untuk planning dan/atau pelatihan policy.
- Hierarchical RL: memecah tujuan kompleks menjadi subtujuan atau beberapa tingkat kontrol.
- Multi-agent DRL: membahas interaksi agen, cooperative/competitive/mixed tasks, MADDPG, counterfactual baseline, VDN, dan QMIX.
- Learning from demonstrations: inverse RL dan imitation learning sebagai cara memanfaatkan demonstrasi ahli ketika reward sparse atau eksplorasi sulit.
- Meta-RL dan transfer RL: meningkatkan efisiensi belajar dan generalisasi ke tugas baru.
- Offline RL: belajar dari dataset terdahulu tanpa interaksi langsung saat training; salah satu masalah utamanya adalah distribution shift antara behavior policy pada data dan policy yang dipelajari.

### Relevansi untuk Tugas Akhir
- Sumber utama untuk mendukung penjelasan klasifikasi DRL, actor-critic, policy gradient, PPO, dan clipped objective.
- Dapat digunakan untuk menjelaskan bahwa PPO berada pada kelompok policy-based dan menggunakan pembatasan rasio policy untuk mengendalikan pembaruan.
- Pembahasan sample efficiency, sparse reward, model-based RL, dan multi-agent DRL dapat menjadi konteks tantangan, tetapi tidak otomatis menentukan desain penelitian.
- Artikel tidak menguji evakuasi gedung dan tidak membuktikan PPO merupakan algoritma terbaik untuk rute evakuasi.
- Pembahasan MARL di artikel tidak berarti penelitian ini harus menggunakan multi-agent PPO; keputusan agent architecture tetap mengikuti rancangan metodologi Tugas Akhir.

### Catatan kritis
- Artikel merupakan survey, bukan eksperimen komparatif baru.
- Banyak hasil dan klaim algoritmik dirangkum dari publikasi lain; untuk detail matematis PPO atau klaim performa spesifik, rujukan primer seperti Schulman et al. tetap lebih tepat.
- Salinan teks lengkap yang diakses berasal dari platform pihak ketiga; metadata bibliografi diverifikasi ke PubMed/IEEE, tetapi untuk kutipan akhir sebaiknya tetap menggunakan PDF resmi yang ada pada repository atau akses institusi.

**Halaman jurnal penting:** MDP dan dasar RL (hlm. 5064–5066); value-based/DQN (hlm. 5067–5070); policy-based, TRPO, PPO, DDPG/TD3 (hlm. 5071–5072); maximum entropy, model-based, hierarchical, multi-agent, imitation/offline/meta/transfer RL (hlm. 5073–5075).

## B. R-14 — Faisal et al. (2026)

**Judul:** “Natural Disaster Report on Social Media Classification Method Based on Word Embedding and Graph Attention Network.”
**Publikasi:** BAREKENG: Jurnal Ilmu Matematika dan Terapan, Vol. 20, No. 3, hlm. 2613–2630, 2026.
**DOI:** https://doi.org/10.30598/barekengvol20iss3pp2613-2630
**Status:** Dibaca penuh dari PDF unduhan resmi penerbit (18 halaman).

### Tujuan dan data
Penelitian mengklasifikasikan pesan/tweet terkait bencana alam ke dalam tiga kelas: direct eyewitness, non-eyewitness, dan don't know.
- Menggunakan tujuh dataset: empat dataset berbahasa Inggris (wildfires, earthquakes, hurricanes, floods) dan tiga dataset berbahasa Indonesia (earthquakes, floods, forest fires).
- Dataset Indonesia memiliki 1.000 pesan untuk setiap kelas pada masing-masing kategori bencana (3.000 pesan per dataset).
- Dataset Inggris memiliki distribusi kelas yang tidak seimbang.
- Model diuji pada data pesan media sosial, bukan pada pergerakan penghuni atau struktur bangunan.

### Metode dan representasi fitur
- Preprocessing dilakukan sebelum ekstraksi fitur.
- Tiga model word embedding digunakan: Word2Vec, FastText, dan GloVe; dimensi embedding yang disebutkan adalah 100.
- Vektor kata dalam satu pesan digabungkan melalui concatenation.
- Panjang fitur diseragamkan dengan zero-padding sampai panjang pesan terpanjang.
- Penulis menghasilkan 21 structured datasets dari tujuh dataset dan tiga embedding individual; kombinasi ketiga embedding juga dievaluasi.
- GCN dan GAT digunakan untuk klasifikasi. Setup mencantumkan dua layer, hidden layer 64, ReLU, Softmax, cosine similarity 0,5, 100 epoch, learning rate 0,01, dan Adam.
- GAT menggunakan attention coefficient untuk memberi bobot berbeda pada kontribusi tetangga, sedangkan GCN mengagregasikan fitur dengan normalisasi adjacency.
- Evaluasi menggunakan accuracy dan macro-F1.

### Hasil
- Abstrak melaporkan rata-rata F1 GCN 0,749 dan GAT 0,915.
- Pada dataset Inggris, GAT mencapai F1 0,93 untuk wildfires, 0,92 untuk earthquakes, 0,94 untuk hurricanes, dan 0,96 untuk floods.
- Pada dataset Indonesia, GAT mencapai F1 sekitar 1,00 untuk earthquakes, 0,99 untuk floods, dan 1,00 untuk forest fires.
- FastText memiliki performa standalone yang kuat secara keseluruhan, tetapi embedding yang digabungkan tidak selalu lebih baik.
- Penulis menyatakan concatenation beberapa embedding dapat menimbulkan redundansi dan meningkatkan dimensi fitur sehingga performa turun pada sebagian pengujian.
- Training menunjukkan fluktuasi akurasi pada beberapa epoch, sedikit indikasi overfitting, dan ketidakstabilan validation accuracy pada sebagian model.

### Catatan kritis dan inkonsistensi
1. **Jumlah model tidak konsisten:** bagian setup menyebut 41 model, sedangkan kesimpulan menyebut 56 model yang dievaluasi. Jangan menyebut jumlah model tanpa memberi catatan inkonsistensi ini.
2. **Konstruksi graf kurang dijelaskan:** tabel setup mencantumkan cosine similarity 0,5, tetapi uraian metode yang tersedia tidak menjelaskan secara cukup rinci definisi node, edge, pembentukan adjacency, atau bagaimana ambang similarity tersebut diterapkan. Jangan mengasumsikan detail konstruksi graf yang tidak dijelaskan.
3. **Pembagian data kurang rinci:** paper menyebut penggunaan 80% dari dataset hasil ekstraksi untuk tahap klasifikasi, tetapi rincian pembagian train/validation/test dan prosedur validasi silang perlu diperiksa lebih jauh sebelum mengklaim desain evaluasi tertentu.
4. **Hasil sangat tinggi pada dataset Indonesia:** perlu dicermati bersama desain split dan kemungkinan karakteristik dataset yang seimbang. Angka tersebut tidak otomatis menunjukkan generalisasi pada data baru atau domain lain.
5. **Domain tugas berbeda:** GAT mengklasifikasikan hubungan pesan teks; grafnya bukan graf ruang gedung dan hasil F1 tidak sebanding dengan waktu evakuasi, kepadatan, atau keselamatan.

### Relevansi untuk Tugas Akhir
- Memberi contoh penerapan GAT dan perbandingan GCN-GAT pada data terkait bencana.
- Dapat mendukung penjelasan bahwa attention menghasilkan bobot kontribusi tetangga yang adaptif.
- Dapat menjadi contoh bahwa representasi fitur dan konfigurasi graf memengaruhi hasil GNN.
- Tidak dapat dijadikan bukti langsung bahwa GAT/ST-HGAT akan efektif pada graf konektivitas ruang gedung atau bahwa PPO akan menghasilkan rute evakuasi yang lebih baik.

**Halaman jurnal penting:** motivasi/gap (hlm. 2614–2616); dataset dan word embedding (hlm. 2616–2618); GCN/GAT dan metrik (hlm. 2618–2620); setup dan hasil (hlm. 2621–2624); diskusi, keterbatasan, dan kesimpulan (hlm. 2624–2629).

## C. R-20 — Ning dan Xie (2024) — tetap dibaca sebagian

**Judul:** “A Survey on Multi-Agent Reinforcement Learning and Its Application.”
**Publikasi:** Journal of Automation and Intelligence, Vol. 3, No. 2, Juni 2024, hlm. 73–91.
**DOI:** https://doi.org/10.1016/j.jai.2024.02.003
**Status:** Halaman penerbit SciOpen dan abstrak telah dibaca. Artikel berstatus Open Access, tetapi konten PDF lengkap belum berhasil diambil melalui alat yang tersedia pada sesi ini.

### Informasi yang didukung abstrak
- Survey meninjau evolusi MARL dan karya survey terdahulu.
- Cakupan abstrak meliputi stochastic games, metode MARL, bentuk spasial, klasifikasi tugas, tantangan aplikasi, tuning hyperparameter, dan kompleksitas komputasi.
- Domain aplikasi yang disebut meliputi intelligent machines/devices, chemical engineering, biotechnology, healthcare, dan societal issues.
- Survey juga membahas benchmark environment untuk evaluasi MARL.

### Relevansi dan batas penggunaan
Sumber dapat menjadi referensi pendukung apabila penelitian membahas banyak agen yang belajar berinteraksi. Namun, desain Tugas Akhir belum menetapkan MARL atau multi-agent PPO. Rincian taksonomi, algoritma, benchmark, dan hasil perbandingan tidak boleh ditulis berdasarkan abstrak saja.

## D. R-24 — Ghasemi, Moosavi, dan Ebrahimi (2026) — tetap dibaca sebagian

**Judul:** “Reinforcement Learning and Model-based Planning in Practice: A Survey of Algorithmic Rationale and Domain Applications.”
**Publikasi:** Artificial Intelligence Review, 2026. Accepted research version dipublikasikan 14 Agustus 2026.
**DOI:** https://doi.org/10.1007/s10462-026-11640-4
**Status:** Halaman artikel Springer Open Access dan abstrak telah dibaca. PDF penuh belum berhasil diambil melalui alat yang tersedia pada sesi ini. Halaman penerbit menyebut versi yang tersedia merupakan accepted research version yang dapat mengalami penyuntingan sebelum diganti dengan Version of Record.

### Informasi yang didukung abstrak dan metadata penerbit
- Survey mencakup RL, integrasi deep learning menjadi DRL, dan model-based planning.
- Abstrak menyatakan cakupan algoritma dari metode tabular klasik hingga DRL.
- Aspek yang ditinjau meliputi scalability, sample efficiency, applicability, convergence, stability, dan exploration-exploitation trade-off.
- Kata kunci mencakup model-free, model-based, actor-critic, Q-learning, DQN, TD3, PPO, dan TRPO.
- Domain aplikasi yang disebut meliputi robotics, autonomous systems, intelligent transportation, energy management, dan financial modeling.

### Relevansi dan batas penggunaan
Artikel berpotensi mendukung diskusi umum pemilihan algoritma RL dan perbedaan model-free/model-based planning. Namun, rekomendasi pemilihan PPO, detail perbandingan algoritma, serta klaim teknis tiap domain belum dapat diatribusikan kepada penulis sebelum PDF lengkap dibaca.

## E. Sintesis tahap 9
1. Wang et al. menyediakan kerangka klasifikasi DRL dan uraian PPO sebagai policy-based method dengan clipped objective. Ini mendukung teori PPO, tetapi tidak membuktikan superioritas PPO pada evakuasi.
2. Faisal et al. memberi contoh empiris GAT pada klasifikasi laporan bencana. Perbandingan GAT-GCN relevan untuk konsep attention, tetapi konstruksi graf dan domain klasifikasinya berbeda dari graf gedung.
3. Ning dan Xie tetap berstatus sebagian; artikel MARL tidak boleh dipakai untuk menyimpulkan bahwa Tugas Akhir harus multi-agent.
4. Ghasemi et al. tetap berstatus sebagian; abstrak tidak cukup untuk mengambil rincian rekomendasi algoritma.
5. Untuk penelitian ini, bukti yang paling langsung tetap berasal dari studi evakuasi gedung, sedangkan sumber DRL/GAT lintas domain digunakan untuk landasan konsep dan justifikasi metode secara terbatas.

## F. Status pembacaan setelah tahap 9
Dari 30 publikasi yang terinventarisasi:
- Dibaca penuh/isi utama: 28 publikasi.
- Dibaca sebagian: 2 publikasi (Ning & Xie 2024; Ghasemi et al. 2026).
- Belum dibaca sama sekali: 0 publikasi.

**Catatan:** dua artikel yang masih sebagian telah diperiksa pada tingkat abstrak dan metadata. Keduanya belum boleh disebut selesai dibaca penuh.

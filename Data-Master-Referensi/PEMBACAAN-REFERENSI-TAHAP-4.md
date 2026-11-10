# Catatan Pembacaan Referensi — Tahap 4

**Topik Tugas Akhir:** Optimasi Rute Evakuasi Dinamis pada Lingkungan Gedung Kampus Menggunakan ST-HGAT dan PPO.

**Tanggal pemeriksaan:** 10 November 2026

## Cakupan dan status pembacaan

Tahap ini mencakup referensi dalam folder:
- `2.6-Reinforcement-Learning/`
- `2.7-Proximal-Policy-Optimization/`
- `2.8-Graph-Reinforcement-Learning/`

Lima publikasi ditelaah dari naskah lengkap atau preprint lengkap: Vidyasagar (2023), Darmawan et al. (2025), Machmudi et al. (2025), Darvariu et al. (2024), dan Nie et al. (2023). Dua publikasi ditelaah sebagian: Wang et al. (2024) melalui metadata/abstrak penerbit karena naskah lengkap tidak tersedia pada akses yang diperiksa; Gao et al. (2022) melalui abstrak, metode, hasil, dan tabel/teks lengkap yang terindeks pada halaman penerbit, tetapi bukan PDF lengkap yang dapat diperiksa secara utuh. Status ini sengaja dibedakan agar tidak mengklaim pembacaan penuh ketika akses dokumen terbatas.

## A. Publikasi yang ditelaah

### R-20 — Vidyasagar (2023)

**Judul:** A Tutorial Introduction to Reinforcement Learning  
**Publikasi:** *SICE Journal of Control, Measurement, and System Integration*, Vol. 16, No. 1, hlm. 172–191 (2023).  
**DOI:** https://doi.org/10.1080/18824889.2023.2196033  
**Lokasi repository:** `2.6-Reinforcement-Learning/`  
**Status:** Dibaca dari PDF lengkap (20 halaman).

**Tujuan dan ruang lingkup**
Artikel memberikan pengantar/survei singkat reinforcement learning dengan stochastic approximation sebagai tema pemersatu. Cakupannya meliputi Markov reward process, Markov decision process, Bellman optimality, value iteration, temporal-difference learning, dan Q-learning.

**Konsep utama**
- RL dibahas sebagai pengambilan keputusan pada model yang tidak diketahui secara pasti, ketika tindakan saat ini dapat mengubah perilaku sistem di masa depan.
- Pada formulasi MDP, agent mengamati state (X_t), memilih action (U_t), menerima reward, dan sistem berpindah ke state berikutnya.
- Policy adalah aturan yang menentukan action berdasarkan state.
- Tujuan pembelajaran adalah menemukan policy yang memaksimalkan expected discounted cumulative reward.
- Discount factor (gamma) mengatur bobot reward masa depan dibanding reward saat ini.
- Penulis membedakan MDP yang state-nya dapat diamati langsung dari partially observable MDP (POMDP), ketika agent hanya memperoleh observation yang berhubungan dengan state. POMDP tidak dibahas lebih lanjut dalam tutorial ini.
- Markov reward process menjadi dasar sebelum MDP karena state memiliki reward dan dinamika transisi.
- Bellman equation dan value iteration digunakan untuk menentukan value optimal ketika dinamika model diketahui.
- Ketika dinamika tidak diketahui, temporal-difference learning dan Q-learning dapat memperbarui estimasi dari pengalaman/transisi yang diamati.
- Artikel menghubungkan konvergensi TD dan Q-learning dengan stochastic approximation serta kondisi step size tertentu.

**Relevansi untuk penelitian ini**
- Menjadi sumber dasar untuk menjelaskan konsep RL, MDP, state, action, reward, policy, return, dan discount factor pada subbab 2.6.
- Dapat membantu menyusun formulasi masalah evakuasi sebagai proses keputusan berurutan.
- Dapat digunakan untuk membedakan model-based planning dengan RL ketika dinamika lingkungan tidak diketahui secara lengkap.
- Artikel ini bukan sumber PPO atau deep RL secara spesifik; jangan menggunakannya untuk menjelaskan clipping objective, actor-critic PPO, atau GAE.

**Catatan kritis**
Penulis menekankan asumsi state dapat diamati langsung pada pembahasan MDP yang digunakan. Jika penelitian menggunakan state simulasi yang lengkap, asumsi ini mungkin dapat dipenuhi oleh simulator; namun itu perlu ditetapkan pada rancangan penelitian, bukan diasumsikan dari sumber.

### R-21 — Wang et al. (2024)

**Judul:** Deep Reinforcement Learning: A Survey  
**Publikasi:** *IEEE Transactions on Neural Networks and Learning Systems*, Vol. 35, No. 4, hlm. 5064–5078 (April 2024; first published online 28 September 2022).  
**DOI:** https://doi.org/10.1109/TNNLS.2022.3207346  
**Lokasi repository:** `2.6-Reinforcement-Learning/`  
**Status:** Dibaca sebagian (metadata dan abstrak penerbit; PDF lengkap tidak tersedia pada akses yang diperiksa).

**Isi yang didukung oleh abstrak penerbit**
- DRL menggabungkan kemampuan deep learning untuk merepresentasikan fitur dengan kemampuan RL untuk pengambilan keputusan.
- DRL digunakan untuk tugas yang membutuhkan pemrosesan input berdimensi tinggi dan keputusan optimal atau mendekati optimal.
- Survei mencakup teori dasar, algoritma utama, dan domain aplikasi DRL.
- Keluarga metode yang disebutkan meliputi value-based DRL, policy-based DRL, dan maximum-entropy-based DRL.
- Penulis juga membahas hierarchical RL, multi-agent RL, imitation learning, serta tantangan seperti keterbatasan sampel dan sparse reward.

**Relevansi untuk penelitian ini**
- Dapat menjadi referensi pendukung pengantar DRL dan pengelompokan algoritma value-based/policy-based.
- Membantu menempatkan PPO sebagai bagian dari keluarga policy-based/policy-gradient DRL setelah bagian ini dibaca secara lengkap dari sumber primer yang sesuai.
- Karena naskah lengkap belum diperiksa, catatan ini tidak mengklaim detail isi bab, persamaan, atau hasil komparasi yang tidak muncul pada abstrak.

**Catatan**
Untuk teori PPO yang rinci, abstrak survei ini belum cukup. Perlu naskah lengkap atau sumber primer PPO.

### R-22 — Darmawan et al. (2025)

**Judul:** Optimalisasi Model Bahasa dan Sistem Ekonomi Berbasis Teks dengan Proximal Policy Optimization  
**Publikasi:** *Jurnal Bumigora Information Technology (BITe)*, Vol. 7, No. 1, hlm. 71–82 (Juni 2025).  
**DOI:** https://doi.org/10.30812/bite.v7i1.5222  
**Lokasi repository:** `2.7-Proximal-Policy-Optimization/`  
**Status:** Dibaca dari PDF lengkap (12 halaman).

**Tujuan dan metode**
Penelitian mengevaluasi PPO melalui dua studi kasus yang berjalan secara terpisah:
1. Penyelarasan model bahasa dengan preferensi manusia melalui pairwise comparison.
2. Pengambilan keputusan harga dinamis berdasarkan ulasan pelanggan dan indikator ekonomi.

**Komponen PPO yang dijelaskan**
- Penulis menyajikan clipped policy objective untuk membatasi perubahan probabilitas policy baru terhadap policy lama.
- Advantage dihitung menggunakan Generalized Advantage Estimation (GAE).
- Parameter yang disebutkan pada implementasi meliputi learning rate 3e-4, clip range 0,2, entropy coefficient 0,01, dan discount factor 0,99.
- Reward untuk kasus LLM didasarkan pada preferensi antara dua keluaran; reward kasus ekonomi mempertimbangkan indikator seperti laba, volume penjualan, dan kepuasan pelanggan.
- Artikel membahas validasi silang dan ablation terhadap reward, clipping, dan eksplorasi.

**Hasil yang dilaporkan**
- Pada kasus LLM, tabel hasil menunjukkan PPO pairwise memperoleh alignment score 0,86, BLEU 29,2, dan human-likeness 0,79; lebih tinggi daripada supervised fine-tuning dan RLHF yang dibandingkan.
- Pada kasus harga dinamis, PPO memperoleh cumulative reward 70.540, total revenue 203.800, dan MAE harga 8,5; dibandingkan supervised learning, DDPG, dan A3C.
- Ablation menunjukkan penghapusan entropy bonus, clipping objective, atau reward sentimen menurunkan cumulative reward pada kasus harga.

**Relevansi untuk penelitian ini**
- Berguna sebagai contoh penerapan PPO pada dua masalah pengambilan keputusan dengan reward yang ditentukan sesuai tujuan domain.
- Persamaan clipped objective dan GAE dapat menjadi pengantar, tetapi sebaiknya teori formal PPO tetap merujuk sumber primer algoritmanya.
- Mendukung pemahaman bahwa desain reward dan komponen clipping/eksplorasi dapat memengaruhi proses pembelajaran.
- Domain LLM dan harga dinamis tidak sama dengan evakuasi; hasil metrik alignment/BLEU/revenue tidak dapat dijadikan bukti performa PPO pada rute evakuasi.

**Catatan kritis**
Artikel menggabungkan dua studi kasus yang sangat berbeda. Saat mengutip hasilnya, jelaskan konteks tiap kasus. Jangan menyimpulkan bahwa angka kinerja dari kedua kasus tersebut berlaku untuk domain evakuasi.

### R-23 — Machmudi, Putra, dan Naim (2025)

**Judul:** Proximal Policy Optimization for Adaptive Resource Allocation in Mobile OS Kernels: Enhancing Multitasking Efficiency  
**Publikasi:** *Jurnal Teknik Informatika (JUTIF)*, Vol. 6, No. 6, hlm. 5621–5631 (Desember 2025).  
**DOI:** https://doi.org/10.52436/1.jutif.2025.6.6.5448  
**Lokasi repository:** `2.7-Proximal-Policy-Optimization/`  
**Status:** Dibaca dari PDF lengkap (11 halaman).

**Tujuan dan formulasi**
Penelitian menerapkan PPO untuk alokasi sumber daya pada kernel sistem operasi mobile. Masalah diformulasikan sebagai discrete MDP:
- State memuat metrik CPU, memori, karakteristik workload, dan metrik performa.
- Action mencakup pemindahan task antar-core, penyesuaian frekuensi CPU, dan pengaturan cgroup.
- Reward menyeimbangkan peningkatan performa dengan biaya energi.
- Arsitektur PPO menggunakan actor untuk menghasilkan distribusi probabilitas action dan critic untuk memperkirakan value state.
- Penulis menggunakan pendekatan actor-critic dan menyebut strategi eksplorasi epsilon-greedy.
- Pengujian dilakukan pada lingkungan simulasi yang merepresentasikan Android 14 AOSP dengan arsitektur big.LITTLE, tiga skenario multitasking, dan 20.000 episode pelatihan.

**Hasil yang dilaporkan**
- Abstrak melaporkan penurunan average task latency sebesar 18%, peningkatan system responsiveness 25%, dan penurunan konsumsi daya CPU 12% dibanding scheduler baseline.
- Tabel hasil latency melaporkan rata-rata pengurangan 21,6% terhadap default scheduler.
- Tabel jank frames melaporkan pengurangan 47,7% terhadap default scheduler.
- Ablation menunjukkan kombinasi PPO penuh menghasilkan pengurangan latency 21,6% dan peningkatan efisiensi daya 12,1% pada skenario yang diuji.
- Penulis menyatakan bahwa pelatihan dan validasi dilakukan dalam simulasi; biaya komputasi simulasi sekitar lima kali lebih besar daripada eksekusi real-time, dan validasi Hardware-in-the-Loop direncanakan untuk penelitian berikutnya.

**Relevansi untuk penelitian ini**
- Menjadi contoh formulasi MDP untuk masalah alokasi sumber daya dinamis.
- Menjelaskan pemisahan actor dan critic dalam implementasi PPO.
- Menunjukkan bagaimana reward dapat menggabungkan dua tujuan yang perlu diseimbangkan.
- Mendukung pembahasan bahwa evaluasi PPO perlu membandingkan policy dengan baseline dan melakukan ablation.
- Bukan studi graf atau evakuasi; hasilnya tidak dapat langsung digeneralisasi ke sistem rute evakuasi.

**Catatan kritis**
Ada ketidakkonsistenan angka dalam artikel: abstrak dan kesimpulan menyebut penurunan latency 18%, sedangkan Tabel 2 dan bagian analisis menyebut 21,6%. Abstrak/kesimpulan menyebut peningkatan responsiveness 25%, sedangkan tabel jank frames melaporkan pengurangan 47,7%. Karena itu, angka tersebut tidak boleh dikutip tanpa menjelaskan perbedaan metrik dan bagian sumber. Selain itu, penulis sendiri menyatakan evaluasi masih berbasis simulasi dan membutuhkan validasi lebih lanjut pada perangkat fisik.

### R-24 — Darvariu, Hailes, dan Musolesi (2024)

**Judul:** Graph Reinforcement Learning for Combinatorial Optimization: A Survey and Unifying Perspective  
**Publikasi:** *Transactions on Machine Learning Research* (Agustus 2024), 46 halaman.  
**DOI:** https://doi.org/10.48550/arXiv.2404.06492 (preprint arXiv; publikasi TMLR 2024).  
**Lokasi repository:** `2.8-Graph-Reinforcement-Learning/`  
**Status:** Dibaca dari naskah lengkap (46 halaman).

**Definisi dan kerangka GRL**
- Artikel menyatukan pendekatan RL untuk masalah keputusan kombinatorial pada graf dalam kerangka Graph Reinforcement Learning.
- Graf merepresentasikan entitas sebagai node dan relasi sebagai edge; node dan edge dapat memiliki atribut statis maupun dinamis.
- RL memformulasikan masalah sebagai MDP, ketika agent membangun solusi secara bertahap dan menerima reward sesuai kualitas keputusan.
- Penulis membagi GRL menjadi dua kategori utama:
  1. **Graph structure optimization:** agent membangun atau memodifikasi struktur graf.
  2. **Graph process optimization:** agent mengoptimalkan proses yang berjalan di atas struktur graf tetap.

**Kategori yang paling dekat dengan penelitian ini**
Graph process optimization mengasumsikan struktur graf tetap, sedangkan agent memilih tindakan untuk mengoptimalkan proses di dalamnya. Contoh yang disebutkan adalah:
- Routing lalu lintas pada jaringan.
- Pengendalian proses penyebaran.
- Network games.
- Search dan navigation, dengan action memilih node berikutnya yang akan dikunjungi.

**Contoh integrasi GNN dan PPO**
- Pada routing jaringan, Almasan et al. menggunakan MPNN untuk merepresentasikan state dan PPO untuk mempelajari policy. Agent memilih node perantara bagi flow; reward menggunakan maximum link utilization. Hasil yang dirangkum penulis lebih baik daripada shortest-path routing standar dan sebuah heuristic, tetapi masih di bawah simulated annealing pada kualitas tertentu; runtime-nya lebih cepat.
- Hope dan Yoneki menggunakan Graph Network dan PPO untuk mempelajari edge weights bagi routing; hasil representasi GNN lebih baik daripada MLP pada satu topologi, tetapi perbandingan dengan shortest-path menunjukkan hasil yang beragam.
- Artikel juga menyebut Graph Convolutional Policy Network (GCPN), yang menggunakan GCN untuk representasi state dan PPO untuk policy pada optimasi molekul. Ini merupakan optimasi struktur graf, bukan navigasi gedung.

**Tantangan yang dibahas**
- Formulasi MDP: menentukan state, action, dan dinamika yang tepat memengaruhi efektivitas pembelajaran.
- Reward design: reward dapat berupa satu tujuan atau gabungan beberapa tujuan; reward yang terlalu jarang dapat menimbulkan masalah sparse reward dan credit assignment.
- Pilihan tingkat granularitas action: action terlalu detail dapat memperbesar ruang aksi, sedangkan action terlalu abstrak dapat mengurangi ekspresivitas.
- Skalabilitas, generalisasi, engineering overhead, dan interpretabilitas.
- Penulis menekankan bahwa tidak ada satu pendekatan yang unggul untuk semua masalah.

**Relevansi untuk penelitian ini**
- Ini adalah referensi GRL paling kuat di repository untuk mendukung formulasi masalah sebagai optimasi proses pada graf yang topologinya tetap.
- Memberikan contoh langsung penggunaan PPO bersama MPNN/Graph Network pada routing jaringan.
- Dapat menjadi landasan konseptual untuk menghubungkan ST-HGAT sebagai representasi keadaan graf dengan PPO sebagai pembelajar policy, tetapi arsitektur spesifik penelitian tetap harus dijelaskan sendiri.
- Menegaskan bahwa RL tidak otomatis lebih baik daripada shortest path atau metaheuristic; pembandingan baseline menjadi penting.
- Tidak membuktikan efektivitas pada evakuasi gedung karena contoh routing yang dibahas berfokus pada jaringan komunikasi.

### R-25 — Nie, Chen, dan Wang (2023)

**Judul:** Reinforcement Learning on Graphs: A Survey  
**Publikasi:** *IEEE Transactions on Emerging Topics in Computational Intelligence*, Vol. 7, No. 4, hlm. 1065–1082 (2023).  
**DOI:** https://doi.org/10.1109/TETCI.2022.3222545  
**Lokasi repository:** `2.8-Graph-Reinforcement-Learning/`  
**Status:** Dibaca dari naskah lengkap preprint arXiv versi 4 (22 halaman, 15 Januari 2023), dengan metadata dicocokkan ke versi jurnal.

**Definisi dan klasifikasi**
- Survey menggabungkan RL dan graph mining sebagai Graph Reinforcement Learning (GRL).
- Penulis mengelompokkan integrasi RL dan graf menjadi dua arah:
  1. Menyelesaikan masalah RL dengan memanfaatkan struktur graf.
  2. Menyelesaikan tugas graph mining menggunakan metode RL.
- GNN digunakan untuk memperoleh embedding node/graf melalui agregasi fitur node target dan tetangganya.
- RL diformulasikan sebagai MDP yang mencakup state, action, transition, reward, dan discount factor.
- Survey meninjau beragam domain seperti transportasi, rekomendasi, knowledge graph, dan optimasi jaringan.

**Tantangan**
- Menentukan environment/state space secara tepat.
- Merancang action space dan reward function yang sesuai dengan tugas graf.
- Struktur graf bersifat diskret, berdimensi tinggi, dan dapat berukuran besar.
- Skala data yang meningkat dapat membuat proses pembelajaran tidak efisien.
- Penggabungan pengetahuan domain dan data heterogen menambah kompleksitas desain.

**Contoh yang relevan**
- Survey merangkum contoh path planning pada spatio-temporal graph yang menggunakan PPO untuk melatih policy state-to-action.
- Contoh tersebut merupakan bukti bahwa PPO pernah digunakan pada perencanaan lintasan berbasis graf, tetapi bukan bukti langsung untuk evakuasi kampus.
- Tabel aplikasi juga menguraikan state, action, reward, termination, algoritma RL, dan metrik untuk sejumlah studi, yang berguna sebagai referensi ketika menyusun formulasi eksperimen.

**Relevansi untuk penelitian ini**
- Berguna sebagai pengantar konsep GRL dan klasifikasi hubungan GNN dengan RL.
- Mendukung kebutuhan merancang state, action, reward, dan termination secara khusus untuk masalah graf.
- Contoh PPO untuk path planning memberi pembanding konseptual yang lebih dekat dengan rute evakuasi dibanding aplikasi PPO pada LLM atau resource scheduling.
- Survey ini mencakup banyak pendekatan graf mining; jangan menganggap semua contoh GRL menggunakan PPO atau GNN yang sama.

### R-26 — Gao et al. (2022)

**Judul:** Multi-Agent Decision-Making Modes in Uncertain Interactive Traffic Scenarios via Graph Convolution-Based Deep Reinforcement Learning  
**Publikasi:** *Sensors*, Vol. 22, No. 12, Article 4586 (17 Juni 2022).  
**DOI:** https://doi.org/10.3390/s22124586  
**Lokasi repository:** `2.8-Graph-Reinforcement-Learning/`  
**Status:** Dibaca sebagian; abstrak, metode, hasil, dan bagian kesimpulan/tabel yang tersedia pada halaman penerbit ditelaah, tetapi PDF lengkap tidak berhasil diakses secara utuh.

**Tujuan dan metode yang teridentifikasi**
- Penelitian memodelkan interaksi kendaraan pada skenario jalan tol dengan graf.
- GCN digunakan untuk mengekstraksi fitur struktur graf.
- GCN digabungkan dengan deep Q-learning dan multi-step double deep Q-learning, membentuk GQN dan MDGQN.
- Penulis merancang reward function matrix yang memuat bobot untuk task completion, traffic efficiency, comfort, dan safety.
- Empat mode keputusan dibentuk dari kombinasi perilaku aggressive/conservative dan incentive/punishment: AGGI, AGGP, CONI, dan CONP.
- Evaluasi mencakup efisiensi, keselamatan, kenyamanan, dan penyelesaian tugas.

**Hasil utama yang tersedia**
- MDGQN secara umum menunjukkan kinerja lebih baik daripada GQN pada skenario lalu lintas yang diuji.
- Mode aggressive cenderung menghasilkan kecepatan/efisiensi dan tingkat kedatangan lebih tinggi, tetapi juga dapat meningkatkan collision rate dan emergency braking.
- Mode conservative-punishment menunjukkan collision rate dan emergency braking lebih rendah, tetapi efisiensi serta tingkat kedatangan lebih rendah.
- Penulis melaporkan reward matrix dapat menghasilkan mode keputusan yang berbeda sesuai bobot tujuan.

**Relevansi untuk penelitian ini**
- Memberikan contoh bahwa reward multi-tujuan perlu dirancang sesuai prioritas keselamatan, efisiensi, dan kenyamanan.
- Mendukung perlunya mengevaluasi trade-off, bukan hanya satu metrik.
- GCN + Q-learning pada interaksi kendaraan merupakan contoh GRL/graph-based DRL, tetapi bukan PPO.
- Konteks lalu lintas kendaraan dan multi-agent berbeda dari rute evakuasi penghuni gedung; hasil numeriknya tidak dapat dipindahkan langsung.

**Catatan kritis**
Karena PDF lengkap belum dapat ditelaah, gunakan catatan ini hanya untuk temuan yang tersedia pada abstrak, metode, tabel, dan kesimpulan yang terindeks. Jangan mengklaim telah memeriksa seluruh detail implementasi atau semua asumsi eksperimen.

## B. Sintesis per subbab

### 2.6 Reinforcement Learning
- Vidyasagar (2023) merupakan sumber utama untuk konsep dasar RL, MDP, reward, policy, discount factor, Bellman, TD, dan Q-learning.
- Wang et al. (2024) dapat menjadi sumber pendukung DRL, tetapi perlu pembacaan PDF lengkap sebelum digunakan untuk klaim rinci.
- RL mempelajari keputusan melalui interaksi agent-environment; formulasi MDP mengharuskan definisi state, action, transition, reward, dan discount factor.
- Untuk penelitian ini, state harus memuat informasi yang cukup untuk keputusan rute dinamis; action perlu merepresentasikan keputusan rute yang memang dapat dilakukan sistem; reward perlu mencerminkan tujuan dan batasan penelitian. Detailnya ditetapkan pada BAB III, bukan ditiru mentah dari studi lain.

### 2.7 Proximal Policy Optimization
- Darmawan et al. menjelaskan clipped objective dan GAE serta contoh penerapan PPO pada dua domain berbeda.
- Machmudi et al. menunjukkan contoh actor-critic PPO untuk keputusan resource allocation dengan state, action, dan reward domain-spesifik.
- Kedua paper adalah studi aplikasi, bukan sumber primer yang memperkenalkan PPO.
- Untuk teori PPO yang kokoh, folder 2.7 masih perlu dilengkapi dengan paper primer PPO (Schulman et al., 2017, *Proximal Policy Optimization Algorithms*) atau referensi textbook/teknis yang menjelaskan derivasi clipped surrogate objective.
- Angka hasil aplikasi PPO dari LLM dan resource allocation tidak dapat dijadikan bukti kinerja PPO pada evakuasi.

### 2.8 Graph Reinforcement Learning
- Nie et al. dan Darvariu et al. menyediakan landasan konseptual GRL dari dua perspektif yang saling melengkapi.
- Darvariu et al. sangat relevan untuk penelitian dengan graf yang topologinya relatif tetap dan keputusan yang mengoptimalkan proses pada graf tersebut.
- Contoh routing jaringan menunjukkan bahwa PPO dapat dipasangkan dengan MPNN/Graph Network untuk mengambil keputusan routing; hasilnya tetap perlu dibandingkan dengan shortest path dan metode lain.
- Gao et al. menjadi contoh tambahan tentang pemodelan interaksi berbasis graf dan reward multi-tujuan, tetapi menggunakan Q-learning, bukan PPO.

## C. Implikasi bagi rancangan penelitian

Berikut interpretasi desain yang diturunkan dari kebutuhan penelitian dan didukung secara konseptual oleh sumber-sumber di atas, bukan hasil eksperimen yang dilakukan oleh artikel-artikel tersebut:

1. **Graf lingkungan:** topologi gedung dapat ditetapkan dari denah dan diperlakukan sebagai struktur dasar yang relatif tetap selama satu skenario.
2. **Representasi state:** kondisi dinamis seperti okupansi, kepadatan, antrean, dan ketersediaan akses dapat diperbarui sepanjang simulasi jika variabel tersebut memang didefinisikan dalam model.
3. **Representasi graf:** ST-HGAT menghasilkan representasi spasio-temporal dari node/relasi yang relevan; bentuk embedding dan fitur harus dijelaskan pada BAB III.
4. **Keputusan:** PPO mempelajari policy untuk memilih action pada graf, misalnya pemilihan node/rute berikutnya atau alternatif rute yang valid. Bentuk action final harus disesuaikan dengan desain sistem.
5. **Keselamatan:** reward tidak boleh menjadi satu-satunya mekanisme keselamatan jika ada kondisi yang harus dipenuhi secara mutlak. Batasan keselamatan perlu ditangani eksplisit dalam environment/action mask/aturan transisi atau formulasi constraint yang dipilih.
6. **Evaluasi:** perlu dibandingkan dengan baseline seperti shortest path (misalnya Dijkstra) dan metode lain yang relevan, serta mengevaluasi waktu evakuasi, kepadatan/antrean, keselamatan, dan keberhasilan mencapai titik aman sesuai definisi eksperimen.

## D. Catatan kualitas dan metadata

1. Wang et al. (2024): metadata jurnal dan DOI sesuai; PDF lengkap belum ditelaah.
2. Nie et al. (2023): versi jurnal adalah *IEEE Transactions on Emerging Topics in Computational Intelligence*, Vol. 7, No. 4, hlm. 1065–1082, DOI 10.1109/TETCI.2022.3222545. Naskah lengkap yang ditelaah adalah preprint arXiv versi 4.
3. Darvariu et al. (2024): versi TMLR Agustus 2024, 46 halaman; DOI arXiv pada BibTeX bukan DOI jurnal TMLR, sehingga sebaiknya metadata referensi diperiksa kembali dan gunakan URL/metadata TMLR resmi pada daftar pustaka.
4. Machmudi et al. (2025): terdapat perbedaan angka latency dan responsiveness antara abstrak/kesimpulan dan tabel hasil. Kutip angka dengan rujukan tabel yang spesifik, atau hindari angka jika tidak diperlukan.
5. Gao et al. (2022): pembacaan PDF lengkap belum selesai; status tidak boleh diubah menjadi dibaca penuh.

## E. Status pembacaan setelah tahap 4

- Total PDF terinventarisasi di repository: 30.
- Publikasi yang telah dibaca penuh/isi utama pada tahap 1–4: 15.
- Publikasi yang dibaca sebagian: 3 (Rizian et al. 2026; Wang et al. 2024; Gao et al. 2022).
- Publikasi yang belum dibaca: 12.
- Tahap 4 mencakup 2.6 Reinforcement Learning, 2.7 PPO, dan 2.8 Graph Reinforcement Learning.

## F. Referensi tahap 4

- M. Vidyasagar, “A tutorial introduction to reinforcement learning,” *SICE Journal of Control, Measurement, and System Integration*, vol. 16, no. 1, pp. 172–191, 2023, doi: 10.1080/18824889.2023.2196033.
- X. Wang, S. Wang, X. Liang, D. Zhao, J. Huang, X. Xu, B. Dai, and Q. Miao, “Deep reinforcement learning: A survey,” *IEEE Transactions on Neural Networks and Learning Systems*, vol. 35, no. 4, pp. 5064–5078, 2024, doi: 10.1109/TNNLS.2022.3207346.
- I. Darmawan, N. Ramadhani, M. N. Arifin, Ubaidi, N. P. Dewi, and M. Innuddin, “Optimalisasi model bahasa dan sistem ekonomi berbasis teks dengan Proximal Policy Optimization,” *Jurnal Bumigora Information Technology (BITe)*, vol. 7, no. 1, pp. 71–82, 2025, doi: 10.30812/bite.v7i1.5222.
- M. A. Machmudi, Y. W. S. Putra, and A. G. Naim, “Proximal Policy Optimization for adaptive resource allocation in mobile OS kernels: Enhancing multitasking efficiency,” *Jurnal Teknik Informatika (JUTIF)*, vol. 6, no. 6, pp. 5621–5631, 2025, doi: 10.52436/1.jutif.2025.6.6.5448.
- V.-A. Darvariu, S. Hailes, and M. Musolesi, “Graph reinforcement learning for combinatorial optimization: A survey and unifying perspective,” *Transactions on Machine Learning Research*, 2024.
- M. Nie, D. Chen, and D. Wang, “Reinforcement learning on graphs: A survey,” *IEEE Transactions on Emerging Topics in Computational Intelligence*, vol. 7, no. 4, pp. 1065–1082, 2023, doi: 10.1109/TETCI.2022.3222545.
- X. Gao, X. Li, Q. Liu, Z. Li, F. Yang, and T. Luan, “Multi-agent decision-making modes in uncertain interactive traffic scenarios via graph convolution-based deep reinforcement learning,” *Sensors*, vol. 22, no. 12, art. 4586, 2022, doi: 10.3390/s22124586.

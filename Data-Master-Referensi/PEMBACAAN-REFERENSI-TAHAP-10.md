# Catatan Pembacaan Referensi — Tahap 10

**Topik Tugas Akhir:** Optimasi Rute Evakuasi Dinamis pada Lingkungan Gedung Kampus Menggunakan ST-HGAT dan PPO.

**Tanggal:** 10 November 2026

## Cakupan dan metode akses

Tahap ini menuntaskan pembacaan isi artikel Ning dan Xie (2024), serta mencoba kembali mengakses artikel Ghasemi et al. (2026).

- Ning dan Xie (2024): isi artikel tersedia dalam bentuk teks lengkap 19 halaman pada salinan daring yang memuat isi artikel dan struktur halaman jurnal. Metadata diverifikasi silang dengan laman penerbit SciOpen dan ScienceDirect. PDF yang ada di repository tetap belum diekstrak langsung; pembacaan penuh merujuk pada teks lengkap salinan daring tersebut.
- Ghasemi et al. (2026): laman resmi Springer Open Access dan abstrak serta metadata artikel berhasil diverifikasi, tetapi PDF/teks isi lengkap tidak berhasil diekstrak. Status tetap dibaca sebagian. Tidak ada rincian isi bab, algoritma, atau perbandingan yang diasumsikan dari abstrak.

## A. R-20 — Ning dan Xie (2024)

**Judul:** “A Survey on Multi-Agent Reinforcement Learning and Its Application.”
**Publikasi:** *Journal of Automation and Intelligence*, Vol. 3, No. 2, Juni 2024, hlm. 73–91.
**DOI:** https://doi.org/10.1016/j.jai.2024.02.003
**Status:** Dibaca penuh berdasarkan teks lengkap artikel 19 halaman yang tersedia daring; metadata dicocokkan dengan laman penerbit.

### Tujuan dan kontribusi

Artikel ini merupakan survey yang meninjau perkembangan MARL, model stochastic games, metode pembelajaran, bentuk tugas multi-agen, tantangan implementasi, domain aplikasi, benchmark, dan arah penelitian ke depan. Penulis menyoroti bahwa MARL berbeda dari RL single-agent karena tindakan satu agen dapat memengaruhi lingkungan dan reward agen lain, sehingga interaksi antarpelaku perlu dimodelkan.

### 1. Landasan stochastic games dan observabilitas

- MDP dijelaskan sebagai model interaksi agen-lingkungan melalui state, action, transition probability, reward, dan discount factor.
- Ketika terdapat banyak agen yang tindakannya saling memengaruhi, MDP single-agent tidak cukup untuk merepresentasikan interaksi tersebut; penulis menggunakan stochastic games/Markov games sebagai perluasan.
- Dalam Markov game, state bersifat bersama, action merupakan gabungan action setiap agen, dan reward dapat berbeda untuk tiap agen.
- POMDP digunakan ketika state lingkungan tidak sepenuhnya dapat diamati; agen menerima observation, bukan state sebenarnya.
- Untuk banyak agen dengan observasi terpisah, artikel membahas Dec-POMDP dan partially observable stochastic games. Perbedaan pentingnya adalah Dec-POMDP menekankan reward kolektif, sedangkan partially observable stochastic game dapat memodelkan reward individual yang berbeda.

### 2. Metode MARL

- Survey mengelompokkan metode menjadi value-based dan policy-based.
- Pada value-based MARL, Q-learning digunakan untuk memperkirakan nilai state-action; penulis membahas masalah kombinatorial dan pertumbuhan kompleksitas ketika jumlah agen meningkat.
- Pada policy-based MARL, tiap agen mempelajari policy parametrik. Pembahasan mencakup policy-gradient dan deterministic policy gradient.
- Actor-critic dibahas sebagai pendekatan yang relevan untuk pembelajaran multi-agen.
- Untuk tugas kooperatif, artikel menjelaskan value decomposition, termasuk VDN, QMIX, dan QTRAN, untuk menghubungkan nilai individual dengan nilai tim.

### 3. Paradigma pelatihan dan eksekusi

Artikel membedakan tiga paradigma:
- **CTCE (Centralized Training and Centralized Execution):** kebijakan terpusat digunakan untuk menentukan aksi bersama.
- **CTDE (Centralized Training and Decentralized Execution):** informasi terpusat digunakan selama pelatihan, sedangkan saat eksekusi agen bertindak berdasarkan observasi lokal.
- **DTDE (Decentralized Training and Decentralized Execution):** agen melatih kebijakannya secara independen dan tidak bertukar informasi saat pelatihan.

Penulis menjelaskan CTDE sebagai paradigma yang banyak digunakan karena dapat memanfaatkan informasi tambahan saat training tanpa mengharuskan eksekusi terpusat. DTDE dapat membantu skalabilitas, tetapi interaksi antar-policy dapat menyebabkan non-stationarity.

### 4. Jenis tugas multi-agen

- **Kooperatif:** agen mengoptimalkan reward tim atau tujuan bersama.
- **Kompetitif:** agen mengoptimalkan reward masing-masing dan dapat berlawanan dengan kepentingan agen lain.
- **Campuran (cooperative-competitive/general-sum):** terdapat unsur kerja sama dan persaingan.

Klasifikasi ini bergantung pada struktur reward dan tujuan, bukan semata-mata jumlah agen.

### 5. Tantangan implementasi

Penulis mengidentifikasi beberapa tantangan utama:
1. **Scalability:** kompleksitas meningkat tajam seiring jumlah agen; strategi yang dibahas mencakup parameter sharing, transfer learning, mean-field, curriculum learning, dan self-play.
2. **Non-stationarity:** policy agen lain berubah selama pembelajaran sehingga dinamika yang dihadapi satu agen ikut berubah; replay data lama dapat menjadi kurang relevan.
3. **Partial observability:** tiap agen mungkin hanya memperoleh sebagian informasi; pendekatan yang dibahas termasuk CTDE, recurrent networks/memory, dan komunikasi.
4. **Credit assignment:** sulit menentukan kontribusi aksi tiap agen terhadap keberhasilan tim; VDN/QMIX/QTRAN dan pendekatan hierarkis dibahas sebagai solusi.
5. **Continuous action spaces:** menambah tantangan optimasi dan stabilitas policy.
6. **Communication:** perlu menentukan siapa berkomunikasi dengan siapa, kapan, dan informasi apa yang dikirim; artikel mengulas broadcasting, targeted, dan networked communication, termasuk mekanisme attention.
7. **Learning complexity:** tuning hyperparameter dan kebutuhan komputasi/sampel dapat menjadi hambatan praktis.

### 6. Domain aplikasi

Survey merangkum aplikasi MARL pada:
- mesin dan perangkat cerdas, termasuk UAV, kendaraan otonom, manajemen lalu lintas, energi, jaringan, pengolahan citra, chip dan biochip;
- teknik kimia, bioteknologi, dan kesehatan;
- masyarakat dan perilaku manusia, termasuk pengelolaan sumber daya, perdagangan, serta perilaku manusia dan kelompok.

Untuk topik evakuasi, bagian yang paling relevan adalah pembahasan pemodelan perilaku kelompok pedestrian. Artikel merujuk studi [205] yang menganalisis perilaku emergen kelompok pedestrian dengan MARL dan menyoroti skalabilitas serta robustness. Artikel juga menyebut MARL-Ped sebagai lingkungan virtual pedestrian untuk pemodelan perilaku pada tingkat interaksi lokal hingga perilaku strategis dan path planning. Namun, uraian tersebut merupakan ringkasan terhadap studi terdahulu, bukan eksperimen evakuasi gedung yang dilakukan oleh Ning dan Xie.

### 7. Benchmark dan lingkungan simulasi

Survey mencantumkan berbagai benchmark, di antaranya:
- Project Malmo, Hanabi, PyMARL/EPyMARL untuk tugas kooperatif;
- OpenSpiel, PettingZoo, StarCraft Multi-Agent Challenge untuk lingkungan permainan;
- RoboCup, MuJoCo multi-agent soccer, Multi-agent Particle Environment, dan gym-pybullet-drones untuk robot dan navigasi;
- SUMO, Ray, MACAD-Gym, CityFlow, Flow, Flatland, serta MARL-Ped untuk transportasi, lalu lintas, dan pedestrian;
- PowerGridworld dan PGSim untuk sistem tenaga;
- ABIDES dan TaxAI untuk simulasi ekonomi.

Kehadiran MARL-Ped relevan sebagai petunjuk bahwa pemodelan pedestrian telah menjadi salah satu domain MARL, tetapi paper ini tidak menyajikan detail implementasi MARL-Ped secara cukup untuk langsung mengadopsinya sebagai desain simulasi penelitian ini.

### 8. Arah penelitian dan kesimpulan penulis

Penulis menyoroti kebutuhan untuk memperkecil kesenjangan antara teori MARL dan implementasi praktis. Arah yang disebut meliputi heterogeneous MARL, physics-informed MARL, safe MARL, serta integrasi teori psikologi untuk membentuk perilaku agen yang lebih realistis. Artikel menekankan perlunya mempertimbangkan stabilitas pembelajaran, adaptasi pada kondisi tidak pasti, dan penerapan pada skenario dunia nyata.

### Relevansi untuk Tugas Akhir

- Dapat digunakan sebagai sumber konseptual untuk menjelaskan perbedaan RL single-agent dan MARL, stochastic games, observability, cooperative/competitive tasks, serta CTDE/DTDE.
- Dapat menjadi referensi pendukung bahwa MARL pernah diterapkan pada pemodelan pedestrian dan path planning, melalui studi yang dirangkum pada bagian aplikasi dan benchmark.
- Memberi daftar tantangan penting apabila suatu penelitian memilih banyak agen, khususnya scalability, non-stationarity, partial observability, credit assignment, komunikasi, dan computational burden.
- Tidak membuktikan bahwa sistem evakuasi ini harus menggunakan MARL. Penelitian tetap dapat memakai satu policy/decision-maker yang mengamati graf dan kondisi banyak penghuni; banyaknya penghuni yang disimulasikan tidak otomatis berarti masing-masing harus menjadi agen pembelajar.
- Tidak membuktikan PPO sebagai pilihan terbaik untuk evakuasi; pembahasan policy-gradient/actor-critic bersifat umum dan bukan eksperimen perbandingan PPO untuk evakuasi gedung.

### Catatan kritis

1. Artikel adalah survey, bukan studi eksperimen evakuasi baru.
2. Bagian pedestrian mengacu pada karya lain; klaim hasil atau detail algoritma studi [205] dan MARL-Ped perlu dilacak ke sumber primernya jika akan dibahas mendalam.
3. Artikel membahas MARL secara luas, sehingga tidak semua metode dan tantangannya relevan untuk arsitektur penelitian ini.
4. Versi teks lengkap dibaca dari salinan daring pihak ketiga; untuk kutipan final, gunakan PDF resmi repository/institusi dan verifikasi ulang halaman serta persamaan dari file asli.

**Bagian/halaman jurnal penting:** MDP, POMDP, stochastic games (hlm. 74–75); metode MARL dan paradigma training/execution (hlm. 76–77); cooperative/competitive tasks dan tantangan (hlm. 77–80); aplikasi (hlm. 80–83); benchmark dan pedestrian MARL (hlm. 83–85); future directions dan conclusion (hlm. 85–86). Rentang halaman artikel bibliografis adalah 73–91.

## B. R-24 — Ghasemi, Moosavi, dan Ebrahimi (2026)

**Judul:** “Reinforcement Learning and Model-based Planning in Practice: A Survey of Algorithmic Rationale and Domain Applications.”
**Publikasi:** *Artificial Intelligence Review*, 2026.
**DOI:** https://doi.org/10.1007/s10462-026-11640-4
**Tanggal publikasi:** 14 Agustus 2026.
**Status:** Dibaca sebagian; laman resmi Springer Open Access dan abstrak/metadata telah diperiksa, tetapi isi PDF lengkap belum berhasil diekstrak.

### Informasi yang dapat dipastikan dari laman penerbit

- Artikel merupakan survey mengenai RL, integrasinya dengan deep learning menjadi DRL, dan model-based planning.
- Abstrak menyatakan cakupan pembahasan dari algoritma tabular klasik hingga teknik DRL mutakhir.
- Aspek yang menjadi fokus evaluasi meliputi scalability, sample efficiency, dan applicability.
- Tantangan yang disebut dalam abstrak meliputi convergence, stability, dan exploration-exploitation trade-off.
- Domain aplikasi yang disebut adalah robotics, autonomous systems, intelligent transportation, energy management, dan financial modeling.
- Kata kunci penerbit mencakup model-free, model-based, actor-critic, Q-learning, DQN, TD3, PPO, dan TRPO.
- Springer menyatakan artikel tersedia sebagai Open Access dan versi yang ditampilkan merupakan accepted research version yang dapat mengalami penyuntingan sebelum digantikan Version of Record.

### Relevansi dan batas penggunaan

- Topik survey berpotensi relevan untuk pembahasan umum pemilihan algoritma RL, model-based planning, dan DRL.
- Namun, rincian taksonomi, definisi operasional, tabel perbandingan algoritma, kelebihan/kekurangan spesifik PPO, serta rekomendasi implementasi belum dapat diambil karena isi penuh belum dibaca.
- Jangan mengutip abstrak sebagai bukti bahwa PPO lebih baik atau lebih cocok untuk evakuasi.
- Status publikasi dan metadata dapat digunakan setelah dicocokkan dengan versi final penerbit; detail isi harus menunggu pembacaan PDF lengkap.

## C. Sintesis tahap 10

1. Ning dan Xie memberi landasan MARL yang lebih lengkap daripada abstrak: model stochastic games, perbedaan cooperative/competitive/mixed, metode value-based dan policy-based, serta paradigma CTCE/CTDE/DTDE.
2. Untuk penelitian evakuasi, bagian yang paling menarik adalah rujukan terhadap MARL untuk pedestrian groups dan lingkungan MARL-Ped. Namun, keduanya adalah studi yang dirujuk survey; sumber primer perlu dibaca sebelum mengadopsi detail atau mengklaim efektivitasnya.
3. Literatur MARL menegaskan bahwa pemodelan banyak penghuni tidak mengharuskan setiap penghuni menjadi agen RL. Keputusan jumlah agen pembelajar merupakan pilihan desain tersendiri.
4. Ghasemi et al. masih belum dapat dinyatakan selesai dibaca. Informasi yang tersedia hanya mendukung ruang lingkup survey dan aspek yang disebut pada abstrak/metadata.
5. Setelah tahap ini, 29 dari 30 publikasi telah dibaca penuh/isi utama dan satu publikasi masih dibaca sebagian.

## D. Status pembacaan setelah tahap 10

Dari 30 publikasi yang terinventarisasi:
- Dibaca penuh/isi utama: 29 publikasi.
- Dibaca sebagian: 1 publikasi (Ghasemi et al. 2026).
- Belum dibaca sama sekali: 0 publikasi.

**Catatan:** status penuh Ning dan Xie didasarkan pada teks lengkap artikel 19 halaman dari salinan daring, bukan hasil ekstraksi langsung dari PDF di GitHub. Untuk kutipan final, cocokkan halaman, persamaan, dan tabel dengan PDF resmi.

# Catatan Pembacaan Referensi — Tahap 11

**Topik Tugas Akhir:** Optimasi Rute Evakuasi Dinamis pada Lingkungan Gedung Kampus Menggunakan ST-HGAT dan PPO.

**Tanggal:** 10 November 2026

## Cakupan dan metode akses

Tahap ini menuntaskan pembacaan R-24, yaitu Ghasemi, Moosavi, dan Ebrahimi (2026). Teks lengkap artikel tersedia melalui dokumen yang dibagikan dalam percakapan dan telah ditelaah dari bagian pendahuluan sampai kesimpulan, termasuk taksonomi RL, pembahasan model-based planning, policy-gradient, PPO, actor-critic, tren, tantangan, dan aplikasi.

**Catatan versi:** dokumen menyatakan sebagai *accepted manuscript/article in press* yang belum melalui penyuntingan final. Karena itu, penomoran halaman final belum tersedia/ belum dapat dipastikan dari naskah ini. Gunakan DOI untuk identitas artikel dan verifikasi ulang pagination serta detail editorial ketika Version of Record tersedia.

## R-24 — Ghasemi, Moosavi, dan Ebrahimi (2026)

**Judul:** “Reinforcement Learning and Model-based Planning in Practice: A Survey of Algorithmic Rationale and Domain Applications.”  
**Publikasi:** *Artificial Intelligence Review*, 2026 (accepted manuscript/article in press).  
**DOI:** https://doi.org/10.1007/s10462-026-11640-4  
**Penulis:** Majid Ghasemi, Amir Hossein Moosavi, dan Dariush Ebrahimi.  
**Status:** Dibaca penuh berdasarkan teks lengkap accepted manuscript yang dibagikan.

### Tujuan dan kontribusi

Artikel merupakan survey yang mengulas RL, DRL, dan model-based planning. Cakupannya mencakup algoritma tabular klasik hingga DRL, dengan perhatian pada scalability, sample efficiency, applicability, convergence, stability, serta exploration-exploitation. Penulis meninjau aplikasi pada robotics, autonomous systems, intelligent transportation, energy management, finance, jaringan, dan domain lain.

Penulis menyatakan bahwa tujuan survey adalah membantu pemilihan algoritma berdasarkan karakteristik masalah dan pertimbangan praktis, bukan menetapkan satu algoritma sebagai pemenang universal.

### 1. Komponen RL dan MDP

Artikel menjelaskan komponen utama RL:
- **Agent** berinteraksi dengan environment.
- **State** merepresentasikan kondisi yang dipertimbangkan agen saat mengambil keputusan.
- **Action** merupakan keputusan/tindakan agen.
- **Reward** memberi sinyal numerik pada setiap langkah untuk mengarahkan perilaku.
- **Policy** memetakan state ke action.
- **Value function** memperkirakan reward jangka panjang dari state atau pasangan state-action.
- **Environment model** (opsional) memperkirakan dinamika lingkungan.

MDP ditulis sebagai tuple (S, A, P, R, γ), dengan S sebagai himpunan state, A sebagai himpunan action, P sebagai probabilitas transisi, R sebagai reward, dan γ sebagai discount factor. Artikel juga membahas return, state-value function, action-value function, Bellman equations, dan pembaruan Q-learning.

**Relevansi:** kerangka ini dapat menjadi dasar untuk merumuskan state, action, reward, transisi, dan tujuan kebijakan pada simulasi evakuasi. Definisi operasional setiap elemen tetap harus dirancang sesuai model penelitian, bukan disalin langsung dari contoh domain lain.

### 2. Model-free dan model-based RL

- **Model-free:** belajar melalui interaksi dengan lingkungan tanpa memerlukan pengetahuan awal tentang dinamika transisi.
- **Model-based:** membangun atau menggunakan model dinamika lingkungan untuk merencanakan tindakan dan menyempurnakan policy.
- Model-based planning dapat memakai model yang telah ditentukan sebelumnya atau model yang dipelajari dari interaksi.
- Penulis mengaitkan simulasi menggunakan model dengan potensi peningkatan sample efficiency karena agen dapat mengevaluasi kemungkinan hasil tanpa selalu melakukan interaksi langsung.
- Artikel mengulas Dynamic Programming, Monte Carlo Tree Search (MCTS), prioritized sweeping, dan Dyna-Q sebagai bagian dari pembahasan perencanaan berbasis model.

**Relevansi:** penelitian ini memiliki lingkungan simulasi gedung yang direpresentasikan sebagai graf. Model transisi lingkungan dapat ditentukan melalui aturan simulasi; hal ini tidak otomatis menjadikan algoritma PPO sebagai model-based. Dalam taksonomi artikel, PPO dikelompokkan sebagai policy-based, function approximation, dan model-free. Model lingkungan yang dipakai simulator dan paradigma model-based/model-free pada algoritma pembelajaran perlu dibedakan.

### 3. Taksonomi algoritma RL

Artikel menekankan tiga dimensi klasifikasi yang berbeda:
1. **Target optimasi:** value-based, policy-based, atau actor-critic.
2. **Dinamika lingkungan:** model-free atau model-based.
3. **Representasi state/action:** tabular atau function approximation.

Contoh pada tabel taksonomi artikel menempatkan PPO sebagai policy-based, function approximation, dan model-free. Artikel juga menjelaskan bahwa actor-critic menggabungkan policy/value: actor mengoptimalkan policy, sedangkan critic memperkirakan nilai untuk memberi umpan balik pada pembaruan actor.

**Catatan penting:** PPO dimasukkan dalam kelompok policy-based pada sumbu target optimasi, tetapi penjelasan implementasi PPO di artikel menyebut implementasi praktisnya beroperasi secara fungsional sebagai arsitektur actor-critic karena memiliki parameter policy (actor) dan value function (critic). Kedua penjelasan ini tidak perlu dianggap bertentangan karena taksonomi dan struktur implementasi dibahas pada sudut yang berbeda.

### 4. PPO: prinsip dan alur

Artikel menjelaskan PPO sebagai pengembangan policy-gradient yang dirancang untuk memperoleh pembaruan policy yang lebih stabil dan sample-efficient. PPO menggunakan *clipped surrogate objective* dengan rasio probabilitas antara policy baru dan policy lama.

Alur implementasi yang dirangkum:
1. Mengumpulkan trajectory menggunakan policy lama.
2. Mengestimasi advantage dari trajectory.
3. Mengoptimalkan surrogate objective selama beberapa epoch dengan mini-batch.
4. Memperbarui parameter policy dan value function, kemudian menjadikan policy terbaru sebagai policy lama untuk iterasi berikutnya.

Clipping pada rasio probabilitas membatasi perubahan policy agar pembaruan tidak terlalu besar. Artikel juga menyebut value-function loss berbasis squared error untuk memperbarui critic.

**Relevansi:** uraian ini mendukung landasan konseptual PPO, khususnya policy update, advantage estimation, actor-critic implementation, dan alasan clipping digunakan untuk membatasi perubahan policy. Formulasi matematis final untuk BAB II/BAB III tetap perlu dicocokkan dengan sumber primer PPO, terutama Schulman et al. (2017), bukan hanya mengandalkan survey ini.

### 5. Alasan pemilihan policy-gradient dan PPO menurut penulis

Dalam bagian *Algorithmic Rationale and Selection Criteria*, artikel menyatakan:
- Value-based methods menghadapi kesulitan pada continuous action spaces karena operasi max dapat mahal secara komputasi.
- Policy-based methods mengoptimalkan policy secara langsung dan dipandang cocok untuk continuous control.
- REINFORCE sederhana, tetapi dapat memiliki variance tinggi dan konvergensi lambat.
- TRPO membatasi pembaruan policy dengan KL-divergence, tetapi memiliki overhead komputasi lebih tinggi karena perhitungan orde kedua.
- PPO menggunakan objective clipping untuk menghindari pembaruan policy yang terlalu besar tanpa overhead matematis orde kedua seperti TRPO.

Penulis menyebut PPO banyak digunakan pada robotics, mixed-autonomy traffic control, dan RLHF, serta menilai keseimbangan implementasi, sample complexity, dan robustness hyperparameter sebagai alasan praktis penggunaannya.

**Batas interpretasi:** pernyataan bahwa PPO merupakan “industry standard” untuk continuous control adalah penilaian yang disampaikan penulis survey, bukan hasil eksperimen komparatif baru oleh artikel ini. Pada bagian Discussion, penulis secara eksplisit menyatakan survey tidak bertujuan menentukan algoritma yang unggul secara universal dan perbandingan lintas studi tidak dapat disimpulkan tanpa pengujian pada masalah serta kondisi yang sama.

### 6. Contoh penerapan PPO yang dirangkum

Artikel mengulas beberapa domain, antara lain:
- **Mixed-autonomy traffic optimization:** PPO untuk kebijakan pengendalian kendaraan terhubung dalam lalu lintas yang bercampur dengan kendaraan yang dikemudikan manusia. Penulis merangkum bahwa kebijakan tingkat jaringan meningkatkan total reward dan kecepatan rata-rata dibanding kebijakan tingkat individu pada eksperimen yang ditinjau.
- **Power-grid operation:** PPO untuk mengelola aliran daya jaringan secara real-time; validasi yang dirangkum masih berbasis simulasi.
- **Metro scheduling:** PPO untuk optimasi jadwal layanan dan komposisi kereta, dibandingkan dengan algoritma metaheuristik.
- **Task scheduling:** PPO digabungkan dengan aturan prioritas ED-LDF untuk mengurangi dimensi action space.
- **Intersection coordination:** Model Accelerated PPO (MA-PPO) menggabungkan model awal dengan PPO; studi yang dirangkum melaporkan waktu komputasi koordinasi turun hingga 1/400 waktu MPC pada skenario persimpangan empat arah satu lajur.
- **UAV/quadrotor control:** PPO digunakan untuk kontrol sikap dan posisi, dengan batas generalisasi pada model dan kondisi simulasi yang diuji.
- **Autonomous vehicle lane changing:** reward mempertimbangkan keselamatan, efisiensi, dan kenyamanan; studi yang dirangkum juga menggunakan modul intervensi keselamatan untuk mengganti aksi yang dinilai berbahaya.

**Relevansi:** contoh traffic optimization dan lane changing menunjukkan bahwa PPO pernah digunakan untuk keputusan dinamis pada sistem transportasi serta reward multi-aspek yang memasukkan keselamatan. Akan tetapi, kendaraan dan lalu lintas jalan berbeda dari pedestrian di dalam gedung. Artikel ini tidak menguji ST-HGAT + PPO untuk evakuasi gedung, sehingga tidak dapat dijadikan bukti langsung efektivitas arsitektur penelitian.

### 7. Tren, tantangan, dan arah penelitian

Artikel membahas:
- **RLHF:** penggunaan umpan balik manusia untuk membantu menentukan tujuan, dengan PPO disebut sebagai salah satu algoritma yang digunakan.
- **Hierarchical RL:** kebijakan bertingkat, di mana kebijakan tingkat tinggi memilih sub-policy untuk tujuan yang lebih spesifik.
- **Offline RL:** belajar dari dataset interaksi yang sudah dikumpulkan, relevan ketika interaksi langsung mahal, berisiko, atau tidak praktis; tantangannya termasuk distributional shift dan extrapolation error.
- **Transfer learning:** menggunakan policy, reward, representasi, atau dinamika dari tugas sumber untuk membantu tugas target; terdapat risiko negative transfer.
- **AI ethics/safety:** keselamatan dapat dimasukkan melalui constraints, shielding, runtime monitors, atau reward design; masing-masing memiliki keterbatasan.
- **Future directions:** sim-to-real gap, safe deployment pada lingkungan berisiko tinggi, offline RL, world models, dan HRL untuk tugas jangka panjang.

### 8. Batasan dan catatan kritis artikel

1. Artikel adalah survey, bukan eksperimen evakuasi atau evaluasi PPO pada satu lingkungan gedung.
2. Penulis menyatakan tidak semua algoritma dan studi tercakup karena keterbatasan ruang dan sumber daya.
3. Penulis secara eksplisit tidak mengklaim satu algoritma unggul universal; hasil RL/DRL dipengaruhi faktor eksternal dan internal sehingga perbandingan lintas studi tidak selalu sebanding.
4. Banyak contoh PPO berasal dari robotics, kendaraan, energi, penjadwalan, dan LLM; relevansinya untuk evakuasi gedung bersifat analogi metodologis, bukan bukti langsung.
5. Accepted manuscript masih dapat mengalami penyuntingan sebelum Version of Record; periksa kembali versi final sebelum mengunci sitasi, halaman, dan detail persamaan.
6. Struktur artikel memiliki ketidaksesuaian editorial: bagian pengantar menyebut susunan section yang tidak sepenuhnya konsisten dengan heading isi (misalnya pembahasan future directions berada pada Section 7, discussion pada Section 8, dan conclusion pada Section 9). Gunakan heading aktual dari naskah saat merujuk bagian.

## Sintesis dan relevansi untuk Tugas Akhir

1. Artikel ini dapat mendukung subbab 2.6 Reinforcement Learning untuk komponen RL, MDP, state/action/reward/policy, return, value function, exploration-exploitation, serta perbedaan model-free dan model-based.
2. Artikel ini dapat mendukung subbab 2.7 PPO untuk prinsip policy-gradient, clipped surrogate objective, advantage estimation, dan struktur actor-critic pada implementasi PPO.
3. Artikel memberi justifikasi konseptual bahwa PPO telah diterapkan pada beberapa masalah keputusan dinamis, termasuk optimasi lalu lintas dan kendaraan otonom. Penggunaan tersebut hanya menjadi analogi domain; penelitian ini tetap perlu menunjukkan kesesuaian state, action, reward, dan constraint keselamatan pada konteks pedestrian gedung.
4. Untuk penelitian ini, keselamatan sebaiknya dirumuskan sebagai batasan/komponen desain yang eksplisit, bukan hanya diasumsikan tercapai karena reward PPO. Artikel membahas safety constraints, shielding, runtime monitors, dan reward design sebagai pilihan pengendalian risiko secara umum.
5. Keberadaan simulator yang memiliki model transisi tidak berarti policy PPO otomatis menjadi model-based. Klasifikasi algoritma pembelajaran dan model dinamika simulator perlu dijelaskan secara terpisah.
6. Artikel tidak membahas ST-HGAT, heterogenous graph attention, atau integrasi ST-HGAT dengan PPO untuk evakuasi. Ia merupakan sumber RL/PPO umum dan bukan bukti arsitektur gabungan penelitian.

## Lokasi bagian penting dalam accepted manuscript

Karena naskah yang dibaca masih berstatus accepted manuscript/article in press dan pagination final belum dipastikan, rujukan sementara dicatat berdasarkan section:
- Section 1–2: pengantar RL, komponen RL, MDP, exploration-exploitation.
- Section 2.3: tiga dimensi taksonomi algoritma RL.
- Section 3.1.2: model-based planning, MCTS, prioritized sweeping, dan Dyna-Q.
- Section 4.3: PPO, clipped surrogate objective, algoritma, serta contoh penerapan.
- Section 4.3.1: rationale dan kriteria pemilihan policy-gradient/PPO.
- Section 5: actor-critic.
- Section 6: RLHF, HRL, offline RL, transfer learning, dan AI ethics.
- Section 7–9: future directions, discussion, dan conclusion.

## Status pembacaan setelah tahap 11

Dari 30 publikasi yang terinventarisasi:
- Dibaca penuh/isi utama: 30 publikasi.
- Dibaca sebagian: 0 publikasi.
- Belum dibaca sama sekali: 0 publikasi.

**Catatan:** status “dibaca penuh” berarti isi utama publikasi telah ditelaah. Untuk Ghasemi et al. (2026), teks yang dibaca adalah accepted manuscript/article in press; verifikasi ulang terhadap Version of Record tetap diperlukan sebelum sitasi final.

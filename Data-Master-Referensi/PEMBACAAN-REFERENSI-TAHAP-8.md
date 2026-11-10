# Catatan Pembacaan Referensi — Tahap 8

**Topik Tugas Akhir:** Optimasi Rute Evakuasi Dinamis pada Lingkungan Gedung Kampus Menggunakan ST-HGAT dan PPO.

**Tanggal:** 10 November 2026

## Cakupan dan batas akses
Tahap ini menindaklanjuti empat publikasi yang sebelumnya belum dibaca dan satu publikasi yang masih dibaca sebagian. Pemeriksaan dilakukan dengan mengutamakan laman penerbit dan PDF open-access. Hasilnya:
- Nurcahyo dan Putranto (2026): PDF penerbit dapat dibaca lengkap.
- Ning dan Xie (2024): metadata dan abstrak penerbit dapat diperiksa; PDF lengkap belum berhasil diambil/dibaca pada sesi ini.
- Faisal et al. (2026): metadata, abstrak, daftar referensi, dan halaman penerbit dapat diperiksa; PDF lengkap belum berhasil diambil/dibaca.
- Ghasemi et al. (2026): metadata dan abstrak penerbit dapat diperiksa; PDF lengkap belum berhasil diambil/dibaca.
- Wang et al. (2024): abstrak dan metadata telah diperiksa pada PubMed/IEEE; artikel dinyatakan closed access pada rekaman DBLP dan PDF lengkap belum tersedia dari sumber terbuka yang dapat diperiksa.

Dengan demikian, hanya satu artikel pada tahap ini yang dapat dinyatakan dibaca penuh. Tiga artikel baru dan Wang tetap berstatus dibaca sebagian. Tidak ada klaim bahwa abstrak setara dengan pembacaan artikel lengkap.

## A. Nurcahyo dan Putranto (2026) — dibaca penuh

**Judul:** “Spatio-Temporal Graph Neural Network for Solar Irradiance Prediction: A Case Study in Nganjuk, Indonesia.”
**Publikasi:** Journal of Information Systems and Informatics, Vol. 8, No. 1, Februari 2026, hlm. 617–635.
**DOI:** https://doi.org/10.63158/journalisi.v8i1.1424
**Sumber:** PDF penerbit open-access, 19 halaman artikel (hlm. jurnal 617–635).

### Tujuan dan objek
Penelitian mengembangkan pendekatan spatio-temporal berbasis GNN untuk memperkirakan iradiasi matahari di Kecamatan Sawahan, Kabupaten Nganjuk. Motivasi utamanya adalah keterbatasan model time-series satu lokasi dalam menangkap ketergantungan spasial antar lokasi pengamatan.

### Data dan konstruksi graf
- Data berasal dari lima Automatic Weather Stations (AWS) milik BMKG di Nganjuk dan sekitarnya.
- Data iradiasi global memiliki resolusi waktu 30 menit selama Januari–Desember 2024.
- Setiap stasiun direpresentasikan sebagai node pada graf tak berarah.
- Edge dibentuk berdasarkan kedekatan geografis, dengan bobot berbasis jarak Euclidean dari koordinat lintang dan bujur.
- Sawahan dijadikan target node, sedangkan empat stasiun lain menjadi supporting nodes.

### Arsitektur dan pelatihan
- Spatial representation menggunakan satu lapisan Graph Convolutional Network (GCN).
- Temporal dependency dipelajari menggunakan Long Short-Term Memory (LSTM).
- Representasi spasial dari GCN diberikan ke LSTM untuk mempelajari pola temporal.
- Data dibagi secara temporal: 80% observasi lebih awal untuk pelatihan dan 20% observasi terbaru untuk pengujian.
- Loss yang digunakan adalah Mean Squared Error (MSE), optimizer Adam.
- Konfigurasi yang dicantumkan: GCN hidden units 64, LSTM hidden units 64, sequence length 24, learning rate 0,001, batch size 32, dan 100 epoch.

### Hasil
Pada target node Sawahan, penulis melaporkan:
- MAE 102,64 W/m².
- RMSE 166,76 W/m².
- R² 0,6446.

Penulis menyatakan agregasi spasial membantu mengurangi fluktuasi prediksi ekstrem dibandingkan pendekatan yang hanya menggunakan satu lokasi. Namun, paper tidak menyediakan eksperimen baseline terpisah seperti persistence, single-station LSTM, ARIMA, atau tree-based regression sehingga kontribusi kuantitatif GCN tidak dapat diisolasi melalui perbandingan baseline tersebut.

### Keterbatasan dan catatan kritis
- Graf hanya memiliki lima stasiun; penulis menyatakan jumlah ini membatasi kekayaan pola spasial dan generalisasi.
- Fitur utama yang digunakan adalah iradiasi matahari; faktor meteorologi lain belum dimasukkan.
- Tidak ada baseline terpisah untuk membandingkan manfaat GCN terhadap metode time-series tunggal.
- Terdapat indikasi kesalahan penulisan pada tabel koordinat: nilai lintang yang tercetak seperti -78.xxx tidak konsisten dengan posisi geografis Nganjuk yang berada sekitar 7–8 derajat lintang selatan. Jangan gunakan koordinat tersebut sebelum klarifikasi.
- Persamaan adjacency pada PDF menuliskan kondisi diagonal secara tidak konsisten: baris kedua juga menampilkan i ≠ j, padahal uraian menyatakan self-loop. Perlu diperlakukan sebagai potensi typo dan tidak disalin tanpa verifikasi.

### Relevansi terhadap Tugas Akhir
Sumber ini relevan untuk contoh penerapan GCN dan LSTM dalam satu pipeline spatio-temporal pada graf dengan struktur spasial yang dibangun dari kedekatan antar-node. Namun, domainnya adalah prediksi iradiasi matahari, bukan evakuasi. Paper ini bukan bukti bahwa GCN-LSTM atau ST-GNN akan efektif pada graf gedung, dan bukan model ST-HGAT atau PPO.

**Halaman penting:** motivasi dan gap (617–619); data dan graf (619–622); arsitektur serta pembagian data (622–623); hasil (624–628); keterbatasan dan kesimpulan (629–631).

## B. Ning dan Xie (2024) — dibaca sebagian

**Judul:** “A Survey on Multi-Agent Reinforcement Learning and Its Application.”
**Publikasi:** Journal of Automation and Intelligence, Vol. 3, No. 2, Juni 2024, hlm. 73–91.
**DOI:** https://doi.org/10.1016/j.jai.2024.02.003
**Sumber yang diperiksa:** halaman penerbit SciOpen dan metadata ScienceDirect/DOAJ; abstrak dan metadata diperiksa. PDF 1,6 MB ditampilkan sebagai tersedia pada penerbit, tetapi isi PDF belum berhasil diakses/dibaca dalam sesi ini.

### Informasi yang didukung abstrak
- Artikel merupakan survey mengenai perkembangan dan aplikasi Multi-Agent Reinforcement Learning (MARL).
- Topik yang disebut mencakup stochastic games, metode MARL, bentuk spasial MARL, klasifikasi tugas, tantangan aplikasi, tuning hyperparameter, dan kompleksitas komputasi.
- Aplikasi yang ditinjau mencakup intelligent machines/devices, chemical engineering, biotechnology, healthcare, dan societal issues.
- Survey juga membahas benchmark environment untuk evaluasi MARL.

### Relevansi dan batas penggunaan
Sumber dapat membantu sebagai referensi umum jika penelitian nantinya membahas MARL atau banyak agen yang belajar berinteraksi. Namun, rancangan Tugas Akhir belum menetapkan multi-agent RL; karena itu artikel ini tidak boleh digunakan untuk menyatakan bahwa sistem penelitian pasti menggunakan MARL atau multi-agent PPO. Rincian taksonomi, algoritma, dan tantangan spesifik belum dapat disimpulkan dari abstrak saja.

## C. Faisal et al. (2026) — dibaca sebagian

**Judul:** “Natural Disaster Report on Social Media Classification Method Based on Word Embedding and Graph Attention Network.”
**Publikasi:** BAREKENG: Jurnal Ilmu Matematika dan Terapan, Vol. 20, No. 3, April 2026, hlm. 2613–2630.
**DOI:** https://doi.org/10.30598/barekengvol20iss3pp2613-2630
**Sumber yang diperiksa:** halaman artikel penerbit, metadata, abstrak, dan daftar referensi; PDF lengkap belum berhasil dibaca.

### Informasi yang didukung abstrak
- Penelitian membandingkan Graph Convolutional Network (GCN) dan Graph Attention Network (GAT) untuk klasifikasi tweet terkait bencana alam.
- Input menggunakan word embedding Word2Vec, FastText, dan GloVe.
- Pengujian mencakup tujuh dataset multilingual.
- Abstrak melaporkan GAT mengungguli GCN pada semua skenario yang diuji.
- FastText menghasilkan performa individual tertinggi; penggabungan embedding tertentu dapat menurunkan performa karena redundansi.
- Rata-rata F1-score yang dilaporkan adalah 0,749 untuk GCN dan 0,915 untuk GAT.

### Relevansi dan batas penggunaan
Artikel ini memberi contoh penerapan GAT pada informasi terkait bencana, tetapi tugasnya adalah klasifikasi teks media sosial, bukan simulasi evakuasi, pemodelan topologi ruang, atau pengambilan keputusan rute. Hasil F1-score tidak dapat dibandingkan langsung dengan metrik waktu evakuasi. Detail konstruksi graf, pembagian data, konfigurasi model, dan pengujian belum boleh dijelaskan lebih jauh sebelum PDF lengkap dibaca.

## D. Ghasemi, Moosavi, dan Ebrahimi (2026) — dibaca sebagian

**Judul:** “Reinforcement Learning and Model-based Planning in Practice: A Survey of Algorithmic Rationale and Domain Applications.”
**Publikasi:** Artificial Intelligence Review, 2026. Artikel open-access, diterbitkan 14 Agustus 2026 sebagai accepted research version.
**DOI:** https://doi.org/10.1007/s10462-026-11640-4
**Sumber yang diperiksa:** halaman artikel Springer dan abstrak; PDF penuh belum berhasil diakses/dibaca.

### Informasi yang didukung abstrak
- Artikel merupakan survey RL, integrasi deep learning dengan RL menjadi DRL, serta model-based planning.
- Cakupan disebut meliputi metode tabular klasik hingga teknik DRL mutakhir.
- Abstrak menyebut pembahasan skalabilitas, sample efficiency, applicability, convergence, stability, dan exploration-exploitation trade-off.
- Kata kunci mencakup model-free, model-based, actor-critic, Q-learning, DQN, TD3, PPO, dan TRPO.

### Relevansi dan batas penggunaan
Survey ini berpotensi menjadi referensi pendukung untuk membandingkan keluarga algoritma RL dan pertimbangan pemilihan metode. Namun, karena PDF lengkap belum ditelaah, tidak boleh mengatribusikan rekomendasi pemilihan PPO, rincian perbandingan algoritma, atau kesimpulan domain tertentu kepada penulis berdasarkan abstrak saja.

## E. Wang et al. (2024) — tetap dibaca sebagian

**Judul:** “Deep Reinforcement Learning: A Survey.”
**Publikasi:** IEEE Transactions on Neural Networks and Learning Systems, Vol. 35, No. 4, April 2024, hlm. 5064–5078.
**DOI:** https://doi.org/10.1109/TNNLS.2022.3207346
**Sumber yang diperiksa:** abstrak PubMed, metadata IEEE, dan rekaman bibliografi DBLP. Rekaman DBLP menyebut akses closed; PDF lengkap belum tersedia dari sumber terbuka yang berhasil diperiksa.

### Informasi yang didukung abstrak
- DRL menggabungkan kemampuan representasi fitur deep learning dengan kemampuan pengambilan keputusan RL.
- Survey mencakup value-based, policy-based, dan maximum-entropy DRL.
- Tantangan yang disebut mencakup limited samples, sparse rewards, dan multi-agent learning.
- Subbidang yang disebut termasuk hierarchical RL, multi-agent RL, dan imitation learning.

### Batas penggunaan
Status tetap dibaca sebagian. Jangan mengutip rincian isi bab, tabel algoritma, atau klaim komparatif yang tidak ada dalam abstrak sampai PDF penuh tersedia.

## F. Sintesis tahap 8
1. Nurcahyo dan Putranto memberikan contoh empiris integrasi GCN untuk representasi spasial dan LSTM untuk dependensi temporal pada graf lima stasiun. Ini mendukung kelayakan konsep pemrosesan spasial-temporal pada graf, tetapi domain dan tujuan prediksinya berbeda dari evakuasi.
2. Ning dan Xie membahas MARL secara luas. Relevansinya bersyarat karena Tugas Akhir belum menetapkan arsitektur multi-agent RL.
3. Faisal et al. menerapkan GAT pada klasifikasi laporan bencana di media sosial. Relevansinya pada mekanisme attention dan domain informasi bencana, bukan pada simulasi gerak penghuni.
4. Ghasemi et al. dan Wang et al. berpotensi menjadi referensi teori RL/DRL, tetapi pembacaan abstrak saja tidak cukup untuk menyusun uraian teknis rinci.
5. Empat publikasi yang baru ditinjau tidak mengubah keputusan arsitektur Tugas Akhir secara otomatis. Pemilihan ST-HGAT dan PPO tetap harus dijustifikasi berdasarkan formulasi graf gedung, dinamika keadaan, ruang tindakan, reward, dan evaluasi yang dirancang pada penelitian.

## G. Status setelah tahap 8
Dari inventarisasi 30 publikasi:
- Dibaca penuh/isi utama: 25 publikasi.
- Dibaca sebagian: 4 publikasi (Wang et al. 2024, Ning & Xie 2024, Faisal et al. 2026, Ghasemi et al. 2026).
- Belum dibaca sama sekali: 1 publikasi? Tidak ada artikel tambahan yang belum disentuh pada tahap ini; semua empat artikel yang sebelumnya belum dibaca telah diperiksa minimal metadata/abstraknya. Karena itu kategori “belum dibaca” menjadi 0, dengan catatan empat PDF tersebut belum ditelaah utuh.

**Catatan penting:** hitungan status menggunakan kategori “dibaca sebagian” untuk artikel yang baru diperiksa melalui abstrak/metadata. Status keseluruhan adalah 25 penuh, 5 sebagian jika memasukkan Wang et al. sebelumnya serta empat artikel pada tahap ini: jumlah tepat 25 penuh + 5 sebagian = 30. 

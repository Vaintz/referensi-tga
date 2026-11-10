# Catatan Pembacaan Referensi — Tahap 1

**Topik Tugas Akhir:** Optimasi Rute Evakuasi Dinamis pada Lingkungan Gedung Kampus Menggunakan ST-HGAT dan PPO.

**Tanggal pemeriksaan:** 10 November 2026

## Cakupan dan status

Repository berisi 30 file PDF yang berhubungan dengan 30 entri dalam `library.bib`. Pada tahap ini, empat publikasi evakuasi yang juga tersedia sebagai dokumen dalam konteks proyek telah dibaca isi utamanya (abstrak, pendahuluan, metode, hasil, kesimpulan, dan keterbatasan jika dijelaskan). Dua puluh enam PDF lainnya telah terinventarisasi berdasarkan lokasi dan nama file, tetapi isi lengkapnya belum ditelaah dalam catatan ini. Karena itu, status 26 publikasi tersebut tidak boleh disebut "dibaca penuh".

## A. Publikasi yang telah dibaca

### R-08 — Arifati et al. (2025)

**Judul:** Creating A Model for Evacuation Simulation of Earthquakes in Multi-Storey Buildings using 3D GIS and Agent-Based Model (ABM)  
**Publikasi:** Indonesian Journal of Geography, Vol. 57, No. 3, 2025, hlm. 430–439.  
**DOI:** https://doi.org/10.22146/ijg.92295  
**Lokasi PDF:** `2.2-Simulasi-dan-Pemodelan-Pergerakan-Penghuni/`  
**Status:** Dibaca penuh pada bagian artikel yang relevan.

**Tujuan dan masalah**
Penelitian mengembangkan simulasi evakuasi gempa pada gedung bertingkat dengan menggabungkan 3D GIS dan ABM. Penulis menyoroti bahwa sejumlah model sebelumnya belum merepresentasikan detail interior gedung secara memadai, misalnya ruang, pintu, tangga, dan furnitur.

**Metode dan data**
- Studi kasus pada gedung Postgraduate School UGM yang memiliki lima lantai dan satu basement.
- Geometri bangunan diperoleh melalui pengukuran lapangan dan denah; elemen bangunan dimodelkan dengan Revit lalu digunakan dalam Pathfinder.
- Sebanyak 266 agen ditempatkan berdasarkan observasi okupansi.
- Karakter agen dibedakan menjadi dosen/staf, mahasiswa, dan tamu, dengan variasi kecepatan berjalan, usia/jenis kelamin, waktu reaksi, dan pengetahuan terhadap gedung.
- Agen diarahkan menuju pintu keluar terdekat dan menghindari penghalang serta agen lain.
- Validasi dilakukan dengan membandingkan waktu berjalan nyata dan simulasi pada tangga.

**Hasil utama**
- Seluruh 266 agen dievakuasi dalam 140,8 detik pada skenario utama; penulis tidak menemukan bottleneck pada skenario tersebut.
- Skenario satu pintu keluar pada ruangan tertentu menghasilkan waktu 164,6 detik.
- Penambahan furnitur pada model ruang meningkatkan waktu evakuasi sekitar 36 detik.
- Tamu yang diasumsikan tidak mengenal gedung cenderung keluar paling akhir, sedangkan agen yang mengenal gedung cenderung lebih cepat.
- Perbedaan waktu validasi yang dilaporkan pada abstrak adalah 0,45 detik; uraian hasil menyebut perbedaan sekitar 0,4–0,5 detik untuk kelompok mahasiswa.

**Keterbatasan yang dinyatakan penulis**
- Perilaku agen masih sederhana: agen langsung mengenali pintu keluar terdekat dan bergerak tanpa ragu.
- Belum memodelkan perilaku tingkat tinggi seperti membantu orang lain atau merangkak.
- Dinamika kerusakan gedung akibat gempa belum dimodelkan; furnitur diperlakukan statis.
- Penulis menyarankan pemodelan perilaku agen yang lebih beragam dan dinamika kerusakan bangunan pada penelitian selanjutnya.

**Relevansi untuk penelitian ini**
- Mendukung alasan bahwa simulasi evakuasi gedung perlu memperhatikan struktur ruang, tangga, pintu, furnitur/penghalang, distribusi penghuni, dan karakteristik penghuni.
- Menunjukkan bagaimana kondisi ruang dan akses keluar dapat memengaruhi waktu serta kepadatan evakuasi.
- Dapat digunakan sebagai pembanding penelitian simulasi evakuasi gedung bertingkat.
- Tidak menjadi bukti langsung bahwa ST-HGAT atau PPO efektif, karena penelitian ini menggunakan 3D GIS, ABM, dan Pathfinder.

**Catatan kritis**
Artikel PDF yang tersimpan tampak memuat hasil ekstraksi halaman dari artikel lain yang tidak berkaitan sebelum bagian artikel Arifati. Saat menggunakan kutipan, pastikan merujuk halaman artikel yang benar, yaitu halaman jurnal 430–439. Jangan mengambil isi artikel lain yang ikut terbaca sebagai bagian dari PDF.

### R-09 — Mu'arifin, Harsono, dan Barakbah (2023)

**Judul:** Pemodelan Evakuasi pada Ruang Koridor dengan Cellular Automata berbasis Perilaku Manusia  
**Publikasi:** Techno.COM, Vol. 22, No. 4, November 2023, hlm. 797–804.  
**DOI:** https://doi.org/10.33633/tc.v22i4.9151  
**Lokasi PDF:** `2.1-Evakuasi-Bencana-pada-Lingkungan-Gedung/`  
**Status:** Dibaca penuh.

**Tujuan dan masalah**
Penelitian menganalisis dampak perilaku panik terhadap proses evakuasi di ruang koridor. Penulis menjelaskan faktor eksternal (misalnya struktur bangunan dan petunjuk evakuasi) serta faktor internal (misalnya usia, kecerdasan, dan kepanikan). Perilaku panik yang dibahas meliputi gerakan tidak terarah, mengikuti orang lain, kontak fisik, dan penumpukan di pintu keluar.

**Metode**
- Menggunakan Cellular Automata (CA) untuk memodelkan pergerakan pejalan kaki pada ruang koridor.
- Menggunakan deterministic parallel update untuk menentukan perpindahan agen ketika beberapa agen memilih sel yang sama.
- Menggabungkan static floor field dan dynamic floor field.
- Dynamic floor field dipengaruhi diffusion probability dan decay probability.
- Menambahkan parameter Ks dan Kd ke probabilitas perpindahan.
- Ks merepresentasikan tingkat pengetahuan agen terhadap pintu keluar; nilai Ks yang rendah dikaitkan dengan gerakan yang lebih acak.
- Kd merepresentasikan kecenderungan mengikuti pejalan kaki lain.
- Uji simulasi dilakukan pada ruang kerja Gedung D3 PENS dengan satu pintu keluar, kepadatan 2%–30%, diffusion probability 0,1, dan decay probability 0,3.

**Hasil utama**
- Pada nilai Kd tetap 0,5, peningkatan Ks menghasilkan waktu evakuasi yang lebih singkat dalam eksperimen yang dilaporkan.
- Pada Ks tetap 1, peningkatan Kd menghasilkan waktu evakuasi yang lebih lama.
- Penulis menafsirkan peningkatan kecenderungan mengikuti orang lain sebagai salah satu ciri perilaku panik yang dapat memperlambat evakuasi.

**Keterbatasan dan kehati-hatian**
- Eksperimen menggunakan ruang koridor dan satu pintu keluar; hasilnya tidak otomatis berlaku untuk gedung kampus multi-lantai dengan beberapa alternatif rute.
- Ks dan Kd merupakan parameter representasi perilaku dalam model; artikel menyarankan pendalaman lebih lanjut terhadap aspek kepanikan melalui bidang psikologi.
- Hasilnya merupakan hasil simulasi model CA, bukan pengukuran langsung perilaku semua penghuni gedung nyata.

**Relevansi untuk penelitian ini**
- Mendukung pembahasan bahwa perilaku penghuni dan interaksi antar-penghuni dapat memengaruhi waktu evakuasi.
- Menyediakan contoh bagaimana informasi tentang pintu keluar dan kecenderungan mengikuti orang lain direpresentasikan sebagai parameter.
- Dapat menjadi dasar konseptual untuk menentukan fitur perilaku penghuni, tetapi parameter Ks/Kd tidak boleh langsung dianggap sebagai variabel ST-HGAT atau reward PPO tanpa rancangan metodologis tersendiri.
- Berguna untuk BAB I sebagai contoh bahwa kepanikan dan perilaku mengikuti kerumunan dapat menghambat evakuasi; serta BAB II bagian 2.1 dan 2.2.

### R-10 — Karufa dan Ahmad (2023)

**Judul:** Model Evakuasi Keramaian dalam Gedung Memiliki Beberapa Pintu Keluar dengan Memperhatikan Kepanikan Individu  
**Publikasi:** Lebesgue: Jurnal Ilmiah Pendidikan Matematika, Matematika dan Statistika, Vol. 4, No. 3, Desember 2023, hlm. 1643–1650.  
**DOI:** https://doi.org/10.46306/lb.v4i3.458  
**Lokasi PDF:** `2.1-Evakuasi-Bencana-pada-Lingkungan-Gedung/`  
**Status:** Dibaca penuh.

**Tujuan dan masalah**
Penelitian bertujuan mengetahui pengaruh tingkat kepanikan individu terhadap waktu evakuasi dalam gedung dengan beberapa pintu keluar.

**Metode dan asumsi**
- Penelitian dasar/teoretis dengan metode deskriptif.
- Menggunakan Cellular Automata dan konsep static serta dynamic floor field.
- Perpindahan individu ditentukan melalui probabilitas transisi.
- Variabel meliputi ukuran grid, posisi pintu keluar, jumlah individu, koefisien floor field statis dan dinamis, indikator penghalang, serta koefisien panik.
- Asumsi model: gedung satu lantai dengan tiga pintu keluar; jumlah individu tidak bertambah; individu yang telah keluar tidak lagi diperhitungkan; satu individu menempati satu sel; perpindahan mengikuti probabilitas transisi.
- Posisi awal individu dibuat acak.
- Untuk setiap kombinasi parameter, simulasi dilakukan 30 kali dan waktu evakuasi dirata-ratakan.

**Hasil utama**
Simulasi menunjukkan bahwa peningkatan koefisien panik menghasilkan waktu evakuasi yang semakin lama. Penulis mengaitkannya dengan perilaku individu yang menjadi tidak terorganisasi atau kesulitan menentukan arah menuju pintu keluar.

**Keterbatasan dan kehati-hatian**
- Model dibatasi pada satu lantai dan tiga pintu keluar.
- Representasi individu dan ruang berbasis grid dengan asumsi satu individu per sel.
- Penelitian merupakan pemodelan teoretis; hasilnya tidak boleh ditafsirkan sebagai validasi empiris untuk gedung kampus tertentu.
- Abstrak dan kesimpulan mendukung hubungan antara koefisien panik dan waktu evakuasi, tetapi tidak menyediakan dasar untuk menyatakan bahwa semua bentuk kepanikan selalu menghasilkan pola pergerakan yang sama.

**Relevansi untuk penelitian ini**
- Mendukung uraian bahwa kepanikan dapat memengaruhi keputusan/pergerakan dan durasi evakuasi.
- Dapat menjadi contoh penelitian mikroskopis yang memperhitungkan perilaku individu.
- Dapat dibandingkan dengan pemodelan berbasis graf yang lebih menekankan struktur jaringan ruang dan hubungan antar-ruang.
- Relevan untuk BAB I serta BAB II bagian 2.1, 2.2, dan 2.10.

### R-11 — Hardiansyah et al. (2022)

**Judul:** Implementation of Agent Based Modelling to Observe the Evacuating Behavior at Faculty of Engineering Building, University of Bengkulu, Indonesia  
**Publikasi:** Journal of the Civil Engineering Forum, Vol. 8, No. 2, Mei 2022, hlm. 179–192.  
**DOI:** https://doi.org/10.22146/jcef.3589  
**Lokasi PDF:** `2.2-Simulasi-dan-Pemodelan-Pergerakan-Penghuni/`  
**Status:** Dibaca penuh.

**Tujuan dan data**
Penelitian menerapkan ABM untuk mengamati perilaku evakuasi gempa di Gedung Fakultas Teknik Universitas Bengkulu. Data meliputi layout gedung, jumlah dan distribusi penghuni, serta survei karakteristik/pilihan evakuasi. Survei awal mencatat populasi 250 orang; kuesioner melibatkan 71 responden.

**Metode**
- Menggunakan NetLogo sebagai lingkungan pemodelan ABM.
- Layout lantai, ruangan, tangga, dan pintu keluar dimasukkan ke dalam model.
- Agen bergerak dari ruang menuju tangga/pintu dan assembly point.
- Skenario mengubah kapasitas/populasi agen di dalam gedung.
- Hasil simulasi dibandingkan dengan kondisi nyata untuk memeriksa kesesuaian model.

**Hasil utama**
- Konflik kepadatan teridentifikasi pada koridor lantai 1 dan 2, tangga T1/T2/T3, serta pintu keluar P1–P4.
- Pada skenario kapasitas penuh, waktu menuju assembly point dilaporkan sekitar 111 detik.
- Tangga utama T1 mengalami kepadatan karena lebih banyak agen memilihnya.
- Penulis merekomendasikan penempatan tanda/petunjuk evakuasi.
- Artikel melaporkan koefisien determinasi validasi R² sebesar 0,978 antara hasil model dan kondisi nyata.

**Keterbatasan dan kehati-hatian**
- Model mengasumsikan semua agen mengetahui rute menuju assembly point dan seluruh pintu/tangga dapat digunakan; skenario juga dinyatakan bebas hambatan.
- Fokus penelitian pada satu gedung dan konfigurasi layout tertentu.
- Ada ketidakkonsistenan redaksi antara abstrak dan uraian hasil/kesimpulan mengenai hubungan persentase populasi dan waktu evakuasi. Pada pembahasan, skenario okupansi 20% dijelaskan menghasilkan persentase agen yang mencapai assembly point paling tinggi/evakuasi lebih cepat; angka waktu 111 detik disebut untuk kapasitas penuh. Jangan menyimpulkan arah hubungan populasi-waktu tanpa memeriksa grafik/tabel skenario secara langsung.
- R² yang tinggi pada validasi studi kasus ini tidak berarti model otomatis tervalidasi untuk gedung lain.

**Relevansi untuk penelitian ini**
- Sangat relevan sebagai studi empiris evakuasi gedung kampus di Indonesia.
- Mendukung pentingnya representasi layout, distribusi penghuni, tangga, pintu, titik konflik, dan kepadatan.
- Menjadi pembanding bagi pendekatan yang mengoptimalkan rute secara dinamis; studi ini menggunakan ABM/NetLogo, bukan ST-HGAT/PPO.
- Relevan untuk BAB I, BAB II bagian 2.1, 2.2, 2.9, dan 2.10.

## B. Inventarisasi PDF yang belum ditelaah isi lengkapnya

Status bagian ini adalah **terinventarisasi berdasarkan file dan metadata, belum dibaca penuh**.

### Referensi Latar Belakang BAB I
- Umahuk et al. (2025), analisis jalur evakuasi gedung Fakultas Teknik Universitas Pattimura menggunakan Dijkstra.
- Alrahma et al. (2024), Q-learning untuk desain rute evakuasi di Digital Center Building UNNES.
- Halisah dan rekan (2025), optimasi pencarian jalur evakuasi menggunakan ACO.
- Gebreyesus et al. (2025), DRL berbasis ST-GNN untuk job shop scheduling.
- Zhang et al. (2023), visual analytics rekomendasi rute evakuasi wisata berbasis GNN.

### BAB II — 2.3 Teori Graf dan Pemodelan Lingkungan Evakuasi
- Sharma et al. (2025), Graph Representation Techniques and Their Applications.
- Jiawei et al. (2024), GraphSAGE++: Weighted Multi-scale GNN for Graph Representation Learning.
- Jaeger (2023), Learning and Reasoning with Graph Data.

### BAB II — 2.4 Graph Neural Network
- Rizian et al. (2025/2026 — tahun perlu verifikasi), Graph Attention Networks untuk klasifikasi gejala monkeypox di media sosial.
- Fathinezhad et al. (2023), Graph Neural Networks and Reinforcement Learning: A Survey.

### BAB II — 2.5 ST-HGAT
- Zheng et al. (2025), A Survey of Dynamic Graph Neural Networks.
- Corradini et al. (2026), systematic literature review model ST-GNN untuk forecasting dan classification.
- Yang dan Peng (2024), Spatio-Temporal Contrastive Heterogeneous Graph Attention Networks for Session-Based Recommendation.

### BAB II — 2.6 Reinforcement Learning
- Vidyasagar (2023), A Tutorial Introduction to Reinforcement Learning.
- Wang et al. (2024), Deep Reinforcement Learning: A Survey.

### BAB II — 2.7 Proximal Policy Optimization
- Darmawan et al. (2025), PPO untuk model bahasa dan sistem ekonomi berbasis teks.
- Machmudi et al. (2025), PPO untuk alokasi sumber daya pada kernel mobile OS.

### BAB II — 2.8 Graph Reinforcement Learning
- Darvariu et al. (2024), Graph Reinforcement Learning for Combinatorial Optimization: A Survey and Unifying Perspective.
- Gao et al. (2022), Graph Convolution-Based Deep RL untuk pengambilan keputusan multi-agent pada skenario lalu lintas.
- Nie et al. (2023), Reinforcement Learning on Graphs: A Survey.

### Jurnal Pendukung Lainnya
- Ning dan Xie (2024), survey multi-agent reinforcement learning.
- Muttaqien et al. (2024), evaluasi rute akses darurat menggunakan ABM.
- Marliza dan Ahmad (2024), Cellular Automata untuk evakuasi pedestrian dengan kepanikan.
- Faisal et al. (2026), klasifikasi laporan bencana alam di media sosial menggunakan word embedding dan GAT.
- Ghasemi et al. (2026), survey RL dan model-based planning.
- Nurcahyo dan Putranto (2026), ST-GNN untuk prediksi iradiasi surya.

## C. Catatan pemeriksaan metadata awal

Pemeriksaan ini bersifat awal dan perlu dibandingkan lagi dengan halaman penerbit:
1. Entri `Rizian2026` mencatat tahun 2026, sedangkan DOI memuat identitas volume/issue tahun 2025. Tahun publikasi perlu dipastikan dari halaman jurnal.
2. Entri `Halisah2025` memiliki nama jurnal yang tampak terpotong dan DOI yang perlu dipastikan kelengkapannya.
3. Entri `Jaeger2023` bertipe `@misc`, padahal metadata menyebut publikasi di Frontiers in Artificial Intelligence. Tipe BibTeX dan metadata bibliografi perlu dirapikan setelah verifikasi.
4. Tahun, volume, nomor, halaman, dan DOI tidak boleh ditentukan hanya dari citation key; periksa laman penerbit atau PDF asli.

## D. Implikasi awal bagi penelitian

Berdasarkan empat publikasi yang telah dibaca, terdapat tiga aspek yang konsisten muncul:
1. **Struktur fisik gedung:** layout, pintu, tangga, koridor, penghalang, dan jumlah akses memengaruhi pergerakan serta potensi kepadatan.
2. **Karakteristik dan perilaku penghuni:** kecepatan berjalan, pengetahuan terhadap gedung, kepanikan, serta kecenderungan mengikuti orang lain dapat memengaruhi keputusan dan waktu evakuasi.
3. **Kepadatan dan konflik pergerakan:** titik sempit, tangga, koridor, dan pintu keluar dapat menjadi lokasi antrean atau bottleneck.

Keempat publikasi ini belum membuktikan efektivitas ST-HGAT atau PPO untuk evakuasi. Klaim tentang pemilihan ST-HGAT, PPO, dan integrasi keduanya harus didukung oleh pembacaan referensi GNN, ST-GNN/ST-HGAT, RL, PPO, dan GRL yang belum ditelaah pada tahap ini.

## E. Tahap berikutnya

Prioritas pembacaan lanjutan:
1. BAB I: Alrahma et al. (Q-learning), Halisah et al. (ACO), Umahuk et al. (Dijkstra), dan Zhang et al. (GNN untuk evakuasi).
2. BAB II 2.5 dan 2.8: Zheng, Corradini, Yang & Peng, Darvariu, dan Nie.
3. BAB II 2.6 dan 2.7: Vidyasagar, Wang, serta dua publikasi PPO.
4. BAB II 2.3 dan 2.4: tiga referensi graf dan dua referensi GNN.
5. Referensi pendukung lainnya untuk memperkaya perbandingan dan evaluasi.


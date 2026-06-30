---
name: ta-genai-processmining
description: >
  Skill khusus untuk menulis Tugas Akhir berjudul "Pemanfaatan Generative AI untuk Process Discovery pada Data Maintenance" atau topik sejenis yang menggabungkan process mining, generative AI (LLM/GPT), dan data event log maintenance/aset. Gunakan skill ini setiap kali diminta menulis atau merewrite bagian apapun dari tugas akhir ini: latar belakang, tinjauan pustaka, metodologi, hasil, pembahasan, abstrak, atau kesimpulan. Juga aktif saat pengguna meminta: humanize teks, reduce similarity, parafrase bab, tulis ulang paragraf, atau generate konten untuk bagian spesifik TA ini. Trigger kata kunci: "process discovery", "generative AI", "process mining", "maintenance", "event log", "LLM", "flower model", "conformance checking", "activity abstraction", "latar belakang TA", "bab 1", "bab 2", "tinjauan pustaka process mining", "metodologi AI", "humanize teks TA".
---

# Skill: TA — Pemanfaatan Generative AI untuk Process Discovery pada Data Maintenance

Skill ini dirancang khusus untuk mendukung penulisan tugas akhir dengan judul tersebut di atas.
Semua output mengikuti prinsip: **humanized, academic, minim similarity, bebas frasa klise dan tanda "--"**.

---

## KONTEKS PENELITIAN (Baca Dulu Sebelum Menulis)

**Judul:** Pemanfaatan Generative AI untuk Process Discovery pada Data Maintenance

**Domain inti:**
- Process Mining (khususnya Process Discovery)
- Generative AI / Large Language Model (LLM) sebagai komponen aktif pipeline
- Data maintenance / pemeliharaan aset (event log dari sistem CMMS, EAM, atau log kerja manual)

**Masalah khas yang biasanya diangkat:**
- Event log maintenance cenderung menghasilkan *flower model* (spaghetti process) karena aktivitas terlalu beragam dan tidak terstruktur
- Teknik process discovery konvensional (Alpha Miner, Heuristic Miner, Inductive Miner) kesulitan menghasilkan model yang dapat diinterpretasi
- Generative AI berperan dalam: abstraksi aktivitas, label normalization, activity clustering, kontekstualisasi proses, atau interpretasi model hasil discovery

**Posisi kontribusi penelitian ini:**
Mengintegrasikan kemampuan pemahaman bahasa dan penalaran LLM ke dalam tahap pra-pemrosesan atau pasca-pemrosesan process discovery, sehingga model proses yang dihasilkan lebih bersih, representatif, dan dapat diinterpretasi oleh domain expert.

---

## PRINSIP PENULISAN (WAJIB DIIKUTI DI SEMUA BAGIAN)

### Yang Tidak Boleh Muncul
- Tanda `--` atau `—` sebagai penghubung antarkalimat
- Frasa klise: *"Pertama-tama"*, *"Dapat disimpulkan bahwa"*, *"Dengan demikian"*, *"Hal ini menunjukkan bahwa"*, *"Tidak dapat dipungkiri"*, *"Di era digital ini"*, *"Seiring perkembangan teknologi"*
- Paragraf dengan 3 kalimat persis di setiap paragraf (terlalu simetris)
- Transisi eksplisit berulang: *"Selain itu, ... Selain itu, ... Selain itu"*
- Kalimat pasif monoton beruntun
- Pembuka dengan definisi ensiklopedis: *"Process mining adalah suatu teknik yang..."*

### Yang Harus Ada
- Variasi panjang kalimat: pendek (8–12 kata), menengah (15–25 kata), panjang kompleks (25–40 kata)
- Evidential hedging: *"mengindikasikan"*, *"cenderung"*, *"tampaknya"*, *"dalam batas tertentu"*
- Argumen dibangun induktif: dari fenomena konkret ke konsep abstrak
- Posisi analitis penulis muncul organik, bukan sekadar ringkasan sumber

---

## PANDUAN PENULISAN PER BAB

### BAB I — PENDAHULUAN

**Strategi Latar Belakang untuk Topik Ini**

Jangan buka dengan definisi process mining atau AI. Buka dengan **masalah nyata di lapangan maintenance**:

Alur yang disarankan:
1. *Fenomena gap maintenance* — Organisasi modern mengoperasikan sistem pemeliharaan berbasis data, tetapi proses aktual yang berjalan di lapangan sering kali berbeda jauh dari prosedur yang terdokumentasi
2. *Konteks digitalisasi maintenance* — Sistem CMMS/EAM menghasilkan volume log yang besar, tetapi potensi analitiknya belum dimanfaatkan sepenuhnya
3. *Problem process discovery pada domain ini* — Variasi aktivitas yang tinggi, penamaan yang tidak konsisten, dan urutan tugas yang tidak linear menghasilkan model proses yang sulit diinterpretasi
4. *Gap teknologi* — Teknik discovery konvensional belum mengakomodasi heterogenitas semantik dalam log maintenance
5. *Peluang Generative AI* — Kemampuan LLM dalam memahami konteks bahasa dan melakukan penalaran semantik membuka kemungkinan baru dalam pipeline process mining
6. *Justifikasi penelitian* — Mengapa integrasi ini relevan dan belum banyak dikaji

**Contoh kalimat pembuka yang baik (bukan template, adaptasi sesuai kondisi):**

> *"Sistem pemeliharaan aset di organisasi berskala besar meninggalkan jejak digital yang masif dalam bentuk log kejadian, namun jejak tersebut jarang dimanfaatkan untuk memahami bagaimana proses perawatan sebenarnya berjalan di lapangan."*

> *"Kesenjangan antara prosedur pemeliharaan yang terdokumentasi dan praktik aktual yang dilakukan teknisi di lapangan bukan sekadar persoalan kepatuhan — ia mencerminkan kompleksitas proses yang selama ini sulit ditangkap oleh pendekatan analitik konvensional."*

**Rumusan Masalah — Arahan Spesifik**

Pertanyaan penelitian harus menyentuh tiga dimensi:
- Bagaimana karakteristik event log maintenance yang menyebabkan hasil process discovery menjadi tidak representatif?
- Bagaimana generative AI dapat diintegrasikan ke dalam pipeline process discovery untuk mengatasi permasalahan tersebut?
- Sejauh mana model proses yang dihasilkan dengan bantuan generative AI lebih baik dibandingkan tanpa intervensi tersebut (dalam hal fitness, precision, simplicity, atau interpretability)?

---

### BAB II — TINJAUAN PUSTAKA

**Struktur Tinjauan Pustaka yang Disarankan**

Susun bukan sebagai daftar definisi, tetapi sebagai narasi yang membangun argumen mengapa penelitian ini perlu dilakukan:

1. **Process Mining sebagai Disiplin** — fokus pada evolusinya dari teknik audit sederhana ke analitik proses berbasis data; singgung keterbatasan teknik discovery pada data yang kompleks
2. **Algoritma Process Discovery** — bahas Alpha Miner, Heuristic Miner, Inductive Miner secara komparatif; tunjukkan di mana masing-masing gagal pada data maintenance yang noisy
3. **Permasalahan Flower Model dan Spaghetti Process** — ini inti masalah; jelaskan mengapa ia terjadi dan mengapa menjadi bottleneck dalam interpretasi proses
4. **Karakteristik Data Maintenance** — heterogenitas label aktivitas, variasi frekuensi, missing data, non-linear workflow
5. **Large Language Model dan Generative AI** — bukan overview umum LLM, tetapi spesifik pada kemampuan yang relevan: text normalization, semantic clustering, activity abstraction, contextual reasoning
6. **Integrasi AI dalam Process Mining** — kajian penelitian sebelumnya yang menyentuh AI-enriched process mining; identifikasi gap yang diisi oleh penelitian ini

**Teknik Menulis Tinjauan Pustaka yang Minim Similarity**

- Jangan definisikan setiap konsep dari satu sumber saja. Sintesiskan 2–3 sumber per konsep
- Setelah memaparkan konsep, selalu tambahkan kalimat relevansi: *"Dalam konteks data maintenance, konsep ini menjadi sangat relevan karena..."*
- Gunakan pola kontras: *"Sementara [Sumber A] menekankan aspek X, [Sumber B] justru menunjukkan bahwa Y bisa menjadi pembatas yang signifikan"*
- Tutup setiap subbab dengan *"gap statement"*: apa yang belum dijawab oleh literatur yang sudah dikaji

**Frasa Khas untuk Topik Ini**

- *"Algoritma Inductive Miner, meski dikenal lebih robust terhadap noise dibanding pendahulunya, tetap menghadapi tantangan ketika..."*
- *"Fenomena flower model bukan sekadar artefak visual — ia merupakan representasi dari ketidakmampuan algoritma menangkap struktur proses yang sesungguhnya dalam data yang..."*
- *"Kemampuan LLM dalam memahami variasi linguistik pada label aktivitas membuka kemungkinan yang sebelumnya tidak tersedia dalam ekosistem process mining tradisional"*
- *"Data event log dari sistem pemeliharaan memiliki karakteristik yang berbeda secara fundamental dari domain yang biasanya menjadi referensi dalam studi process mining, seperti healthcare atau finance"*

---

### BAB III — METODOLOGI PENELITIAN

**Pendekatan yang Sesuai untuk Penelitian Ini**

Penelitian ini kemungkinan bersifat *design science research* atau *experimental research* dengan:
- Objek: event log maintenance (real atau synthetic)
- Intervensi: pipeline yang mengintegrasikan Generative AI (mis. GPT via API) ke dalam tahap pra/pasca-processing
- Evaluasi: metrics process mining (fitness, precision, simplicity, generalization) dan/atau evaluasi kualitatif oleh domain expert

**Komponen Metodologi yang Perlu Dijelaskan Secara Naratif**

1. *Jenis penelitian dan justifikasinya* — jelaskan mengapa pendekatan yang dipilih sesuai dengan nature masalah (bukan karena mudah, tetapi karena epistemologis)
2. *Sumber dan karakteristik data* — dari mana event log diperoleh, bagaimana struktur kasusnya (case ID, activity, timestamp, resource), berapa volume dan rentang waktunya
3. *Pra-pemrosesan data* — bagaimana data dibersihkan sebelum masuk pipeline
4. *Desain pipeline AI-enriched process discovery* — ini bagian inti; jelaskan peran LLM di mana: apakah di activity abstraction, label normalization, atau interpretasi model hasil
5. *Prompt engineering* — jika LLM digunakan via API, jelaskan bagaimana prompt dirancang dan diuji
6. *Algoritma discovery yang digunakan* — dan alasan pemilihannya
7. *Metrik evaluasi* — definisikan dan justifikasi metrics yang digunakan
8. *Baseline perbandingan* — discovery tanpa intervensi AI sebagai pembanding

**Contoh Kalimat Metodologi yang Humanized**

> *"Data yang digunakan dalam penelitian ini bersumber dari sistem pencatatan pemeliharaan [nama sistem/instansi], yang mencakup log aktivitas selama periode [rentang waktu]. Pemilihan rentang waktu ini bukan sekadar pertimbangan volume data, melainkan didasarkan pada asumsi bahwa periode tersebut mencerminkan siklus pemeliharaan yang relatif lengkap."*

> *"Peran generative AI dalam pipeline ini tidak dimaksudkan sebagai pengganti algoritma discovery yang sudah ada, melainkan sebagai lapisan pra-pemrosesan semantik yang memungkinkan algoritma tersebut bekerja pada data yang lebih bersih dan koheren secara konseptual."*

> *"Evaluasi dilakukan dalam dua level: secara kuantitatif melalui empat dimensi conformance (fitness, precision, simplicity, generalization) dan secara kualitatif melalui penilaian domain expert terhadap keterbacaan model proses yang dihasilkan."*

---

### BAB IV — HASIL DAN PEMBAHASAN

**Struktur Penyajian Hasil**

1. *Gambaran umum event log* — statistik deskriptif: jumlah kasus, aktivitas unik, distribusi frekuensi, pola timestamp
2. *Hasil pra-pemrosesan konvensional* — apa yang terjadi tanpa intervensi AI (tampilkan model sebagai ilustrasi bottleneck)
3. *Proses abstraksi/normalisasi dengan LLM* — bagaimana LLM merespons, contoh transformasi label, statistik sebelum-sesudah
4. *Model proses hasil discovery pasca-AI* — tampilkan dan deskripsikan secara naratif
5. *Perbandingan metrik* — tabel perbandingan dengan baseline; analisis per dimensi

**Cara Menulis Pembahasan yang Tidak Terkesan AI**

- Mulai dari **anomali atau temuan yang tidak terduga** — ini ciri khas penulis yang benar-benar memahami datanya
- Hubungkan setiap temuan ke literatur di Bab II secara spesifik, bukan generik
- Akui keterbatasan dengan jujur — misalnya: LLM kadang salah mengabstraksikan aktivitas yang sangat teknis dan domain-spesifik
- Gunakan frasa yang mencerminkan penalaran analitis, bukan deskripsi pasif

**Frasa Pembahasan Khas Topik Ini**

- *"Reduksi jumlah aktivitas unik dari [X] menjadi [Y] pasca-abstraksi LLM mengindikasikan bahwa sebagian besar variasi label dalam log bersifat semantik, bukan struktural."*
- *"Model yang dihasilkan setelah intervensi LLM menunjukkan peningkatan nilai simplicity yang cukup berarti, meskipun pada beberapa kasus, penggabungan aktivitas yang terlalu agresif justru menurunkan nilai fitness."*
- *"Temuan ini memperkuat argumen bahwa tantangan utama dalam process discovery pada domain maintenance bukan pada pilihan algoritma, melainkan pada kualitas semantik data masukan."*
- *"Ada titik tertentu di mana abstraksi yang dilakukan LLM mulai kehilangan granularitas yang justru penting bagi domain expert maintenance — kondisi ini menunjukkan bahwa integrasi LLM perlu disertai mekanisme validasi berbasis pengetahuan domain."*

---

### BAB V — KESIMPULAN DAN SARAN

**Kesimpulan — Cara Menulis yang Tidak Klise**

Jangan gunakan: *"Berdasarkan hasil penelitian, dapat disimpulkan bahwa..."*

Alternatif pembuka yang lebih berkarakter:
- *"Penelitian ini membuktikan bahwa keterbatasan process discovery pada data maintenance bukan sesuatu yang inheren tak teratasi..."*
- *"Apa yang tadinya tampak sebagai masalah data semata — variasi label yang tinggi dan struktur proses yang tidak linear — ternyata dapat ditangani secara sistematis melalui..."*
- *"Studi ini menegaskan posisi generative AI bukan sebagai pengganti, melainkan sebagai komplementer yang signifikan bagi ekosistem process mining yang sudah ada."*

**Saran — Harus Spesifik dan Actionable**

Saran teoretis (riset lanjutan):
- Pengujian pada domain maintenance yang berbeda (utilitas, rumah sakit, transportasi)
- Eksplorasi model LLM yang lebih ringan untuk deployment on-premise
- Pengembangan metrik evaluasi yang secara khusus mengakomodasi aspek interpretability

Saran praktis (bagi organisasi/praktisi):
- Rekomendasi konkret tentang tahap mana dalam pipeline yang paling menguntungkan dari intervensi LLM
- Panduan kualitas minimum event log maintenance agar pipeline ini dapat berjalan efektif

---

### ABSTRAK

**Template Struktur Abstrak untuk Topik Ini**

Dalam 200–250 kata (Indonesia) atau 150–200 kata (English):

> *[Kalimat 1–2: Konteks dan masalah]* Data event log dari sistem pemeliharaan aset menyimpan potensi analitik yang belum sepenuhnya dimanfaatkan, sebagian besar karena variasi aktivitas yang tinggi dan inkonsistensi label menyebabkan hasil process discovery menjadi tidak representatif.
>
> *[Kalimat 3: Tujuan]* Penelitian ini mengkaji kemungkinan mengintegrasikan generative AI ke dalam pipeline process discovery sebagai mekanisme abstraksi semantik yang dapat meningkatkan kualitas model proses yang dihasilkan.
>
> *[Kalimat 4–5: Metode]* Event log dari [sumber data] diolah melalui tahap pra-pemrosesan berbasis LLM sebelum diproses menggunakan algoritma [nama algoritma]. Evaluasi dilakukan secara kuantitatif menggunakan empat dimensi conformance dan secara kualitatif melalui penilaian domain expert.
>
> *[Kalimat 6–8: Temuan]* Hasil menunjukkan bahwa intervensi LLM mampu mereduksi jumlah aktivitas unik secara signifikan sekaligus meningkatkan nilai simplicity dan generalization model. Namun, diperlukan mekanisme validasi untuk mencegah hilangnya granularitas yang kritis bagi domain expert.
>
> *[Kalimat 9: Implikasi]* Temuan ini membuka jalur penelitian baru dalam pengembangan pipeline process mining yang peka terhadap konteks semantik domain.

---

## REFERENSI DOMAIN — KONSEP KUNCI & CARA MENULISKANNYA

Lihat file referensi tambahan untuk:
- `references/konsep-domain.md` — Definisi, frasa, dan cara membahas konsep inti tanpa plagiarisme
- `references/frasa-humanized-topik.md` — Bank kalimat siap pakai yang sudah disesuaikan topik ini
- `references/struktur-paragraf.md` — Pola paragraf akademik bervariasi dengan contoh kontekstual
- `references/sitasi-guide.md` — APA 7th, IEEE, dan Vancouver

---

## ATURAN FORMAT OUTPUT

- Prosa naratif, bukan bullet list, kecuali untuk tabel perbandingan atau daftar teknis
- Tidak ada `--` atau `—` sebagai penghubung kalimat
- Sitasi default: APA 7th Edition, kecuali diminta lain
- Bahasa Indonesia baku (PUEBI), konsisten dalam penggunaan istilah teknis (pilih satu dan pertahankan: "process mining" atau "penambangan proses" — rekomendasikan tetap gunakan "process mining" sebagai istilah baku dalam bidang ini)
- Istilah teknis dari bahasa Inggris dicetak miring saat pertama kali muncul: *event log*, *process discovery*, *conformance checking*
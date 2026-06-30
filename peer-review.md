---
name: ta-peer-review
description: >
  Skill untuk melakukan peer review akademik terhadap Tugas Akhir, skripsi, atau tesis di bidang Data Science, Process Mining, dan topik terkait (Generative AI, Machine Learning, Process Discovery, Conformance Checking, event log, maintenance data). Gunakan skill ini setiap kali pengguna meminta: review bab, cek kesesuaian antar bab, evaluasi rumusan masalah vs tujuan vs hasil, review batasan penelitian, review metodologi, cek logika argumen, beri komentar kritis, penilaian kelayakan sidang, atau review keseluruhan TA. Trigger kata kunci: "review TA", "peer review", "cek kesesuaian", "review bab", "evaluasi rumusan", "kesesuaian tujuan dan hasil", "batasan penelitian", "review metodologi", "layak sidang", "komentar pembimbing", "feedback TA", "koreksi skripsi", "cek konsistensi", "review process mining", "komentar kritis".
---
 
# Skill: Peer Review Tugas Akhir — Data Science & Process Mining
 
Skill ini memandu Claude dalam melakukan peer review akademik yang kritis, konstruktif, dan terstruktur terhadap karya ilmiah — khususnya Tugas Akhir di domain Data Science, Process Mining, Generative AI, dan bidang terkait.
 
---
 
## PRINSIP PEER REVIEW
 
### Posisi Reviewer
Claude bertindak sebagai **reviewer akademik yang kompeten di bidangnya**: kritis seperti penguji sidang, konstruktif seperti pembimbing yang peduli, dan spesifik seperti kolega yang memahami domain. Bukan sekadar memberi pujian atau menyebut masalah tanpa solusi.
 
### Standar Komentar yang Baik
Setiap komentar wajib memenuhi tiga elemen:
1. **Identifikasi masalah** — apa yang bermasalah dan di mana tepatnya
2. **Penjelasan mengapa** — mengapa itu menjadi masalah secara akademik/logika
3. **Arah perbaikan** — bagaimana sebaiknya diperbaiki (tidak harus menulis ulang, cukup arahkan)
Hindari komentar yang:
- Terlalu umum: *"Tulisan ini perlu diperbaiki"*
- Tidak terarah: *"Bab II kurang lengkap"*
- Destruktif tanpa solusi: *"Metodologi ini salah"*
---
 
## DIMENSI REVIEW — CHECKLIST LENGKAP
 
### DIMENSI 1: KONSISTENSI INTERNAL (Kesesuaian Antar Komponen)
 
Ini adalah dimensi paling kritis. Periksa konsistensi di setiap pasangan komponen berikut:
 
#### 1A. Rumusan Masalah ↔ Tujuan Penelitian
- Setiap rumusan masalah harus memiliki tujuan yang menjawabnya secara langsung (1:1 mapping)
- Kata kerja tujuan harus sesuai dengan sifat pertanyaannya: "menganalisis" bukan "mengetahui" jika pertanyaannya bersifat eksplanatori
- Periksa apakah ada tujuan yang tidak memiliki rumusan masalah, atau rumusan masalah yang tidak terjawab oleh tujuan manapun
- **Flag jika:** tujuan lebih luas dari rumusan masalah (scope creep) atau lebih sempit (pertanyaan tidak sepenuhnya dijawab)
#### 1B. Tujuan Penelitian ↔ Hasil & Pembahasan
- Setiap tujuan harus terbukti tercapai atau tidak tercapai secara eksplisit di Bab IV
- Periksa apakah ada tujuan yang tidak memiliki pasangan pembahasan di Bab IV
- **Flag jika:** Bab IV membahas sesuatu yang bukan bagian dari tujuan (pembahasan melebar)
- **Flag jika:** ada tujuan yang "hilang" — tidak dibahas di Bab IV sama sekali
#### 1C. Batasan Penelitian ↔ Isi Seluruh Bab
- Batasan yang dinyatakan harus benar-benar membatasi — verifikasi apakah batasan tersebut konsisten diterapkan
- **Flag jika:** penelitian membahas sesuatu yang sudah dinyatakan sebagai batasan
- **Flag jika:** batasan terlalu longgar sehingga tidak benar-benar membatasi scope
- **Flag jika:** ada keterbatasan nyata dalam pelaksanaan penelitian yang tidak dinyatakan sebagai batasan
#### 1D. Tinjauan Pustaka ↔ Metodologi
- Teori/konsep yang digunakan dalam metodologi harus sudah dijelaskan di Bab II
- **Flag jika:** metodologi menyebut teknik atau konsep yang tidak ada di tinjauan pustaka
- **Flag jika:** ada teori di Bab II yang tidak digunakan di bagian manapun (orphan theory)
#### 1E. Metodologi ↔ Hasil
- Prosedur yang dijelaskan di Bab III harus terefleksi dalam data/output yang disajikan di Bab IV
- **Flag jika:** ada tahap metodologi yang tidak menghasilkan output yang dilaporkan
- **Flag jika:** ada hasil yang tidak bisa ditelusuri ke prosedur di Bab III (hasil "muncul tiba-tiba")
#### 1F. Kesimpulan ↔ Rumusan Masalah
- Kesimpulan harus menjawab rumusan masalah secara langsung — bukan merangkum bab
- **Flag jika:** kesimpulan berisi informasi yang tidak ada di hasil penelitian
- **Flag jika:** ada rumusan masalah yang tidak terjawab di kesimpulan
---
 
### DIMENSI 2: KUALITAS RUMUSAN MASALAH
 
Evaluasi berdasarkan kriteria berikut:
- **Spesifisitas**: apakah pertanyaan cukup tajam untuk bisa dijawab secara empiris?
- **Keterjawaban**: bisakah pertanyaan ini dijawab dengan data/metode yang digunakan?
- **Relevansi gap**: apakah pertanyaan ini lahir dari gap yang sudah diidentifikasi di latar belakang?
- **Lingkup**: apakah terlalu luas (tidak bisa dijawab tuntas) atau terlalu sempit (trivial)?
Untuk domain Process Mining, pertanyaan yang baik biasanya menyentuh: (a) karakteristik data/masalah, (b) pendekatan/teknik yang digunakan, (c) evaluasi/perbandingan hasil.
 
---
 
### DIMENSI 3: KUALITAS TINJAUAN PUSTAKA (BAB II)
 
Periksa aspek berikut:
 
#### Kelengkapan Konsep
- Apakah semua konsep yang digunakan dalam metodologi sudah dijelaskan?
- Untuk Process Mining: apakah event log, algoritma discovery yang digunakan, dan metrik evaluasi sudah didefinisikan?
- Untuk Generative AI: apakah cara kerja LLM yang relevan sudah dijelaskan dengan tepat?
#### Kedalaman Sintesis
- Apakah Bab II sekadar mendefinisikan satu per satu, atau ada sintesis antar konsep?
- Apakah penulis menunjukkan posisinya terhadap perdebatan/gap dalam literatur?
#### Relevansi Sumber
- Apakah sumber yang dikutip relevan dengan topik secara spesifik?
- Apakah ada ketergantungan berlebihan pada satu sumber (mis. hanya Van der Aalst untuk semua hal tentang process mining)?
- Apakah ada sumber yang terlalu lama (>10 tahun) pada topik yang berkembang cepat seperti LLM?
#### Gap Statement
- Apakah akhir Bab II secara eksplisit atau implisit menyatakan gap yang diisi penelitian ini?
---
 
### DIMENSI 4: KUALITAS METODOLOGI (BAB III)
 
Periksa aspek berikut:
 
#### Justifikasi Pilihan
- Apakah setiap pilihan metodologi (algoritma, teknik, tools) disertai alasan yang substantif?
- "Karena paling populer" atau "karena banyak digunakan" bukan justifikasi yang cukup
- Untuk Process Mining: apakah pilihan algoritma discovery dijustifikasi berdasarkan karakteristik data?
#### Kelengkapan Prosedur
- Apakah prosedur cukup detail untuk dapat direplikasi?
- Apakah ada tahap penting yang tidak dijelaskan (mis. bagaimana event log difilter, bagaimana prompt dirancang)?
#### Kesesuaian Metode dengan Tujuan
- Apakah metode yang dipilih memang mampu menjawab rumusan masalah yang ada?
- Untuk topik Generative AI + Process Mining: apakah peran LLM dalam pipeline dijelaskan secara teknis, bukan hanya konseptual?
#### Evaluasi dan Metrik
- Apakah metrik evaluasi yang digunakan sesuai dengan jenis output yang dievaluasi?
- Untuk Process Mining: apakah keempat dimensi (fitness, precision, simplicity, generalization) atau subset yang dipilih dijustifikasi?
- Apakah ada baseline perbandingan yang jelas?
---
 
### DIMENSI 5: KUALITAS HASIL & PEMBAHASAN (BAB IV)
 
#### Penyajian Hasil
- Apakah hasil disajikan secara sistematis mengikuti urutan tujuan penelitian?
- Apakah setiap tabel/gambar diinterpretasikan dalam teks (bukan hanya ditampilkan)?
- Apakah ada anomali dalam data yang diakui dan dibahas?
#### Kedalaman Pembahasan
- Apakah pembahasan menghubungkan temuan dengan teori/literatur dari Bab II?
- Apakah hanya mendeskripsikan hasil, atau juga menjelaskan mengapa hasil itu terjadi?
- Apakah keterbatasan temuan diakui secara jujur?
#### Klaim yang Proporsional
- Apakah klaim yang dibuat didukung oleh data yang cukup?
- **Flag jika:** klaim generalisasi terlalu luas dari data yang terbatas
- **Flag jika:** hasil negatif/mengecewakan disembunyikan atau diminimalkan
---
 
### DIMENSI 6: KUALITAS KESIMPULAN & SARAN (BAB V)
 
#### Kesimpulan
- Apakah menjawab rumusan masalah secara langsung dan eksplisit?
- Apakah ada informasi baru di kesimpulan yang tidak ada di hasil? (tidak boleh)
- Apakah proporsional — tidak terlalu singkat sehingga tidak informatif, tidak terlalu panjang sehingga mengulang Bab IV?
#### Saran
- Apakah saran didasarkan pada temuan dan keterbatasan penelitian ini?
- Apakah dibedakan antara saran teoretis (riset lanjutan) dan saran praktis?
- Apakah saran cukup spesifik dan actionable?
---
 
### DIMENSI 7: KUALITAS BATASAN PENELITIAN
 
Batasan yang baik:
- Jelas membatasi scope, bukan sekadar disclaimer
- Spesifik: bukan "data terbatas" tapi "data yang digunakan hanya mencakup periode X pada sistem Y"
- Tidak bertentangan dengan yang dilakukan dalam penelitian
- Mencerminkan keterbatasan nyata, bukan digunakan untuk menghindari ekspektasi yang seharusnya dipenuhi
**Flag jika batasan digunakan untuk "kabur" dari kelemahan metodologi yang sebenarnya bisa diatasi.**
 
---
 
### DIMENSI 8: DOMAIN-SPESIFIK — PROCESS MINING & DATA SCIENCE
 
Ini adalah layer tambahan untuk topik yang berada di domain ini:
 
#### Untuk Process Mining
- Apakah definisi event log (case ID, activity, timestamp) sudah benar dan konsisten digunakan?
- Apakah algoritma discovery yang dipilih sesuai dengan karakteristik data (noisy, incomplete, low frequency)?
- Apakah evaluasi menggunakan metrik yang tepat dan tidak hanya mengandalkan visual model?
- Apakah perbedaan antara discovered model dan normative model dipahami dengan benar?
- Apakah masalah flower model / spaghetti process diidentifikasi dan diatasi dengan cara yang logis?
#### Untuk Generative AI / LLM
- Apakah peran LLM dalam pipeline didefinisikan dengan tepat (bukan sekadar "menggunakan AI")?
- Apakah prompt engineering dijelaskan sebagai bagian dari metodologi?
- Apakah keterbatasan LLM (halusinasi, domain-specificity, biaya) diakui?
- Apakah ada validasi terhadap output LLM sebelum digunakan dalam tahap selanjutnya?
#### Untuk Data Science (Umum)
- Apakah preprocessing data dijelaskan secara lengkap?
- Apakah ada potensi data leakage yang tidak diantisipasi?
- Apakah hasil eksperimen bisa direplikasi berdasarkan prosedur yang ditulis?
- Apakah interpretasi model (jika ada) dilakukan dengan hati-hati?
---
 
## FORMAT OUTPUT PEER REVIEW
 
### Saat Mereview Satu Bab atau Bagian
 
Gunakan struktur berikut (dalam prosa, bukan bullet list kecuali untuk temuan spesifik):
 
```
RINGKASAN PENILAIAN
[1–2 paragraf: gambaran umum kualitas bagian ini, kekuatan utamanya, dan isu paling kritis]
 
TEMUAN KRITIS (harus diperbaiki sebelum sidang)
[Temuan yang jika tidak diperbaiki akan menjadi pertanyaan penguji yang sulit dijawab]
 
TEMUAN MAYOR (penting diperbaiki, berpengaruh pada kualitas)
[Isu substansial yang mempengaruhi validitas atau koherensi argumen]
 
TEMUAN MINOR (disarankan diperbaiki, tidak kritis)
[Masalah redaksi, kurang presisi, atau hal-hal yang menguatkan jika diperbaiki]
 
PERTANYAAN PENGUJI YANG MUNGKIN MUNCUL
[Simulasi 3–5 pertanyaan yang kemungkinan diajukan penguji berdasarkan temuan di atas]
```
 
### Saat Mereview Kesesuaian Antar Komponen
 
Gunakan tabel konsistensi diikuti narasi analisis:
 
```
MATRIKS KONSISTENSI
[Tabel: Rumusan Masalah | Tujuan | Dibahas di Bab IV | Dijawab di Kesimpulan | Status]
 
ANALISIS KESENJANGAN
[Narasi tentang gap yang ditemukan dan implikasinya]
 
REKOMENDASI PRIORITAS
[Urutan perbaikan berdasarkan dampaknya terhadap koherensi TA]
```
 
### Saat Mereview Keseluruhan TA
 
```
PENILAIAN KELAYAKAN SIDANG
[Verdict: Layak / Layak dengan Revisi Minor / Perlu Revisi Mayor / Belum Layak]
[Penjelasan singkat alasan verdict]
 
PROFIL KEKUATAN
[Apa yang sudah baik dan perlu dipertahankan]
 
ISU LINTAS BAB
[Masalah yang muncul di lebih dari satu bab atau mempengaruhi koherensi keseluruhan]
 
PRIORITAS PERBAIKAN (urut dari paling kritis)
1. [isu paling kritis]
2. ...
 
SIMULASI SIDANG
[5–8 pertanyaan penguji yang paling mungkin muncul, disertai hint jawaban]
```
 
---
 
## PANDUAN KOMENTAR PER KONDISI
 
### Jika Rumusan Masalah Tidak Terjawab di Hasil
> *"Rumusan masalah ke-[X] menanyakan tentang [Y], namun di Bab IV tidak ditemukan bagian yang secara eksplisit menjawab pertanyaan ini. Pembahasan tentang [Z] di halaman [n] mendekati, tetapi tidak secara langsung menjawab pertanyaan yang diajukan. Disarankan untuk menambahkan subbab atau paragraf khusus yang mengintegrasikan temuan-temuan tersebut menjadi jawaban yang kohesif terhadap rumusan masalah ke-[X]."*
 
### Jika Tujuan Terlalu Luas dari Rumusan Masalah
> *"Tujuan penelitian ke-[X] menyatakan ingin '[tujuan]', namun rumusan masalah yang ada hanya menanyakan '[rumusan]'. Ada scope yang ada di tujuan tetapi tidak dicakup oleh pertanyaan penelitian, yang berarti tidak ada mekanisme metodologis untuk mencapainya. Disarankan untuk menyesuaikan salah satunya: sempitkan tujuan agar selaras dengan rumusan masalah, atau tambahkan rumusan masalah baru jika scope yang lebih luas memang disengaja."*
 
### Jika Batasan Bertentangan dengan Isi
> *"Di halaman [n], penelitian menyatakan membatasi diri pada [batasan X]. Namun di Bab [IV/III], penelitian justru [melakukan Y yang bertentangan dengan batasan X]. Inkonsistensi ini akan menjadi pertanyaan penguji yang sulit dijawab. Pilihannya: hapus batasan tersebut jika memang tidak benar-benar membatasi, atau sesuaikan isi agar benar-benar mengikuti batasan yang dinyatakan."*
 
### Jika Tinjauan Pustaka Tidak Mendukung Metodologi
> *"Metodologi di Bab III menggunakan [teknik/konsep X], namun konsep ini tidak dibahas di Bab II. Ini berarti pembaca tidak memiliki fondasi teoretis untuk mengevaluasi apakah penggunaan [X] dalam penelitian ini sudah tepat. Tambahkan subbab atau paragraf di Bab II yang menjelaskan [X] dan justifikasi penggunaannya."*
 
### Jika Klaim Tidak Proporsional dengan Data
> *"Pernyataan '[klaim]' di halaman [n] merupakan generalisasi yang melebihi apa yang bisa disimpulkan dari data yang ada. Data penelitian ini hanya mencakup [scope data], sehingga klaim yang lebih tepat adalah '[versi yang lebih terbatas]. Generalisasi yang berlebihan akan dipertanyakan penguji dan melemahkan kredibilitas temuan yang sebetulnya sudah cukup solid."*
 
### Jika Ada Orphan Theory di Bab II
> *"Konsep [X] yang dibahas di halaman [n] Bab II tidak digunakan di bagian manapun dalam metodologi atau pembahasan. Kehadiran konsep tanpa penggunaan mengindikasikan bahwa Bab II belum sepenuhnya terintegrasi dengan penelitian. Pertimbangkan untuk: (a) menghapus subbab tersebut jika memang tidak relevan, atau (b) menunjukkan secara eksplisit relevansinya di metodologi atau pembahasan."*
 
---
 
## SIMULASI PERTANYAAN PENGUJI
 
Gunakan referensi berikut untuk mengantisipasi pertanyaan sidang berdasarkan isu yang ditemukan:
 
### Pertanyaan tentang Metodologi
- "Mengapa Anda memilih [algoritma X] dan bukan [Y]? Apa kelebihan X untuk kasus ini?"
- "Bagaimana Anda memastikan bahwa hasil abstraksi LLM akurat dan tidak hallucinating?"
- "Kalau data maintenance dari industri lain, apakah pipeline ini masih berlaku?"
- "Apa yang Anda lakukan jika LLM menghasilkan abstraksi yang salah untuk aktivitas teknis yang sangat spesifik?"
- "Bagaimana Anda menentukan threshold untuk menggabungkan aktivitas dalam proses abstraksi?"
### Pertanyaan tentang Hasil
- "Nilai fitness meningkat atau menurun setelah intervensi LLM? Bagaimana Anda menjelaskan hasilnya?"
- "Apa yang dimaksud dengan 'model lebih baik' dalam konteks penelitian ini? Siapa yang menilainya?"
- "Apakah perbedaan metrik antara baseline dan pendekatan yang diusulkan secara statistik signifikan?"
- "Bisakah model yang dihasilkan benar-benar digunakan oleh praktisi maintenance? Sudah divalidasi dengan domain expert?"
### Pertanyaan tentang Kontribusi
- "Apa yang membedakan penelitian ini dari penelitian serupa yang sudah ada?"
- "Apakah kontribusi utama penelitian ini ada di pipeline-nya, di temuan empirisnya, atau di keduanya?"
- "Bagaimana penelitian ini bisa diimplementasikan secara praktis di industri?"
### Pertanyaan tentang Batasan
- "Seberapa besar event log yang diuji? Apakah cukup representatif?"
- "Apakah penelitian ini hanya berlaku untuk [jenis data/domain tertentu]?"
- "Apa yang akan Anda lakukan berbeda jika mengulang penelitian ini?"
---
 
## SKALA PENILAIAN
 
Gunakan skala berikut saat diminta memberikan rating:
 
| Level | Label | Deskripsi |
|---|---|---|
| 5 | Sangat Baik | Memenuhi standar publikasi; tidak ada isu mayor |
| 4 | Baik | Solid dengan beberapa isu minor yang mudah diperbaiki |
| 3 | Cukup | Ada isu mayor yang perlu diperbaiki sebelum sidang |
| 2 | Kurang | Ada isu fundamental yang memerlukan revisi substansial |
| 1 | Tidak Memadai | Perlu pengerjaan ulang yang signifikan |
 
Dimensi yang dinilai:
- Konsistensi Internal (Rumusan ↔ Tujuan ↔ Hasil ↔ Kesimpulan)
- Kualitas Tinjauan Pustaka
- Ketepatan Metodologi
- Kedalaman Pembahasan
- Kualitas Kesimpulan & Saran
- Kesesuaian Batasan
- Kontribusi Keilmuan
---
 
## REFERENSI TAMBAHAN
 
- `references/checklist-konsistensi.md` — Checklist lengkap per pasangan komponen
- `references/pertanyaan-penguji.md` — Bank pertanyaan penguji berdasarkan topik dan isu umum
- `references/rubrik-penilaian.md` — Rubrik detail per dimensi dengan indikator spesifik
- `references/contoh-komentar.md` — Contoh komentar reviewer untuk berbagai jenis isu
 
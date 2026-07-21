# Speaker Notes — Presentasi Sidang / Seminar

**Judul:** Pemanfaatan Generative AI untuk Process Discovery pada Data Operasional Pemeliharaan Perusahaan Listrik  
**Presenter:** Sakha Wibisono (103012480032)  
**Dokumen acuan angka:** `build/main.pdf` (skripsi) · struktur slide: `1_merged.pdf`

Cara pakai: salin tiap blok *Speaker Notes* ke Notes panel PowerPoint/Google Slides pada slide yang sesuai.  
**Durasi acuan total: ±18–20 menit** (tanpa sesi Q&A). Bicara dengan tempo tenang; jika terlalu cepat, gunakan kalimat dalam tanda kurung siku `[...]` sebagai opsi dipersingkat.

---

## Slide 1 — Judul

**Durasi acuan:** ±1 menit

**Speaker Notes:**

Assalamu’alaikum warahmatullahi wabarakatuh / Selamat pagi, Bapak/Ibu Dewan Penguji dan hadirin yang saya hormati.

Perkenalkan, saya Sakha Wibisono, mahasiswa Program Studi Sarjana Informatika, Fakultas Informatika, Telkom University, dengan NIM 103012480032. Pada kesempatan ini saya akan mempresentasikan penelitian skripsi berjudul *Pemanfaatan Generative AI untuk Process Discovery pada Data Operasional Pemeliharaan Perusahaan Listrik*, di bawah bimbingan Ibu Angelina Prima Kurniati, S.T., M.T., Ph.D.

Secara posisi keilmuan, penelitian ini berada di irisan *business process management* dan *process mining*. Inti gagasannya: memanfaatkan *large language model* untuk melakukan *semantic abstraction* atas label aktivitas pemeliharaan yang ditulis bebas, lalu membangun dan membandingkan dua model proses—*as-is* tanpa anotasi dan *enriched AI* setelah anotasi—melalui *process discovery* serta *conformance checking*.

Dalam ±18–20 menit ke depan, saya akan memaparkan latar belakang dan *gap*, rancangan sistem, hasil komparasi model, temuan operasional, serta kesimpulan.

---

## Slide 2 — Latar Belakang

**Durasi acuan:** ±1 menit 30 detik

**Speaker Notes:**

Pemeliharaan pembangkit listrik merupakan proses bisnis kritis untuk menjaga *reliability* aset, ketersediaan unit, dan kontinuitas operasi. Transformasi digital di sektor ketenagalistrikan mendorong pemanfaatan data operasional—bukan hanya untuk pelaporan, tetapi juga untuk pengambilan keputusan teknis yang berbasis bukti.

Catatan operasional berupa job card dan Work Breakdown Structure pada dasarnya adalah jejak eksekusi proses nyata. Karena itu, data tersebut cocok dianalisis dengan *process mining*, khususnya *process discovery*, untuk mengungkap *control-flow* pemeliharaan apa adanya.

Namun ada hambatan praktis yang signifikan. Deskripsi aktivitas ditulis bebas oleh teknisi, sehingga muncul *label heterogeneity*: satu tindakan semantik yang sama tercatat dengan banyak variasi teks. Ketika discovery dijalankan langsung pada label mentah, model yang terbentuk cenderung menjadi *spaghetti model*—padat, saling silang, dan sulit dibaca. Model seperti ini lemah sebagai dasar komunikasi antar-stakeholder maupun perumusan perbaikan proses.

Di sinilah peluang Generative AI. LLM dapat membantu menstandarkan *activity labels* ke kategori yang konsisten, sehingga *event log* merepresentasikan peran aktivitas dalam proses bisnis, bukan sekadar ejaan teknisi. Harapannya, model proses menjadi lebih ringkas, *interpretable*, dan bermanfaat operasional.

---

## Slide 3 — Gap Penelitian

**Durasi acuan:** ±1 menit 30 detik

**Speaker Notes:**

Sejumlah penelitian terkait sudah membawa LLM atau *supervised learning* ke ranah *process mining*, tetapi fokusnya belum sama dengan kebutuhan penelitian ini.

Norouzifar dan kawan-kawan memanfaatkan LLM untuk mengekstrak *constraints* dari teks aturan bisnis. Tax dan kawan-kawan menekankan *event abstraction* melalui pendekatan *supervised learning*, yang biasanya membutuhkan data berlabel cukup besar. Rebmann dan kawan-kawan mengevaluasi kapabilitas LLM lintas *benchmark*, lebih pada asesmen kemampuan model secara umum.

Dari tinjauan tersebut, masih terbuka ruang riset yang belum terisi secara utuh. Belum banyak studi yang secara eksplisit: pertama, menstandarkan label aktivitas pemeliharaan berbasis *taxonomy boundary* langsung pada *real industrial data*; kedua, membandingkan model *as-is* versus *enriched AI* pada *event log* yang sama; ketiga, mengevaluasi keduanya dengan empat dimensi *conformance checking* secara lengkap; dan keempat, menurunkan temuan operasional yang *actionable*—misalnya *bottleneck* dan anomali urutan kerja.

Itulah *research gap* yang kami isi: *semantic abstraction* berbasis 12 kategori, komparasi model yang adil, serta manfaat bagi tata kelola proses pemeliharaan.

---

## Slide 4 — Posisi Penelitian

**Durasi acuan:** ±1 menit 15 detik

**Speaker Notes:**

Untuk memperjelas kontribusi, posisi penelitian digambarkan sebagai dua jalur membangun *process model* dari data yang sama.

Jalur konvensional memakai *raw activity labels* apa adanya. Karena ruang label sangat besar akibat variasi penulisan, *process discovery* menghasilkan model yang merekam keragaman teks, bukan semata keragaman perilaku proses. Akibatnya, *main process behavior*—pola umum alur kerja—sulit dibedakan dari noise label.

Jalur usulan menempatkan *LLM-based annotation* sebagai tahap pra-discovery. Setiap deskripsi aktivitas dipetakan ke salah satu dari dua belas *action types* sebelum model dibangun. Dengan demikian, *enriched event log* bekerja pada tingkat abstraksi yang lebih sesuai untuk analisis *end-to-end business process*.

Perbedaan keduanya bukan sekadar “ada AI atau tidak”, melainkan perbedaan *granularity* representasi proses: dari level ejaan teknis ke level kategori tindakan bisnis.

---

## Slide 5 — Rumusan Masalah

**Durasi acuan:** ±1 menit 15 detik

**Speaker Notes:**

Penelitian diarahkan oleh tiga rumusan masalah yang saling terkait.

RM1 menanyakan bagaimana Generative AI dapat dimanfaatkan untuk menstandarkan ragam label aktivitas pemeliharaan menjadi kategori yang konsisten. Ini menyangkut *semantic labeling*, kualitas anotasi, dan peran *taxonomy-constrained abstraction* agar keluaran model tidak liar.

RM2 menanyakan bagaimana bentuk model proses yang dihasilkan ketika *process discovery* dijalankan pada *event log as-is* dibandingkan dengan *event log enriched*. Fokusnya pada perbedaan struktur *control-flow*, ukuran Petri net, dan keterbacaan model.

RM3 menguji apakah penyeragaman label berbasis LLM benar-benar menghasilkan model yang lebih ringkas dibanding metode tanpa anotasi. Pengujiannya kuantitatif: melalui metrik *fitness*, *precision*, *generalization*, *simplicity*, serta indikator struktural seperti jumlah *places*, *transitions*, dan *trace variants*.

Ketiga RM ini menjadi benang merah dari metodologi hingga pembahasan hasil.

---

## Slide 6 — Rancangan Sistem: Event Log Data

**Durasi acuan:** ±1 menit 15 detik

**Speaker Notes:**

Data penelitian berasal dari kegiatan *overhaul* pemeliharaan di PLTD Titikuning. Sumber utamanya adalah WBS dan job card yang mencatat rangkaian pekerjaan pada setiap unit serta komponen, kemudian diekspor menjadi *event log* berformat CSV.

Dalam kerangka *process mining*, setiap pekerjaan pemeliharaan diperlakukan sebagai *case*; setiap baris aktivitas sebagai *event*. Atribut inti yang dibutuhkan meliputi *case id*, *activity*, dan *timestamp*. Tanpa ketiga elemen ini, discovery dan *conformance checking* tidak dapat dijalankan secara valid.

Perlu ditekankan bahwa kualitas hasil sangat bergantung pada kualitas log. Karena itu, tahap preprocessing—termasuk penanganan *case id* yang tidak lengkap, pemecahan aktivitas majemuk, dan imputasi *timestamp*—menjadi fondasi sebelum anotasi LLM maupun discovery dilakukan.

---

## Slide 7 — Taxonomy Boundary: 12 Kategori

**Durasi acuan:** ±1 menit 30 detik

**Speaker Notes:**

Agar LLM tidak bebas menciptakan label baru, kami menerapkan *taxonomy boundary*: ruang keluaran dibatasi pada dua belas kategori tindakan yang dirancang sesuai karakteristik pekerjaan pemeliharaan.

Secara logika proses bisnis, kategori tersebut dapat dikelompokkan. Ada aktivitas pendukung awal seperti SAFETY_INDUCTION. Ada tahap diagnosis: CLEANING, INSPECTION, dan MEASUREMENT. Ada tahap intervensi: DISASSEMBLY, REPAIR, REPLACEMENT, ASSEMBLY, ADJUSTMENT, dan LUBRICATION. Ada tahap verifikasi akhir: TESTING. Serta OTHER untuk residual yang tidak masuk kelas utama.

Pendekatan ini penting secara metodologis. Abstraksi bersifat *controlled vocabulary*, bukan *open-ended generation*. Dengan batasan taksonomi, *semantic abstraction* tetap terikat domain, hasil antar-*case* menjadi sebanding, dan model *enriched* dapat dievaluasi secara adil terhadap baseline *as-is*.

---

## Slide 8 — Alur Penelitian

**Durasi acuan:** ±1 menit 45 detik

**Speaker Notes:**

Pipeline penelitian mengikuti siklus *process mining* yang standar, dengan tambahan tahap anotasi LLM.

Tahap pertama adalah *data ingestion* dan *preprocessing*. Di sini dilakukan pembersihan log, *compound activity splitting*—memecah satu baris pekerjaan majemuk menjadi beberapa *event*—serta *timestamp imputation* agar urutan waktu dapat dianalisis. Dari preprocessing ini diperoleh 52 *cases*; *event* naik dari 255 pada log *as-is* menjadi 308 pada log *enriched*, dengan 110 *timestamp* terimputasi.

Tahap kedua adalah *annotation* LLM. Deskripsi aktivitas dipetakan ke 12 kategori dalam *taxonomy boundary*, menghasilkan atribut `action_type` pada *enriched event log*.

Tahap ketiga adalah *process discovery* menggunakan Inductive Miner infrequent—IMf—dengan *noise threshold* 0,2. IMf dipilih karena log pemeliharaan memuat perilaku jarang dan variasi tinggi; filter *infrequent* membantu menekan *noise* tanpa mengorbankan struktur utama proses.

Tahap keempat adalah *conformance checking*: model dievaluasi terhadap *event log*-nya masing-masing pada empat metrik—*fitness*, *precision*, *generalization*, dan *simplicity*—lalu dilanjutkan interpretasi operasional.

---

## Slide 9 — Hasil: As-Is vs Enriched AI (Ukuran Log)

**Durasi acuan:** ±1 menit 30 detik

**Speaker Notes:**

Hasil pertama yang perlu dilihat adalah perbandingan ukuran log dan ruang aktivitas.

Kedua skenario memakai jumlah kasus yang sama: 52 *cases*. Jadi komparasi dilakukan pada populasi kasus yang setara.

Pada baseline *as-is*, terdapat 255 *events* dengan 112 *unique activities*. Angka 112 ini mencerminkan betapa beragamnya penulisan teknisi ketika label tidak distandarkan.

Pada *enriched AI*, jumlah *events* meningkat menjadi 308. Kenaikan ini bukan karena kasus baru, melainkan karena *compound activity splitting*: satu catatan majemuk dipecah menjadi beberapa *event* berlabel tunggal. Namun *unique activities* turun drastis dari 112 menjadi 12 *action types*.

Poin analitisnya: volume *event* bertambah, tetapi ruang label menyusut tajam. Itu indikasi bahwa abstraksi semantik mengubah *granularity* representasi proses ke tingkat yang lebih homogen—kondisi yang biasanya lebih baik untuk membaca pola proses bisnis.

---

## Slide 10 — Bentuk Model As-Is

**Durasi acuan:** ±1 menit 15 detik

**Speaker Notes:**

Jika dilihat dari bentuk model, perbedaan semakin jelas.

Model *as-is* dibangun langsung dari 112 label mentah tanpa standarisasi. Petri net yang dihasilkan memuat 81 *places*, 119 *transitions*, dan 36 *trace variants*. Visualisasinya memperlihatkan struktur padat dan saling silang—ciri khas *spaghetti model*.

Secara teoritis, model ini bisa memiliki *fitness* tinggi karena hampir meniru perilaku historis secara rinci. Namun dari sudut pandang *process analyst* dan pemilik proses, model semacam itu sulit dipakai untuk memahami *happy path*, menyepakati SOP, atau menyasar perbaikan. Keterbacaan rendah justru menjadi masalah bisnis, meski kecocokan *replay* tampak baik.

Dengan kata lain, *as-is* unggul sebagai “foto mentah” data, tetapi lemah sebagai model proses yang komunikatif.

---

## Slide 11 — Bentuk Model Enriched AI

**Durasi acuan:** ±1 menit 20 detik

**Speaker Notes:**

Sebaliknya, model *enriched AI* dibangun dari 12 kategori `action_type` hasil abstraksi semantik.

Struktur model menyusut menjadi 31 *places*, 43 *transitions*, dan 30 *trace variants*. Reduksi *places* mencapai 61,73 persen; *transitions* turun sekitar 63,87 persen. Ini bukti kuantitatif bahwa *semantic abstraction* berdampak langsung pada kompleksitas *control-flow*.

Secara kualitatif, alur pemeliharaan menjadi terbaca: dimulai dari pengarahan keselamatan, dilanjutkan diagnosis—*cleaning*, *inspection*, *measurement*—lalu intervensi teknis, dan ditutup dengan *testing* sebagai verifikasi. *Process discovery* kini menangkap peran aktivitas dalam proses bisnis, bukan terjebak pada variasi ejaan.

Inilah jawaban praktis atas RM2: bentuk model *enriched* jauh lebih ringkas dan interpretable dibanding *as-is*.

---

## Slide 12 — Conformance Checking

**Durasi acuan:** ±2 menit

**Speaker Notes:**

Untuk menjawab RM3 secara kuantitatif, kedua model dievaluasi dengan empat dimensi *conformance checking*.

*Fitness* mengukur seberapa baik model dapat mereplay jejak aktual. *As-is* mencapai 0,9833; *enriched* 0,9570. Keduanya tinggi. Penurunan kecil sebesar 0,0263 masih dapat diterima, karena abstraksi memang mengorbankan sebagian detail label.

*Precision* turun lebih tajam: dari 0,8716 ke 0,5063. Artinya model *enriched* mengizinkan lebih banyak perilaku yang secara teori mungkin terjadi. Ini konsekuensi wajar dari penggabungan banyak label mentah ke kategori yang lebih abstrak.

Sebaliknya, *generalization* melonjak dari 0,0807 ke 0,7079—kenaikan 0,6272, atau lebih dari delapan kali lipat. Ini temuan kunci: model *as-is* cenderung *overfitting* terhadap *trace* historis, sedangkan model *enriched* lebih mampu mengakomodasi variasi proses yang wajar di masa depan.

*Simplicity* PM4Py sedikit menurun dari 0,7246 ke 0,6727. Metrik ini perlu dibaca hati-hati karena sensitif terhadap derajat keterhubungan lokal antar simpul, bukan semata keterbacaan bagi manusia. Keterbacaan justru lebih tercermin dari penyusutan ukuran model dan pengurangan keragaman label.

Secara keseluruhan, muncul *trade-off* klasik dalam *process mining*: sedikit mengorbankan *precision* demi *generalization* dan interpretabilitas proses. Untuk tujuan analisis dan perbaikan proses bisnis, *trade-off* ini dinilai menguntungkan.

---

## Slide 13 — Manfaat Operasional & Bottleneck

**Durasi acuan:** ±2 menit

**Speaker Notes:**

Manfaat penelitian tidak berhenti pada kualitas model. *Enriched event log* membuka analisis kinerja dan tata kelola proses.

Pertama, *volume bottleneck*. CLEANING menyerap total waktu kerja terbesar—pada slide dibulatkan 376 jam; pada dokumen skripsi 375,96 jam kerja efektif—karena frekuensinya tinggi. Artinya, inisiatif efisiensi pada pembersihan—standarisasi alat, material, dan prosedur—berpotensi memberi dampak paling luas secara agregat.

Kedua, *duration bottleneck* per kejadian. REPAIR dan ADJUSTMENT paling lama secara rata-rata—sekitar 32,00 jam dan 21,56 jam—meski frekuensinya jarang. Ini menuntut perencanaan berbeda: kesiapan suku cadang, penjadwalan tenaga ahli, dan mitigasi waktu tunggu sebelum intervensi.

Ketiga, anomali urutan proses. Sebanyak 8 dari 52 *cases* melakukan pembongkaran atau *replacement* tanpa *inspection* maupun *measurement* pendahulu. Pola ini menyimpang dari prinsip *diagnose-then-intervene*. Rekomendasi operasionalnya jelas: wajibkan dokumentasi diagnosis sebelum intervensi struktural.

Temuan-temuan ini menunjukkan bahwa *process mining* berbasis abstraksi semantik tidak hanya menyederhanakan model, tetapi juga menghasilkan insight yang dapat ditindaklanjuti oleh manajemen pemeliharaan.

---

## Slide 14 — Kesimpulan & Saran

**Durasi acuan:** ±1 menit 30 detik

**Speaker Notes:**

Sebagai penutup, saya ringkas tiga kesimpulan utama yang menjawab rumusan masalah.

Pertama, terkait RM1: Generative AI dengan *taxonomy boundary* mampu menstandarkan 308 *events* menjadi 12 *action types* melalui *semantic abstraction*, sehingga label aktivitas menjadi konsisten di seluruh kasus.

Kedua, terkait RM2: bentuk model *as-is* dan *enriched* kontras secara struktural—81 *places* dan 119 *transitions* pada *as-is*, versus 31 *places* dan 43 *transitions* pada *enriched AI*. Model *enriched* menampilkan alur pemeliharaan yang lebih terbaca.

Ketiga, terkait RM3: penyeragaman label berbasis LLM menghasilkan model yang lebih ringkas dan jauh lebih generalizable—*generalization* meningkat lebih dari delapan kali lipat—dengan *fitness* yang tetap stabil di sekitar 0,957.

Saran pengembangan ke depan meliputi: validasi anotasi secara kuantitatif oleh ahli domain, analisis DFG hingga tingkat komponen agar *rework* sejati dapat dibedakan dari diagnosis multi-komponen, serta uji pada dataset pemeliharaan yang lebih besar dan lintas lokasi agar generalitas temuan semakin kuat.

---

## Slide 15 — Q&A

**Durasi acuan:** ±30–45 detik (penutup; Q&A terpisah)

**Speaker Notes:**

Demikian pemaparan penelitian saya. Terima kasih atas perhatian Bapak/Ibu Dewan Penguji dan hadirin. Saya siap menerima pertanyaan, kritik, dan masukan untuk penyempurnaan.

*Cadangan jawaban jika ditanya:*

- **Mengapa precision turun?** Karena abstraksi menggabungkan banyak label ke kategori yang lebih umum, sehingga ruang perilaku yang diizinkan model membesar. Model menjadi kurang “ketat”, tetapi lebih mampu menggeneralisasi.
- **Mengapa event bertambah dari 255 ke 308?** Karena *compound activity splitting*: satu baris pekerjaan majemuk dipecah menjadi beberapa *event* berlabel tunggal agar semantik tindakan tidak bercampur.
- **Apakah skor confidence LLM menjamin kebenaran?** Tidak. *Confidence* mencerminkan keyakinan model, bukan kebenaran mutlak domain. Validasi ahli pemeliharaan tetap diperlukan.
- **Mengapa memilih IMf, bukan Alpha Miner atau Heuristic Miner?** IMf lebih cocok untuk log dengan *infrequent behavior* dan menghasilkan Petri net yang natural untuk *conformance checking* lanjutan.
- **Apakah penurunan simplicity bertentangan dengan klaim model lebih ringkas?** Tidak. *Simplicity* PM4Py mengukur kepadatan koneksi lokal, sedangkan keterbacaan manusia lebih tercermin dari reduksi *places*, *transitions*, dan keragaman label.
- **Apa rekomendasi paling prioritas ke operasi?** Dua arah: efisiensi volume pada CLEANING, dan penguatan disiplin *diagnose-before-intervene* untuk menekan intervensi tanpa pemeriksaan.

Wassalamu’alaikum warahmatullahi wabarakatuh / Terima kasih.

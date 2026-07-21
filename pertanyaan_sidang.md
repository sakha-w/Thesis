# Bank Pertanyaan Akademis Sidang

**Judul penelitian:** Pemanfaatan Generative AI untuk Process Discovery pada Data Operasional Pemeliharaan Perusahaan Listrik  
**Acuan:** `build/main.pdf` (Bab I–V, abstrak)  
**Cara pakai:** latih jawaban lisan 1–2 menit per pertanyaan inti; siapkan contoh angka dari Bab IV.

Legenda tingkat:
- ★★☆ = dasar / definisi
- ★★★ = analisis / pembelaan hasil
- ★★★★ = kritis / keterbatasan / alternatif metodologis

---

## A. Konsep Dasar Process Mining & BPM

### A1. ★★☆
Apa perbedaan *process discovery*, *conformance checking*, dan *enhancement* dalam *process mining*? Penelitian Anda menekankan yang mana?

**Arah jawaban:** Discovery membangun model dari *event log*; conformance membandingkan model dengan log; enhancement menganalisis kinerja/perbaikan. Penelitian ini fokus discovery + conformance, lalu interpretasi operasional (mendekati enhancement).

### A2. ★★☆
Apa yang dimaksud *event log*, *case*, *event*, dan *trace*? Berikan contoh dari data PLTD Anda.

**Arah jawaban:** *Case* = satu pekerjaan/overhaul (mis. WT…); *event* = satu aktivitas bertanda waktu; *trace* = urutan *event* dalam satu *case*. Anda punya 52 *cases*, 255/308 *events*.

### A3. ★★★
Mengapa *label heterogeneity* pada deskripsi teknisi menghasilkan *spaghetti model*?

**Arah jawaban:** Algoritma discovery memperlakukan string berbeda sebagai aktivitas berbeda, sehingga ruang aktivitas membengkak (112 label), *control-flow* menjadi padat/saling silang, meski makna semantiknya serupa.

### A4. ★★★
Apa bedanya *event abstraction* / *semantic abstraction* dengan sekadar *filtering noise* pada DFG?

**Arah jawaban:** Filtering membuang perilaku jarang; abstraksi mengubah *granularity* label ke tingkat semantik yang lebih bermakna. Penelitian Anda melakukan abstraksi berbatas taksonomi *sebelum* discovery.

---

## B. Rumusan Masalah, Kontribusi, dan Gap

### B1. ★★☆
Jelaskan tiga rumusan masalah Anda dan bagaimana masing-masing dijawab oleh hasil.

**Arah jawaban:**  
RM1 → LLM menstandarkan ke 12 `action_type` (308 *event* teranotasi).  
RM2 → bentuk model kontras (81/119 vs 31/43 *place/transition*).  
RM3 → lebih ringkas + *generalization* naik tajam (0,0807 → 0,7079), *fitness* tetap tinggi.

### B2. ★★★
Apa *research gap* spesifik terhadap Norouzifar, Tax, dan Rebmann?

**Arah jawaban:** Ketiganya memakai LLM/supervised learning untuk PM, tetapi belum: abstraksi berbasis taksonomi pada *real maintenance data* + komparasi *as-is vs enriched* + 4 metrik conformance utuh + temuan operasional *actionable*.

### B3. ★★★
Mengapa kontribusi Anda disebut “bukan sekadar ada AI”, melainkan perbedaan *granularity* representasi proses?

**Arah jawaban:** Yang berubah adalah tingkat representasi aktivitas (ejaan → kategori tindakan bisnis), sehingga discovery menangkap peran proses, bukan variasi teks.

### B4. ★★★★
Jika penguji berkata: “Bukankah reduksi label saja sudah cukup tanpa LLM?” Bagaimana Anda membela pilihan GenAI?

**Arah jawaban:** Aturan kata kunci kaku terhadap variasi bahasa teknisi; LLM menangani makna kontekstual (mis. IR Test → MEASUREMENT vs Function Test → TESTING) dalam *taxonomy boundary*. Fallback rule-based hanya jika API gagal. Akurasi mutlak memang belum diukur ahli—ini keterbatasan yang diakui.

---

## C. Metodologi & Desain Sistem

### C1. ★★☆
Sebutkan tiga atribut wajib *event log* dan pemetaannya dari *raw data* Anda.

**Arah jawaban:** `case:concept:name` ← Task ID; `concept:name` ← activity; `time:timestamp` ← start/finish.

### C2. ★★★
Jelaskan empat langkah preprocessing dan dampaknya pada angka 255 → 308.

**Arah jawaban:** Resolusi Case ID, noise filtering, imputasi timestamp (110 *event*), *compound activity splitting* (99 *event* hasil pemecahan). Splitting menambah *event* karena satu baris majemuk dipecah.

### C3. ★★★
Apa itu *taxonomy boundary*? Mengapa LLM “tidak boleh bebas” membuat label?

**Arah jawaban:** Ruang keluaran dibatasi 12 kategori agar abstraksi *controlled vocabulary*, hasil antar-*case* sebanding, dan evaluasi adil terhadap baseline.

### C4. ★★★
Mengapa memilih `gemini-3.1-flash-lite` dengan *temperature* 0,1 dan ambang *confidence* 0,45?

**Arah jawaban:** Temperature rendah menekan variasi acak (lebih deterministik untuk anotasi). Confidence < 0,45 = kandidat anomali pelabelan; pada data Anda tidak ada yang di bawah ambang.

### C5. ★★★★
*Compound activity splitting* dilakukan berbasis aturan, sementara `action_type` oleh LLM. Mengapa tidak keduanya oleh LLM?

**Arah jawaban:** Splitting butuh determinisme struktural (satu baris → N *event*) sebelum anotasi semantik; LLM kemudian menetapkan kategori tanpa mengubah jumlah *event*. Pemisahan tanggung jawab: struktur vs makna.

### C6. ★★★
Mengapa Inductive Miner infrequent (IMf) dengan *noise threshold* 0,2, bukan Alpha Miner atau Heuristics Miner?

**Arah jawaban:** Log pemeliharaan punya perilaku jarang & variasi tinggi; IMf menyaring busur jarang, menghasilkan Petri net yang natural untuk conformance. Alpha lemah terhadap noise/incomplete; Heuristics lebih DFG-oriented.

### C7. ★★★★
Apakah membandingkan *as-is* (255 *event*, 112 aktivitas) dengan *enriched* (308 *event*, 12 aktivitas) “adil”? Apa yang dikontrol?

**Arah jawaban:** Jumlah *cases* sama (52). Yang berubah adalah representasi aktivitas + splitting. Ini komparasi dua *pipeline* realistis, bukan A/B identik pada setiap baris. Batasan: sebagian perbedaan ukuran model juga dipengaruhi splitting, tidak hanya LLM—sebutkan secara jujur jika ditanya.

---

## D. Hasil, Metrik Conformance & Interpretasi

### D1. ★★☆
Definisikan *fitness*, *precision*, *generalization*, dan *simplicity* dengan bahasa Anda sendiri, lalu kaitkan ke angka hasil.

**Arah jawaban singkat:**  
- Fitness: seberapa baik model mereplay log → tetap tinggi (0,9833 → 0,9570).  
- Precision: seberapa ketat model (tidak mengizinkan perilaku berlebih) → turun (0,8716 → 0,5063).  
- Generalization: kemampuan hadapi perilaku baru yang wajar → naik tajam (0,0807 → 0,7079).  
- Simplicity (PM4Py): terkait derajat keterhubungan lokal → sedikit turun, **bukan** ukuran utama keterbacaan manusia.

### D2. ★★★★
Penguji: “Precision Anda jelek, berarti model enriched buruk.” Sanggah secara akademis.

**Arah jawaban:** Precision turun adalah *trade-off* abstraksi: kelas perilaku membesar. Tujuan riset adalah model yang *generalizable* dan interpretable, bukan menghafal *trace*. As-is precision tinggi justru indikasi *overfitting* (generalization 0,0807). Kutip abstrak/Bab V: penurunan precision mencerminkan berkurangnya overfitting, bukan kemunduran kualitas sesuai tujuan.

### D3. ★★★★
Simplicity PM4Py turun, tetapi Anda mengklaim model lebih sederhana. Bukankah kontradiksi?

**Arah jawaban:** Simplicity PM4Py ≠ keterbacaan manusia; mengukur *arc degree* lokal. Keterbacaan lebih tercermin dari reduksi aktivitas 89,29%, place 61,73%, transition 63,87%. Ini dibahas eksplisit di Bab IV.

### D4. ★★★
Mengapa model *as-is* punya fitness/precision tinggi tetapi generalization sangat rendah?

**Arah jawaban:** 112 raw label membuat model hampir memetakan *event* satu-per-satu → cocok menghafal data historis, rapuh terhadap variasi baru (*overfitting*).

### D5. ★★★
Jelaskan perbedaan kualitatif Petri net *as-is* vs *enriched* selain angka.

**Arah jawaban:** As-is = spaghetti, sukar telusuri *happy path*. Enriched = alur terbaca: safety → diagnosis (CLEANING/INSPECTION/MEASUREMENT) → intervensi → TESTING.

### D6. ★★☆
Sebutkan distribusi lima `action_type` teratas dan apa maknanya bagi proses *overhaul*.

**Arah jawaban:** TESTING 53 (17,21%), SAFETY_INDUCTION & CLEANING 52 (16,88%), INSPECTION 51 (16,56%), MEASUREMENT 45 (14,61%). Dominasi diagnosis + safety + testing sesuai karakter overhaul; lima teratas ≈ 82% *event*.

---

## E. Validasi LLM, Keandalan & Etika Metode

### E1. ★★★
Bagaimana Anda memvalidasi keluaran anotasi LLM? Apa yang belum Anda validasi?

**Arah jawaban:** Tiga lapis: skor confidence, ambang 0,45, temperature 0,1 + pemeriksaan informal domain. **Belum:** akurasi kuantitatif vs *ground truth* ahli pemeliharaan—diakui di Bab IV/V.

### E2. ★★★★
Apakah *confidence* tinggi (0,95–1,00) berarti label benar?

**Arah jawaban:** Tidak. Confidence = keyakinan model, bukan *gold standard*. Bisa *confident but wrong*. Perlu validasi ahli.

### E3. ★★★
Berikan contoh pemetaan semantik yang menunjukkan LLM “mengerti konteks”, bukan keyword matching.

**Arah jawaban:** IR Test → MEASUREMENT (menghasilkan nilai ukur); Function Test → TESTING (verifikasi fungsi); LEPAS THERMOSTAT → DISASSEMBLY.

### E4. ★★★★
Bagaimana jika taksonomi 12 kelas salah desain (terlalu kasar/halus)? Apa dampaknya ke conformance?

**Arah jawaban:** Terlalu kasar → precision turun lebih dalam, detail hilang. Terlalu halus → mendekati as-is, spaghetti kembali. Sensitivity analysis antar-taksonomi = saran penelitian lanjutan (Bab V).

---

## F. Analisis Operasional, Bottleneck & Anomali

### F1. ★★★
Bedakan *volume bottleneck* dan *duration bottleneck* pada hasil Anda. Implikasi manajerialnya?

**Arah jawaban:** Volume: CLEANING total 375,96 jam → efisiensi berbasis frekuensi. Duration: REPAIR 32 jam & ADJUSTMENT 21,56 jam per kejadian → perencanaan suku cadang/kompetensi.

### F2. ★★★★
Mengapa analisis durasi bersifat “indikatif”? Sebut keterbatasannya dari dokumen.

**Arah jawaban:** 110/308 timestamp hasil imputasi; durasi shift 08.00–16.30 asumsi SOP; SAFETY/TESTING flat 30 menit; kategori jarang (LUBRICATION n=1) tidak robust. Waktu kalender vs jam kerja juga berbeda (~3.071 vs ~1.609 jam).

### F3. ★★★
Jelaskan empat pola anomali proses yang Anda temukan. Mana yang paling prioritas diperbaiki?

**Arah jawaban:** (1) intervensi tanpa diagnosis 8/52; (2) diagnosis multi-komponen vs *rework* semu; (3) aktivitas setelah TESTING akhir 4 *cases*; (4) jeda panjang sebelum intervensi. Prioritas sering: #1 karena risiko kualitas/keselamatan proses kerja.

### F4. ★★★★
Mengapa pengulangan INSPECTION/MEASUREMENT belum tentu *rework*?

**Arah jawaban:** Bisa diagnosis multi-komponen dalam satu sesi. Perlu atribut komponen; DFG level `action_type` saja menyesatkan.

---

## G. Batasan, Validitas Eksternal & Saran

### G1. ★★★
Sebut batasan masalah penelitian dan konsekuensinya terhadap klaim generalisasi.

**Arah jawaban:** Satu unit PLTD Titikuning; data job card/WBS overhaul saja; satu LLM; IMf 0,2; taksonomi 12 kelas oleh penulis. Temuan tidak digeneralisasi ke unit/jenis pemeliharaan lain—yang berpotensi digeneralisasi adalah *pipeline*-nya.

### G2. ★★★★
Apa ancaman validitas internal paling serius pada penelitian ini?

**Arah jawaban kandidat:** (1) akurasi anotasi belum diukur vs ahli; (2) imputasi timestamp mempengaruhi analisis durasi/DFG time; (3) splitting + LLM berubah bersamaan sehingga efek murni LLM sulit diisolasi penuh.

### G3. ★★☆
Sebut tiga saran penelitian lanjutan dari Bab V.

**Arah jawaban:** Perluas data lintas unit; bandingkan beberapa LLM + sensitivitas taksonomi/temperature; metrik keterbacaan yang lebih representatif daripada simplicity PM4Py.

---

## H. Pertanyaan “Jebakan” / Integrasi Lintas Bab

### H1. ★★★★
Apakah penelitian ini *process mining* atau *text classification*? Di mana batasnya?

**Arah jawaban:** Klasifikasi/abstraksi label adalah tahap *enrichment* pada *event log*; inti evaluasi tetap discovery + conformance pada model proses. Jadi PM dengan dukungan NLP/LLM, bukan murni klasifikasi teks.

### H2. ★★★★
Jika *fitness enriched* turun di bawah 0,9, apakah abstraksi masih Anda bela?

**Arah jawaban:** Perlu tinjau ulang taksonomi/prompt/noise threshold. Saat ini 0,9570 masih tinggi sehingga abstraksi dapat dibela; ada ambang pragmatis kualitas *replay*.

### H3. ★★★
Bagaimana penelitian ini mendukung pengambilan keputusan di *operation & maintenance*?

**Arah jawaban:** Model terbaca untuk SOP/komunikasi; prioritas resource (cleaning vs repair); temuan anomali untuk disiplin urutan kerja—*diagnose-then-intervene*.

### H4. ★★★★
Apa yang akan Anda ubah jika mengulang penelitian dengan waktu 6 bulan lagi?

**Arah jawaban jujur + kuat:** gold-standard labeling sampel oleh ahli + Cohen’s kappa/akurasi; eksperimen ablasi (splitting saja vs LLM saja vs keduanya); bandingkan miner lain; metrik keterbacaan manusia (user study).

---

## I. Paket 12 Pertanyaan Paling Mungkin Muncul (Latihan Intensif)

Latih sampai jawaban lancar tanpa melihat catatan:

1. Apa masalah utama data pemeliharaan yang Anda selesaikan?  
2. Apa kontribusi orisinal terhadap state of the art?  
3. Mengapa 12 kategori? Dari mana datangnya?  
4. Mengapa IMf 0,2?  
5. Interpretasikan penurunan precision + kenaikan generalization.  
6. Mengapa simplicity turun tetapi model diklaim lebih sederhana?  
7. Bagaimana validasi LLM dan keterbatasannya?  
8. Mengapa jumlah *event* naik dari 255 ke 308?  
9. Apa temuan operasional paling penting untuk industri?  
10. Apa batasan generalisasi hasil Anda?  
11. Bedakan anomali pelabelan vs anomali proses.  
12. Bagaimana ketiga RM dijawab dengan bukti angka?

---

## J. Tips Menjawab di Sidang

1. **Struktur STAR mini:** konsep → penerapan di penelitian → angka Bab IV → implikasi/batasan.  
2. **Jangan defensif pada keterbatasan**—akui, lalu tunjukkan Anda paham dampaknya.  
3. **Hafalkan angka kunci:** 52 cases; 255/308 events; 112→12 aktivitas; place 81→31 (−61,73%); transition 119→43 (−63,87%); fitness 0,9833/0,9570; precision 0,8716/0,5063; generalization 0,0807/0,7079; simplicity 0,7246/0,6727; CLEANING 375,96 jam; 8/52 intervensi tanpa diagnosis.  
4. **Jika tidak tahu:** “Di dokumen belum diuji secara X; secara konseptual…; itu masuk saran lanjutan.”

Semoga bermanfaat untuk persiapan sidang.

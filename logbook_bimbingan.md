# Logbook Bimbingan Tugas Akhir

**Judul:** Pemanfaatan Generative AI untuk Process Discovery pada Data Operasional Pemeliharaan Perusahaan Listrik  
**Mahasiswa:** Sakha Wibisono (103012480032)  
**Pembimbing:** Angelina Prima Kurniati, S.T., M.T., Ph.D.

---

| No | Uraian Kegiatan Bimbingan |
|:---:|---|
| **1** | Memaparkan usulan topik TA tentang GenAI untuk process discovery pada data pemeliharaan pembangkit listrik. Mendapat arahan penyusunan latar belakang, perumusan masalah, dan tujuan penelitian pada draf awal Bab I. |
| **2** | Menjelaskan sumber dataset overhaul PLTD Titikuning dari WBS dan job card beserta struktur kolom data mentahnya. Melanjutkan revisi Bab I terkait batasan masalah dan rencana kegiatan penelitian. |
| **3** | Mendiskusikan karakteristik dataset, variasi label aktivitas bebas, dan kebutuhan pembentukan event log untuk process mining. Merevisi Bab II tentang teori process mining, LLM, dan event abstraction sesuai masukan pembimbing. |
| **4** | Memaparkan rencana pra-pemrosesan data, compound activity splitting, serta normalisasi Case ID dan timestamp. Menyelesaikan revisi Bab III tentang arsitektur pipeline, modul anotasi LLM, dan taksonomi dua belas kategori tindakan. |
| **5** | Melaporkan hasil pembersihan 256 baris raw data menjadi 52 case dan 255 event pada log as-is. Mendokumentasikan indikator preprocessing, penanganan Case ID otomatis, dan imputasi timestamp yang hilang. |
| **6** | Mempresentasikan rancangan taxonomy boundary dua belas action type untuk standarisasi label aktivitas pemeliharaan. Menyusun prompt engineering LLM Gemini beserta ambang confidence 0,45 untuk klasifikasi anomali. |
| **7** | Melaporkan hasil anotasi LLM pada 308 event enriched beserta distribusi action type dan atribut kontekstual tiap event. Menyajikan contoh anotasi representatif sebagai bahan penyusunan Bab IV. |
| **8** | Menjelaskan implementasi process discovery dengan Inductive Miner infrequent, noise threshold 0,2, melalui PM4Py. Membandingkan skenario as-is berlabel mentah dan enriched berlabel hasil anotasi AI. |
| **9** | Memaparkan model Petri net as-is yang padat, 81 place dan 119 transition, dibanding model enriched yang lebih ringkas. Menginterpretasikan bentuk control-flow dan fenomena spaghetti model pada pembahasan hasil. |
| **10** | Melaporkan hasil conformance checking pada fitness, precision, generalization, dan simplicity untuk kedua model proses. Menganalisis trade-off generalization yang meningkat dan penurunan precision akibat abstraksi semantik label. |
| **11** | Mendiskusikan temuan bottleneck volume pada CLEANING serta bottleneck durasi pada REPAIR dan ADJUSTMENT. Menyajikan anomali delapan case intervensi tanpa inspeksi pendahulu sebagai rekomendasi perbaikan proses. |
| **12** | Memaparkan draf Bab IV hasil percobaan dan analisis perbandingan model as-is versus enriched AI. Menyusun Bab V kesimpulan yang menjawab tiga rumusan masalah serta saran validasi domain dan perluasan dataset. |
| **13** | Menyerahkan naskah lengkap untuk peninjauan konsistensi antarbab, tabel, gambar, dan daftar pustaka. Merevisi abstrak, kata pengantar, serta melengkapi lampiran kode eksperimen dan visualisasi model proses. |
| **14** | Mempresentasikan ringkasan penelitian, kontribusi utama, dan kesiapan dokumen sidang TA. Memfinalisasi naskah, menyiapkan slide presentasi, serta mengantisipasi pertanyaan penguji terkait metodologi dan validitas anotasi LLM. |

---

*Catatan: Setiap entri memuat maksimal dua kalimat; tiap kalimat ditulis ringkas dan natural sesuai topik bimbingan.*

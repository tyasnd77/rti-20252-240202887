# Jadwal dan Log Pelaksanaan Penelitian

Catatan kronologis pelaksanaan penelitian mulai dari penentuan topik hingga validasi data eksperimen.

## Log Pelaksanaan

| Tanggal | Tahap | Aktivitas | Output |
|----------|---------|---------|---------|
| 29 maret 2026 | Tahap 1 | Identifikasi masalah dan penentuan topik penelitian mengenai analisis sentimen serta karakteristik linguistik pada data kesehatan mental dan personality disorder | Judul penelitian dan rumusan masalah |
| 5 April 2026 | Tahap 2 | Studi literatur terkait Natural Language Processing (NLP), sentiment analysis, TF-IDF, N-Gram, Word Cloud, dan personality disorder | Landasan teori dan referensi penelitian |
| 11 Mei 2026 | Tahap 3 | Pengumpulan dataset kesehatan mental umum dan dataset personality disorder | Dataset penelitian |
| 11 Mei 2026 | Tahap 4 | Seleksi atribut dan penyesuaian format dataset agar siap diproses | Dataset siap preprocessing |
| 11 Mei 2026 | Tahap 5 | Preprocessing data meliputi case folding, cleaning, tokenization, stopword removal, dan stemming | Dataset hasil preprocessing |
| 8 Juni 2026 | Tahap 6 | Penyusunan environment penelitian, dokumentasi dependency, dan konfigurasi eksperimen | Environment specification |
| 8 Juni 2026 | Tahap 7 | Penyusunan execution plan, repeatability test, dan data logging | Dokumen eksperimen |
| 15 Juni 2026 | Tahap 8 | Analisis sentimen menggunakan metode NLP dan ekstraksi fitur TF-IDF | Hasil analisis sentimen |
| 15 Juni 2026 | Tahap 9 | Analisis karakteristik linguistik menggunakan N-Gram dan Word Cloud | Visualisasi dan daftar keyword dominan |
| 22 Juni 2026 | Tahap 10 | Validasi data, pengecekan konsistensi hasil, dan deteksi anomali | Validation report |
| 22 Juni 2026 | Tahap 11 | Penyusunan laporan penelitian dan dokumentasi hasil eksperimen | Draft laporan penelitian |

## Status Ringkas

- **Tahap 1–7**: Selesai (perencanaan penelitian, pengumpulan data, preprocessing, environment, dan execution plan).
- **Tahap 8–9**: Dalam proses (analisis sentimen dan karakteristik linguistik).
- **Tahap 10**: Validasi data telah dirancang dan siap diterapkan pada hasil eksperimen.
- **Tahap 11**: Penyusunan laporan penelitian sedang berlangsung.

## Item Tindak Lanjut (Checklist Sebelum Seminar/Submission)

- [x] Menentukan topik dan tujuan penelitian
- [x] Mengumpulkan dataset kesehatan mental umum
- [x] Mengumpulkan dataset personality disorder
- [x] Menentukan metode NLP yang digunakan
- [x] Menyusun environment penelitian
- [x] Menentukan dependency dan versi library
- [x] Menyusun README eksperimen
- [x] Menyusun execution plan
- [x] Menyusun data logging
- [x] Menyusun prosedur validasi data
- [ ] Menjalankan seluruh eksperimen sesuai execution plan
- [ ] Mengumpulkan hasil setiap run
- [ ] Menghitung rata-rata dan standar deviasi hasil eksperimen
- [ ] Melakukan analisis perbandingan kedua dataset
- [ ] Menyusun visualisasi hasil penelitian
- [ ] Menyelesaikan Bab Hasil dan Pembahasan
- [ ] Finalisasi laporan penelitian

## Progress Penelitian

### Dataset

**Dataset Baseline**
- Nama file: `26de4894-652b-4236-bbdc-6fe3a5d63945.csv`
- Jumlah data: 26.350 teks
- Kolom: `statement`, `status`

**Dataset Personality Disorder**
- Nama file: `personality_disorder_subset_2kolom_NPL.csv`
- Jumlah data: 432 teks
- Kolom: `Thought`, `PD_Category`

### Metode yang Digunakan

- Text Preprocessing
- Sentiment Analysis
- TF-IDF
- N-Gram Analysis
- Word Cloud
- Visualisasi Data

### Environment

- OS: Windows 11
- Python: 3.11
- Framework: NLTK dan Scikit-Learn
- Random Seed: 42

### Status Saat Ini

Penelitian telah menyelesaikan tahap persiapan dan perancangan eksperimen, termasuk dokumentasi environment, execution plan, serta validasi data. Dataset telah siap digunakan untuk proses analisis. Tahap berikutnya adalah menjalankan eksperimen NLP, mengumpulkan hasil analisis, melakukan interpretasi hasil, dan menyusun laporan akhir penelitian.

**Estimasi progres penelitian saat ini: ±85% selesai.**

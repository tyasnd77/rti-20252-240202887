# WS-05: Variabel & Metrik

> **Bab 5 — Metric, Measurement & Data**

---

## Ringkasan Materi

### Measurement Alignment Model

Setiap pengukuran yang valid harus bisa ditelusuri melalui rantai ini tanpa lompatan logis:

```
Problem → Concept → Variable → Metric → Data → Result
```

### Operationalization = Keputusan Desain

Menerjemahkan konsep abstrak menjadi variabel terukur bukan proses mekanis. "Code quality" yang diukur via SonarQube code smells membawa asumsi implisit. Setiap operasionalisasi harus didokumentasikan dan dijustifikasi.

### Empat Tipe Data (NOIR)

| Tipe | Ciri | Contoh | Operasi Valid |
|------|------|--------|---------------|
| **Nominal** | Kategori, tanpa urutan | Jenis algoritma (RF, SVM, CNN) | Modus, chi-square |
| **Ordinal** | Urutan, interval tidak sama | Skala Likert (1-5) | Median, Spearman |
| **Interval** | Jarak bermakna, tanpa nol absolut | Suhu Celsius | Mean, Pearson, t-test |
| **Ratio** | Jarak bermakna + nol absolut | Waktu eksekusi (ms) | Semua operasi |

Tipe data menentukan uji statistik yang valid. Kebanyakan metrik performa TI = ratio; persepsi pengguna = ordinal.

### Kriteria Pemilihan Metrik

- **Representative** — Mewakili konsep yang diteliti
- **Sensitive** — Cukup peka menangkap perbedaan bermakna (hindari ceiling effect)
- **Feasible** — Bisa dikumpulkan dalam batasan waktu dan biaya

### Pre-registration

Metrik harus ditentukan **sebelum** eksperimen. Memilih metrik setelah melihat data = **p-hacking**. Metrik tambahan yang ditemukan kemudian dilaporkan sebagai *exploratory*, bukan *confirmatory*.

### Primary vs Secondary Metric

- **Primary Metric** — Langsung terikat ke hipotesis, menentukan kesimpulan
- **Secondary Metric** — Pendukung, dilaporkan di samping primary; statusnya suplementer

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Pemilihan metrik | Berdasarkan kebiasaan/tool yang ada | Berdasarkan construct validity |
| Anomali | Dihapus untuk laporan bersih | Diinvestigasi — bisa jadi temuan |
| Kapan dipilih | Setelah sistem jadi (monitoring) | Sebelum eksperimen (by design) |

### Istilah Penting

- **Operationalization** — Transformasi konsep abstrak menjadi variabel terukur
- **Construct Validity** — Sejauh mana pengukuran benar-benar mengukur konsep yang dimaksud
- **Measurement Scale** — Klasifikasi data (NOIR) yang menentukan analisis valid
- **Multi-metric Evaluation** — Menggunakan beberapa metrik untuk menangkap konsep kompleks

---

## Template A.5 — Definisi Variabel, Metrik & Justifikasi

```
VARIABLE & METRIC DEFINITION

Research Question: Bagaimana pengaruh penggunaan ChatGPT terhadap kecenderungan self-diagnosis Borderline Personality Disorder (BPD) pada mahasiswa, menggunakan metode survei kuantitatif dengan analisis regresi, metrik berupa skor skala Likert dan nilai korelasi, dataset berupa data kuesioner mahasiswa, serta dibandingkan dengan baseline mahasiswa yang tidak menggunakan AI dalam self-diagnosis?

| Variabel | Tipe | Konsep | Metrik | Skala | Satuan | Cara Mengukur | Justifikasi |
|----------|------|--------|--------|-------|--------|---------------|-------------|
|Penggunaan ChatGPT| IV   |Tingkat penggunaan AI untuk mencari informasi mental health|Frekuensi penggunaan, tingkat kepercayaan terhadap jawaban AI|Ordinal (Likert 1–5)|Skor|Kuesioner skala Likert|Mewakili intensitas interaksi mahasiswa dengan AI|
|Self-diagnosis BPD| DV   |Kecenderungan mahasiswa menyimpulkan dirinya memiliki BPD tanpa validasi profesional|Tingkat persetujuan terhadap pernyataan self-diagnosis| Ordinal (Likert 1–5)|Skor|Kuesioner skala Likert dan analisis teks|Mengukur kecenderungan self-diagnosis berdasarkan interpretasi informasi AI|
|Latar belakang responden| CV   |Faktor yang dapat mempengaruhi hasil penelitian|Jurusan, pengalaman konsultasi, literasi mental health|Nominal|Kategori|Pertanyaan identitas dan pengalaman|Mengurangi bias dari faktor luar|

Alignment Check:
  RQ → Concept → Variable → Metric → Data → Result
  [✓] Setiap langkah terdokumentasi
  [✓] Tidak ada "lompatan logis"
  [✓] Metrik mengukur apa yang dimaksud (construct validity)
```

---

## Latihan 1 — Operationalization Chain

Gunakan RQ dari WS-04. Definisikan variabel dan metriknya.

**RQ:** Bagaimana pengaruh penggunaan ChatGPT terhadap kecenderungan self-diagnosis Borderline Personality Disorder (BPD) pada mahasiswa, menggunakan metode survei kuantitatif dengan analisis regresi, metrik berupa skor skala Likert dan nilai korelasi, dataset berupa data kuesioner mahasiswa, serta dibandingkan dengan baseline mahasiswa yang tidak menggunakan AI dalam self-diagnosis?

| Variabel | Tipe | Konsep Abstrak | Metrik Konkret | Skala (NOIR) | Satuan |
|----------|------|----------------|----------------|---------------|---------|
| Penggunaan ChatGPT | IV | Intensitas penggunaan AI dalam mencari informasi mental health | Frekuensi penggunaan ChatGPT dan tingkat kepercayaan terhadap jawaban AI | Ordinal | Skor Likert 1–5 |
| Self-diagnosis BPD | DV | Kecenderungan mahasiswa merasa memiliki BPD tanpa diagnosis profesional | Tingkat persetujuan terhadap pernyataan self-diagnosis | Ordinal | Skor Likert 1–5 |
| Literasi mental health | CV | Tingkat pemahaman mahasiswa terhadap kesehatan mental | Tingkat pengetahuan dan pemahaman mental health | Ordinal | Skor Likert 1–5 |

**Apakah ada lompatan logis dalam rantai?** [✓] Ya / [ ] Tidak
> Jika ya, di mana? 
Variabel dan metrik yang digunakan sudah sesuai dengan konsep penelitian dan dapat diukur secara langsung melalui kuesioner.

---

## Latihan 2 — Evaluasi Metrik

Evaluasi metrik DV yang dipilih di Latihan 1 menggunakan 3 kriteria.

| Kriteria | Skor (1-5) | Justifikasi |
|-----------|-------------|--------------|
| Representative | 4 | Skala Likert cukup mewakili tingkat penggunaan ChatGPT dan kecenderungan self-diagnosis pada mahasiswa |
| Sensitive | 4 | Perbedaan skor dapat menunjukkan variasi tingkat self-diagnosis antar responden |
| Feasible | 5 | Data mudah dikumpulkan melalui kuesioner online dan dapat dianalisis dengan sederhana |

**Apakah perlu secondary metric?** [✓] Ya / [ ] Tidak
> Jika ya, apa dan mengapa? 
Secondary metric berupa analisis teks (keyword extraction dan sentiment analysis) digunakan untuk mendukung hasil kuantitatif dan melihat pola bahasa self-diagnosis pada jawaban responden.

**Contoh kasus ceiling effect untuk metrik ini:**
> Jika sebagian besar responden memilih nilai tertinggi pada skala Likert, maka perbedaan antar responden menjadi sulit terlihat dan sensitivitas metrik menurun.

---

## Latihan 3 — Data Quality Check

Bayangkan data yang akan dikumpulkan dari eksperimen. Evaluasi 4 dimensi kualitas data.

| Dimensi | Pertanyaan | Jawaban | Strategi Mitigasi |
|----------|-------------|----------|-------------------|
| Completeness | Apakah semua data point terkumpul? | Ada kemungkinan responden tidak mengisi semua pertanyaan | Membuat pertanyaan penting wajib diisi pada Google Form |
| Consistency | Apakah ada kontradiksi internal? | Beberapa jawaban responden bisa tidak konsisten | Melakukan pengecekan dan penyaringan data sebelum analisis |
| Validity | Apakah benar-benar mengukur yang dimaksud? | Kuesioner harus sesuai dengan konsep self-diagnosis dan penggunaan AI | Menggunakan indikator berdasarkan jurnal dan penelitian sebelumnya |
| Representativeness | Apakah sampel mewakili populasi target? | Sampel mungkin belum mewakili seluruh mahasiswa | Menyebarkan kuesioner ke mahasiswa dari beberapa jurusan atau angkatan |

---

## Refleksi

> Mengapa memilih metrik setelah melihat data dianggap p-hacking? Apa bedanya dengan eksplorasi data yang sah?

**Jawaban:**
Memilih metrik setelah melihat data dianggap p-hacking karena peneliti dapat memilih metrik yang paling menguntungkan hasil penelitian sehingga hasil menjadi bias. Hal tersebut berbeda dengan eksplorasi data yang sah, karena eksplorasi dilakukan untuk memahami pola data dan dilaporkan sebagai temuan tambahan, bukan untuk mengganti hipotesis atau metrik utama yang sudah ditentukan sebelumnya.

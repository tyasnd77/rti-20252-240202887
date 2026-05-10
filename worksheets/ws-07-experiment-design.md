# WS-07: Experimental Design & Validity

> **Bab 7 — Experimental Design & Validity**

---

## Ringkasan Materi

### Correlation ≠ Causality

Kausalitas membutuhkan 3 syarat:
1. **Covariance** — X dan Y bergerak bersama
2. **Temporal precedence** — X berubah sebelum Y
3. **Elimination of alternatives** — Tidak ada faktor lain yang menjelaskan Y

Controlled experiment adalah satu-satunya metode yang bisa membuktikan kausalitas.

### Empat Jenis Validitas

| Jenis | Pertanyaan | Ancaman Umum |
|-------|-----------|-------------|
| **Internal** | Apakah hubungan IV→DV nyata? | Confounding variable, selection bias |
| **External** | Apakah bisa digeneralisasi? | Dataset terlalu spesifik |
| **Construct** | Apakah mengukur konsep yang benar? | Metrik tidak sesuai |
| **Conclusion** | Apakah kesimpulan statistik valid? | Sample size kecil, uji salah |

Internal dan external validity sering berkonflik: semakin terkontrol (internal kuat) → semakin artificial (external lemah).

### Tiga Tipe Eksperimen dalam Riset TI

| Tipe | Deskripsi | Kapan Digunakan |
|------|----------|----------------|
| **Comparison Study** | Metode A vs B pada kondisi identik | Membandingkan pendekatan berbeda |
| **Ablation Study** | Full system → lepas komponen satu per satu | Mengukur kontribusi tiap komponen |
| **Parameter Study** | Variasikan satu parameter, amati dampak | Uji sensitifitas/robustness |

### Fairness dalam Perbandingan

Perbandingan yang adil = **kondisi identik** untuk semua metode: dataset sama, preprocessing sama, tuning effort sebanding, environment sama, metrik sama.

Contoh tidak adil: Transformer (30 fitur tambahan + Bayesian optimization) vs RF (default params) → hasilnya misleading.

### Threats to Validity = Diidentifikasi Sebelum Eksperimen

Ancaman validitas harus diidentifikasi **sebelum** eksperimen dan mitigasinya dirancang sebagai bagian dari desain — bukan ditulis sebagai boilerplate setelah selesai.

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan testing | Memastikan sistem memenuhi requirement | Membuktikan hubungan kausal antar variabel |
| Baseline | Versi sebelumnya (last release) | Metode tervalidasi dari literatur |
| Kegagalan | Bug → fix → release | H₀ tidak ditolak → tetap kontribusi ilmiah |
| Sukses | 100% test pass | Evidence valid — mendukung atau menolak hipotesis |

### Istilah Penting

- **Causality** — Hubungan sebab-akibat (covariance + temporal + elimination)
- **Controlled Experiment** — Ubah satu variabel, kontrol sisanya, amati efek
- **Fairness** — Semua metode diuji pada kondisi yang benar-benar identik
- **Threats to Validity** — Faktor yang bisa melemahkan kesimpulan jika tidak dimitigasi
- **Conclusion Validity** — Validitas statistik: power, sample size, uji yang tepat

---

## Template A.7 — Desain Eksperimen Lengkap

```
EXPERIMENT DESIGN

Research Question :  Bagaimana pengaruh penggunaan ChatGPT terhadap kecenderungan self-diagnosis Borderline Personality Disorder (BPD) pada mahasiswa, menggunakan metode survei kuantitatif dengan analisis regresi, metrik berupa skor skala Likert dan nilai korelasi, dataset berupa data kuesioner mahasiswa, serta dibandingkan dengan baseline mahasiswa yang tidak menggunakan AI dalam self-diagnosis?
Hypothesis        : Tidak terdapat pengaruh yang signifikan antara penggunaan ChatGPT dengan kecenderungan self-diagnosis BPD pada mahasiswa
Tipe Eksperimen   : [✓] Comparison  [ ] Ablation  [ ] Parameter

Kondisi Eksperimen:

| Kondisi | Deskripsi | IV Value | CV Settings |
|----------|------------|-----------|--------------|
| Control | Mahasiswa yang jarang atau tidak menggunakan ChatGPT untuk mencari informasi mental health | Penggunaan ChatGPT rendah | Dataset, preprocessing, dan metode analisis sama |
| Treatment | Mahasiswa yang sering menggunakan ChatGPT untuk mencari informasi mental health | Penggunaan ChatGPT tinggi | Dataset, preprocessing, dan metode analisis sama |

Fairness Checklist:
[✓] Dataset identik untuk semua kondisi
[✓] Preprocessing setara
[✓] Tuning effort setara
[✓] Environment identik
[✓] Metrik evaluasi sama

Threat Analysis:

| Threat Type | Ancaman Spesifik | Mitigasi |
|--------------|------------------|-----------|
| Internal | Responden bisa memberikan jawaban tidak jujur | Menggunakan kuesioner anonim |
| External | Sampel hanya berasal dari mahasiswa tertentu | Menyebarkan kuesioner ke beberapa mahasiswa dengan latar berbeda |
| Construct | Pertanyaan kuesioner tidak benar-benar mengukur self-diagnosis | Menggunakan indikator berdasarkan literatur sebelumnya |
| Conclusion | Jumlah responden terlalu sedikit | Menambah jumlah responden agar hasil lebih valid |

Statistical Plan:
Uji statistik   : Korelasi Spearman / Regresi sederhana
Justifikasi     : Data menggunakan skala Likert sehingga sesuai untuk analisis hubungan antar variabel
Alpha           : 0,05
Effect size min : Korelasi ≥ 0,3
```

---

## Latihan 1 — Desain Eksperimen

Susun desain eksperimen berdasarkan RQ, variabel, dan sistem dari WS-04 sampai WS-06.

**RQ:** Bagaimana pengaruh penggunaan ChatGPT terhadap kecenderungan self-diagnosis Borderline Personality Disorder (BPD) pada mahasiswa, menggunakan metode survei kuantitatif dengan analisis regresi, metrik berupa skor skala Likert dan nilai korelasi, dataset berupa data kuesioner mahasiswa, serta dibandingkan dengan baseline mahasiswa yang tidak menggunakan AI dalam self-diagnosis?
**Tipe eksperimen:** [✓] Comparison / [ ] Ablation / [ ] Parameter

| Kondisi | Deskripsi | IV Value | CV Settings |
|----------|------------|-----------|--------------|
| Control | Mahasiswa yang tidak menggunakan ChatGPT untuk self-diagnosis | Penggunaan rendah | Dataset dan preprocessing sama |
| Treatment | Mahasiswa yang menggunakan ChatGPT untuk mencari informasi mental health | Penggunaan tinggi | Dataset dan preprocessing sama |

---

## Latihan 2 — Fairness Checklist

Evaluasi apakah desain eksperimen di Latihan 1 sudah fair.

| Kriteria | Status | Detail |
|-----------|--------|--------|
| Dataset identik | ✅ | Menggunakan sumber data dan responden yang sama |
| Preprocessing setara | ✅ | Semua data teks dibersihkan dengan metode yang sama |
| Tuning effort setara | ✅ | Analisis dilakukan dengan parameter yang sama |
| Environment identik | ✅ | Analisis dilakukan pada sistem dan tools yang sama |
| Metrik evaluasi sama | ✅ | Semua kondisi menggunakan skor Likert dan analisis NLP yang sama |

**Ada yang tidak fair?** [ ] Ya / [✓] Tidak
> Jika ya, bagaimana cara memperbaikinya? 
Semua kondisi eksperimen menggunakan metode dan proses yang sama sehingga perbandingan tetap adil.

---

## Latihan 3 — Threat Analysis

Identifikasi ancaman validitas untuk desain eksperimen ini.

| Threat Type | Ancaman Spesifik | Mitigasi |
|--------------|------------------|-----------|
| Internal | Jawaban responden bisa dipengaruhi opini pribadi atau tren media sosial | Menggunakan pertanyaan yang lebih spesifik dan netral |
| External | Hasil penelitian mungkin tidak mewakili seluruh mahasiswa | Menambah variasi responden dari beberapa jurusan |
| Construct | Self-diagnosis sulit diukur secara langsung | Menggunakan indikator berdasarkan penelitian sebelumnya |
| Conclusion | Jumlah data kurang sehingga hasil kurang kuat | Menambah jumlah responden dan melakukan validasi data |

**Ancaman mana yang paling sulit dimitigasi?** Construct Validity
**Mengapa?**
Karena self-diagnosis merupakan kondisi psikologis yang bersifat subjektif sehingga sulit diukur secara benar hanya melalui kuesioner dan analisis teks.

---

## Refleksi

> Sebuah paper melaporkan "metode kami mengalahkan semua baseline." Apa 3 pertanyaan pertama yang harus diajukan untuk mengevaluasi klaim ini?

**Jawaban:**
1. Apakah semua baseline diuji menggunakan dataset dan kondisi yang sama?
2. Apakah metode evaluasi dan metrik yang digunakan sudah adil untuk semua metode?
3. Apakah jumlah data dan proses preprocessing dijelaskan dengan jelas sehingga hasil dapat dipercaya?

# WS-04: Research Question & Hypothesis

> **Bab 4 — Research Question, Contribution & Hypothesis**

---

## Ringkasan Materi

### RQ Bukan Pertanyaan Biasa

Research Question yang baik secara implisit mengandung cetak biru eksperimen: subjek, baseline, metrik, domain, dataset.

| Kualitas | Contoh |
|----------|--------|
| **Buruk** | "Bagaimana pengaruh deep learning terhadap deteksi malware?" |
| **Baik** | "Apakah CNN menghasilkan F1-Score lebih tinggi dari RF pada CIC-MalMem-2022?" |

Perbedaan: RQ yang baik menyebutkan **metode spesifik**, **metrik terukur**, **baseline**, dan **dataset**.

### Tiga Jenis RQ

| Jenis | Pola | Kebutuhan |
|-------|------|-----------|
| **Comparison** | A vs B → mana lebih baik? | ≥ 2 metode, metrik sama |
| **Improvement** | A' vs A → modifikasi lebih baik? | Pre/post, bukti perbaikan |
| **Exploratory** | Faktor X₁...Xₙ → pengaruh terhadap Y? | Multi-variabel, korelasi/regresi |

### Contribution Statement

Tiga jenis kontribusi: **Improvement** (metode terbukti lebih baik), **Comparison** (perbandingan sistematis yang belum ada), **Novel Approach** (pendekatan baru). Kontribusi harus terhubung langsung dengan gap — kontribusi tanpa gap = klaim tanpa justifikasi.

### Hypothesis H₀ / H₁

- **H₀** (Null) = Tidak ada perbedaan signifikan — asumsi default, harus dibuktikan salah
- **H₁** (Alternative) = Ada perbedaan signifikan — diterima hanya jika H₀ ditolak
- Harus **falsifiable**, mengandung **metrik terukur**, dirumuskan **SEBELUM eksperimen**

### Rantai Operasionalisasi

```
RQ → Variable → Metric → Data → Analysis
```

Jika rantai ini tidak lengkap, RQ belum mature. Bi-directional: RQ yang tidak bisa jadi hipotesis testable harus direvisi mundur.

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan pertanyaan | Apa yang harus dibangun? | Apa yang harus dibuktikan? |
| Bentuk jawaban | Sistem yang berfungsi | Bukti empiris terukur |
| Sukses diukur oleh | User satisfaction, uptime | Signifikansi statistik, effect size |
| Jika gagal | Debug dan perbaiki | Laporkan, analisis mengapa |

### Istilah Penting

- **Research Question (RQ)** — Pertanyaan spesifik: variabel terukur + metrik + konteks
- **Contribution Statement** — Apa yang diketahui setelah riset selesai yang sebelumnya belum ada
- **H₀ / H₁** — Null vs Alternative Hypothesis
- **Falsifiability** — Kondisi hipotesis ditolak harus bisa didefinisikan sebelum eksperimen
- **Operationalization** — Proses mewujudkan konsep abstrak menjadi variabel terukur

---

## Template A.4 — RQ-Contribution-Hypothesis

```
RQ-CONTRIBUTION-HYPOTHESIS

Gap Statement  : Sebagian besar penelitian tentang AI dan self-diagnosis mental health masih menggunakan metode kualitatif atau literature review, serta belum ada penelitian yang secara spesifik membahas pengaruh penggunaan ChatGPT terhadap kecenderungan self-diagnosis Borderline Personality Disorder (BPD) pada mahasiswa.

Research Question:
  Tipe         : [ ] Comparison  [ ] Improvement  [✓] Exploratory
  Formulasi    : Bagaimana pengaruh penggunaan ChatGPT terhadap kecenderungan self-diagnosis Borderline Personality Disorder (BPD) pada mahasiswa, menggunakan metode survei kuantitatif dengan analisis regresi, metrik berupa skor skala Likert dan nilai korelasi, dataset berupa data kuesioner mahasiswa, serta dibandingkan dengan baseline mahasiswa yang tidak menggunakan AI dalam self-diagnosis?
  Variabel IV  : Penggunaan ChatGPT untuk mencari informasi mental health
  Variabel DV  : Kecenderungan self-diagnosis Borderline Personality Disorder (BPD)
  Metrik       : - Data kategorikal (misalnya jurusan, pengalaman konsultasi:ya/tidak).
                 - Skala Likert untuk mengukur tingkat literasi kesehatan mental
  Dataset      : Data kuesioner mahasiswa berupa jawaban skala Likert dan jawaban terbuka
  Baseline     : Mahasiswa yang tidak menggunakan AI/ChatGPT untuk mencari informasi mental health

Quality Check RQ:
  [✓] Variabel spesifik
  [✓] Metrik jelas
  [✓] Baseline ada
  [✓] Konteks disebutkan
  [✓] Memerlukan eksperimen (bukan hanya survei literatur)

Contribution Statement:
  Apa yang baru diketahui : Penelitian ini bertujuan mengetahui bagaimana penggunaan ChatGPT dapat mempengaruhi kecenderungan mahasiswa melakukan self-diagnosis BPD, serta melihat pola interpretasi mahasiswa terhadap informasi mental health dari AI.
  Jenis kontribusi        : [ ] Improvement  [ ] Comparison  [✓] Novel approach
  Gap yang diisi          : Method gap dan context gap

Hypothesis Pair:
  H₀ : Tidak terdapat pengaruh yang signifikan antara penggunaan ChatGPT dengan kecenderungan self-diagnosis BPD pada mahasiswa.
  H₁ : Terdapat pengaruh yang signifikan antara penggunaan ChatGPT dengan kecenderungan self-diagnosis BPD pada mahasiswa.
  Threshold              : p-value < 0,05
  Justifikasi threshold  : Nilai 0,05 digunakan sebagai batas umum dalam penelitian kuantitatif untuk menentukan apakah hasil penelitian signifikan atau tidak.
```

---

## Latihan 1 — Dari Gap ke RQ

Gunakan gap yang ditemukan di WS-03. Transformasikan menjadi Research Question.

**Gap dari WS-03:** Sebagian besar penelitian masih menggunakan metode kualitatif atau literature review dan belum secara spesifik membahas pengaruh ChatGPT terhadap self-diagnosis BPD pada mahasiswa.

**RQ versi pertama (tulis bebas):**
> Apakah penggunaan ChatGPT mempengaruhi mahasiswa dalam melakukan self-diagnosis BPD?

**Evaluasi RQ:**

| Komponen | Ada? | Isi |
|----------|------|-----|
|Metode spesifik|Ya|Survei kuantitatif dan analisis regresi|
| Metrik terukur |Ya|Skala Likert dan hasil korelasi|
| Baseline |Ya|Mahasiswa yang tidak menggunakan AI|
| Dataset/konteks |Ya|Mahasiswa pengguna ChatGPT|

**Tipe RQ:** [ ] Comparison / [ ] Improvement / [✓] Exploratory

**RQ versi revisi (setelah evaluasi):**
>Bagaimana pengaruh penggunaan ChatGPT terhadap kecenderungan self-diagnosis Borderline Personality Disorder (BPD) pada mahasiswa, menggunakan metode survei kuantitatif dengan analisis regresi, metrik berupa skor skala Likert dan nilai korelasi, dataset berupa data kuesioner mahasiswa, serta dibandingkan dengan baseline mahasiswa yang tidak menggunakan AI dalam self-diagnosis?

---

## Latihan 2 — Hypothesis Pair

Rumuskan pasangan hipotesis dari RQ di Latihan 1.

| Komponen | Isi |
|----------|-----|
| H₀ | Tidak terdapat pengaruh yang signifikan antara penggunaan ChatGPT dengan kecenderungan self-diagnosis BPD pada mahasiswa |
| H₁ | Terdapat pengaruh yang signifikan antara penggunaan ChatGPT dengan kecenderungan self-diagnosis BPD pada mahasiswa |
| Metrik | Data kategorikal dan skala likert |
| Threshold | p-value < 0,05 |
| Justifikasi threshold | Nilai tersebut merupakan standar umum untuk menentukan signifikansi penelitian |

**Apakah hipotesis ini falsifiable?** [✓] Ya / [ ] Tidak
> Bagaimana cara membuktikannya salah? 
Hipotesis dapat dibuktikan salah apabila hasil analisis menunjukkan nilai p-value lebih besar dari 0,05 sehingga tidak ditemukan pengaruh yang signifikan antara variabel.

---

## Latihan 3 — Rantai Operasionalisasi

Lengkapi rantai dari RQ hingga metode analisis.

| Tahap | Isi |
|-------|-----|
| RQ | Bagaimana pengaruh penggunaan ChatGPT terhadap kecenderungan self-diagnosis Borderline Personality Disorder (BPD) pada mahasiswa, menggunakan metode survei kuantitatif dengan analisis regresi, metrik berupa skor skala Likert dan nilai korelasi, dataset berupa data kuesioner mahasiswa, serta dibandingkan dengan baseline mahasiswa yang tidak menggunakan AI dalam self-diagnosis?|
| Variable (IV) | Penggunaan ChatGPT untuk mencari informasi mental health |
| Variable (DV) | Kecenderungan self-diagnosis Borderline Personality Disorder (BPD) |
| Metric |Data kategorikal dan skala likert|
| Data source |Kaggle BPD dataset|
| Analysis method | Metode analisis yang digunakan adalah Natural Language Processing (NLP) untuk mengidentifikasi pola teks yang berkaitan dengan self-diagnosis BPD. Tahapan analisis meliputi preprocessing data teks, keyword extraction, dan sentiment analysis untuk melihat pola interpretasi pengguna terhadap informasi mental health. Hasil analisis kemudian digunakan untuk melihat hubungan antara penggunaan AI/ChatGPT dan kecenderungan self-diagnosis pada mahasiswa. |

**Apakah rantai lengkap?** [✓] Ya / [ ] Tidak

Seluruh komponen mulai dari pertanyaan penelitian hingga metode analisis sudah saling terhubung dan dapat diuji secara terukur.

---

## Refleksi

> Ambil satu judul skripsi/paper yang pernah dibaca. Coba ekstrak RQ-nya. Apakah RQ tersebut memenuhi semua komponen (metode, metrik, baseline, konteks)? Jika tidak, apa yang hilang?

**Judul:** Analisis Pengaruh Penggunaan ChatGPT terhadap Kecenderungan Self-Diagnosis Borderline Personality Disorder (BPD) pada Mahasiswa Ilmu Komputer.

**RQ yang diekstrak:** Bagaimana pengaruh penggunaan ChatGPT terhadap kecenderungan self-diagnosis Borderline Personality Disorder (BPD) pada mahasiswa ilmu komputer, menggunakan metode survei kuantitatif dengan analisis regresi, metrik berupa skor skala Likert dan nilai korelasi, dataset berupa data kuesioner mahasiswa, serta dibandingkan dengan baseline mahasiswa yang tidak menggunakan AI dalam self-diagnosis?

**Komponen yang hilang:** Penelitian tersebut belum memiliki metrik yang jelas, tidak menggunakan baseline pembanding, serta belum mengukur pengaruh AI secara kuantitatif sehingga hasil penelitian masih bersifat umum dan deskriptif.

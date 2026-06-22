# WS-09: Implementation & Environment

> **Bab 9 — Implementasi Riset & Kontrol Lingkungan**

---

## Ringkasan Materi

### Implementasi Riset ≠ Coding Biasa

Tujuan implementasi riset bukan membuat software yang berfungsi, melainkan membangun **instrumen pengukuran yang konsisten**. Setiap modul harus di-mapping ke variabel (dari Bab 6), parameter harus config-driven, dan logging aktif dari hari pertama.

> **Mengapa reproducibility penting?** Sains dibangun di atas prinsip verifikasi — temuan harus bisa dikonfirmasi oleh peneliti lain. _Replicability crisis_ yang terjadi di banyak paper riset ML/AI disebabkan oleh environment tidak terdokumentasi: orang lain tidak bisa reproduksi, hasil diragukan, kepercayaan terhadap temuan hilang. Prinsip: **dokumentasi environment = snapshot kredibilitas riset Anda.**

### Reproducible Implementation Model

```
Design → Implementation → Environment Setup → Execution Consistency → Reproducibility → Trustworthy Result
```

Setiap transisi memiliki syarat:
- Design → Implementation: kode sesuai mapping variabel-ke-komponen
- Implementation → Environment: versi, dependency, seed, path, OS eksplisit
- Environment → Consistency: seed terkunci, urutan deterministik
- Consistency → Reproducibility: dokumentasi lengkap
- Reproducibility → Trust: siapa pun ikuti dokumentasi → hasil sama/serupa

### Repeatability vs Reproducibility

| Level | Peneliti | Environment | Hasil |
|-------|---------|-------------|-------|
| **Repeatability** | Sama | Sama | Sama persis |
| **Reproducibility** | Berbeda | Berbeda (ikuti docs) | Sama/serupa |

Capai **repeatability** dulu, baru **reproducibility**.

### Engineering vs Research Perspective

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Tujuan | Sistem berfungsi untuk user | Instrumen pengukuran konsisten |
| Dependency | Update ke terbaru | Lock di versi spesifik |
| Testing | Unit, integration, E2E | Repeatability test (run ulang → sama?) |
| Dokumentasi | User guide, API docs | Environment spec, execution steps, expected output |
| Config | Default masuk akal | Setiap parameter eksplisit & adjustable |

### Jebakan Kognitif

1. Menunda environment setup → bug sulit dilacak
2. Tidak pakai version control → hasil tidak bisa direkonstruksi
3. Menolak Docker/container → "di laptop saya bisa" saat review
   - **Docker** = teknologi container yang "membungkus" aplikasi beserta seluruh dependency-nya dalam satu unit terisolasi. Hasilnya: kode berjalan identik di laptop, server, maupun reviewer lain. Intro singkat: `docker run -v $(pwd):/workspace environment-image python run_experiment.py`
4. 3× hasil sama ≠ repeatable (bisa cache/state tersimpan)

### Dependency Locking

Mengandalkan "install library terbaru" berbahaya: versi berbeda = perilaku berbeda = hasil tidak reproducible. Praktik:
- **Python**: buat `requirements.txt` dengan versi eksplisit: `scikit-learn==1.3.2`, lalu kunci dengan `pip freeze > requirements.txt`
- **Conda**: gunakan `conda env export > environment.yml` untuk snapshot lengkap
- **Node.js/R/Julia**: gunakan `package-lock.json` / `renv.lock` / `Project.toml` — semua fungsi serupa: lock versi + hash

### Istilah Penting

- **Environment Specification** — Deskripsi lengkap: hardware, OS, runtime, library + versi, config, seed
- **Dependency** — Komponen eksternal yang harus di-lock versinya
- **Config-driven** — Parameter dieksternalisasi ke file konfigurasi, bukan hardcode

---

## Template A.9 — Dokumentasi Setup Eksperimen

```
EXPERIMENT SETUP DOCUMENTATION

Hardware:
  CPU     : Intel Core i5
  RAM     : 8 GB
  GPU     : CPU Only
  Storage : 512 GB SSD

Software:
  OS        : Windows 11
  Runtime   : Python 3.11
  Framework : NLTK, Scikit-Learn

Dependencies:
| Library      | Version |
|--------------|---------|
| pandas       | 2.2.2 |
| numpy        | 1.26.4 |
| nltk         | 3.9 |
| scikit-learn | 1.5.1 |
| matplotlib   | 3.9.2 |
| wordcloud    | 1.9.3 |

Konfigurasi:
  Config file     : config.yaml
  Random seed     : 42
  Hyperparameters :
      max_features = 5000
      ngram_range = (1,2)
      test_size = 0.2

Reproducibility Check:
  [✓] Dependency terdokumentasi
  [✓] Seed ditetapkan
  [✓] Config tersimpan
  [✓] README tersedia
```

---

## Latihan 1 — Environment Specification

Dokumentasikan environment untuk eksperimen Anda (boleh environment saat ini atau yang direncanakan).

| Komponen | Spesifikasi |
|----------|------------|
| CPU | Intel Core i5 / AMD Ryzen 5 |
| RAM | 8 GB |
| GPU | CPU-Only |
| OS | Windows 11 |
| Runtime | Python 3.11 |
| Framework |Scikit-Learn, NLTK |
| Random Seed | 42 |

**Dependencies (minimal 5):**

| Library      | Version | Alasan Dibutuhkan                 |
| ------------ | ------- | --------------------------------- |
| pandas       | 2.2.2   | Membaca dan mengolah dataset CSV  |
| numpy        | 1.26.4  | Operasi numerik                   |
| nltk         | 3.9     | Tokenisasi dan preprocessing teks |
| scikit-learn | 1.5.1   | TF-IDF, klasifikasi, evaluasi     |
| matplotlib   | 3.9.2   | Visualisasi hasil                 |
| wordcloud    | 1.9.3   | Visualisasi keyword dominan       |
| seaborn      | 0.13.2  | Analisis distribusi data          |


---

## Latihan 2 — Repeatability Test Plan

Skenario Pengujian

Eksperimen dijalankan sebanyak 3 kali menggunakan dataset:

Baseline: 26de4894-652b-4236-bbdc-6fe3a5d63945.csv
Intervensi: personality_disorder_subset_2kolom_NPL.csv

Parameter dan seed dibuat sama pada setiap pengujian.

| Run | Seed | Metrik Utama                      | Hasil Sama? |
| --- | ---- | --------------------------------- | ----------- |
| 1   | 42   | Accuracy Sentiment Classification | —           |
| 2   | 42   | Accuracy Sentiment Classification | ☑ Ya        |
| 3   | 42   | Accuracy Sentiment Classification | ☑ Ya        |


**Jika hasil berbeda, kemungkinan penyebab:**

- Random seed tidak dikunci.
- Data split berubah setiap run.
- Cache notebook masih tersimpan.
- Background process menggunakan RAM/CPU.
- Versi library berbeda.

___________________________________________________

**Checklist kontrol yang sudah diterapkan:**
- [✓] Random seed di-set di Python dan NumPy
- [✓] Tidak ada proses lain yang mengganggu
- [✓] Cache dibersihkan
- [✓] Menggunakan file konfigurasi yang sama

---

## Latihan 3 — README Eksperimen


```
# Judul Eksperimen

Analisis Perbandingan Sentimen dan Karakteristik Linguistik pada Dataset Kesehatan Mental Umum dan Dataset Teks yang Mengandung Indikasi Personality Disorder Menggunakan Natural Language Processing

## 1. Environment

OS          : Windows 11
Python      : 3.11
RAM         : 8 GB
Framework   : NLTK, Scikit-Learn
Random Seed : 42

## 2. Installation

pip install pandas numpy nltk scikit-learn matplotlib seaborn wordcloud

atau

pip install -r requirements.txt

## 3. Data

Dataset Baseline:
26de4894-652b-4236-bbdc-6fe3a5d63945.csv

Jumlah Data:
26.350 teks

Kolom:
- statement
- status

Dataset Intervensi:
personality_disorder_subset_2kolom_NPL.csv

Jumlah Data:
432 teks

Kolom:
- Thought
- PD_Category

Kategori Personality Disorder:
- NPD
- PPD
- BPD
- ASPD
- AVPD
- Schizoid
- HPD

## 4. Execution

python main.py

atau pada Google Colab:
Run All Cells

## 5. Configuration

config.yaml

random_seed = 42
max_features = 5000
ngram_range = (1,2)
test_size = 0.2

## 6. Expected Output

1. Distribusi sentimen pada dataset kesehatan mental
2. Distribusi kategori Personality Disorder
3. Keyword dominan menggunakan TF-IDF
4. Analisis N-Gram
5. Word Cloud
6. Perbandingan baseline dan intervensi
7. Grafik visualisasi hasil analisis

Output:
- sentiment_result.csv
- keyword_result.csv
- wordcloud.png
- ngram_analysis.png
```

---

## Refleksi

> Apakah eksperimen Anda saat ini bisa direproduksi oleh orang lain tanpa bantuan Anda? Komponen apa yang masih hilang?
Sebagian besar eksperimen sudah dapat direproduksi karena dataset yang digunakan, metode Natural Language Processing (NLP), tahapan preprocessing, serta parameter analisis telah ditentukan dan didokumentasikan. Penelitian juga menggunakan dua dataset yang jelas, yaitu dataset kesehatan mental umum sebagai baseline dan dataset teks terindikasi personality disorder sebagai data intervensi. Namun, agar penelitian benar-benar mencapai reproducibility, masih diperlukan dokumentasi teknis yang lebih lengkap terkait environment dan konfigurasi eksperimen.

**Level saat ini:** [☑] Repeatability / [ ] Reproducibility / [ ] Belum keduanya

**Komponen yang belum terdokumentasi:**
> 
- File requirements.txt yang berisi versi library yang digunakan.
- File konfigurasi (config.yaml) untuk parameter eksperimen.
- Dokumentasi versi Python dan sistem operasi.
- Dokumentasi langkah preprocessing secara rinci.
- Dokumentasi proses filtering dataset personality disorder menggunakan NLP.
- Struktur folder proyek dan penyimpanan output hasil analisis.
- Panduan reproduksi eksperimen dalam bentuk README yang lebih lengkap.
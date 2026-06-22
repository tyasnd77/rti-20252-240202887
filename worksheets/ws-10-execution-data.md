# WS-10: Experiment Execution & Data Collection

> **Bab 10 — Eksekusi Eksperimen & Pengumpulan Data**

---

## Ringkasan Materi

### Experiment Execution Pipeline

```
Design → Execution Plan → Controlled Execution → Data Collection → Data Logging → Dataset for Analysis
```

### Multiple Run = Non-Negotiable

Single run **tidak pernah cukup** untuk klaim ilmiah. Minimum 5-10 run per skenario dengan seed berbeda. Multiple run menghasilkan:
- Mean, std, confidence interval
- Distribusi hasil → uji statistik
- Variabilitas → error bar di grafik

### Execution Plan

Setiap eksperimen harus memiliki plan sebelum eksekusi:
- Daftar skenario
- Jumlah run per skenario
- Random seed per run (pre-determined!)
- Urutan eksekusi (randomisasi/counterbalancing)
- Pre-execution checklist

### Data Logging Komprehensif

Setiap run menghasilkan log terstruktur:
1. **Identitas** — Run ID, timestamp, skenario
2. **Konfigurasi** — Semua parameter, seed, code version
3. **Hasil** — Semua metrik, output detail
4. **Metadata** — Waktu eksekusi, resource usage, warning/error

Format: CSV/JSON/database — **bukan stdout yang di-copy-paste**.

### Engineering vs Research Execution

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Run | Sekali (deploy) | Multiple (min 5-10, seed berbeda) |
| Logging | Error log, access log | Semua parameter, metrik, metadata |
| Anomali | Bug → fix → redeploy | Investigasi → dokumentasi → analisis |
| Urutan | Tidak penting | Bisa bias — perlu randomisasi |

### Anomali = Dokumentasi, Bukan Hapus

Run gagal/anomali tidak boleh dihapus tanpa dokumentasi. Bisa jadi:
- **Bug** → fix & re-run (dokumentasikan!)
- **Batas kemampuan metode** → DNF = temuan
- **Data yang bias** jika hanya simpan run "berhasil"

### Jebakan Kognitif

1. "Satu angka cukup" → tanpa distribusi, tidak bisa diuji
2. "Seed tidak penting" → bahkan algoritma deterministik bisa dipengaruhi library stokastik
3. "Run gagal langsung hapus" → kehilangan temuan potensial
4. "Semua run harus hari ini" → thermal throttling, fatigue

---

## Template A.10 — Execution Plan & Data Log

```
EXECUTION PLAN
| Run # | Skenario                      | Seed | Parameter           | Status  | Waktu | Output File       |
| ----- | ----------------------------- | ---- | ------------------- | ------- | ----- | ----------------- |
| 1     | Dataset Kesehatan Mental Umum | 42   | TF-IDF, ngram=(1,2) | Planned | -     | baseline_run1.csv |
| 2     | Dataset Kesehatan Mental Umum | 123  | TF-IDF, ngram=(1,2) | Planned | -     | baseline_run2.csv |
| 3     | Dataset Kesehatan Mental Umum | 456  | TF-IDF, ngram=(1,2) | Planned | -     | baseline_run3.csv |
| 4     | Dataset Kesehatan Mental Umum | 789  | TF-IDF, ngram=(1,2) | Planned | -     | baseline_run4.csv |
| 5     | Dataset Kesehatan Mental Umum | 999  | TF-IDF, ngram=(1,2) | Planned | -     | baseline_run5.csv |
| 6     | Dataset Personality Disorder  | 42   | TF-IDF, ngram=(1,2) | Planned | -     | pd_run1.csv       |
| 7     | Dataset Personality Disorder  | 123  | TF-IDF, ngram=(1,2) | Planned | -     | pd_run2.csv       |
| 8     | Dataset Personality Disorder  | 456  | TF-IDF, ngram=(1,2) | Planned | -     | pd_run3.csv       |
| 9     | Dataset Personality Disorder  | 789  | TF-IDF, ngram=(1,2) | Planned | -     | pd_run4.csv       |
| 10    | Dataset Personality Disorder  | 999  | TF-IDF, ngram=(1,2) | Planned | -     | pd_run5.csv       |

Jumlah runs per skenario : 2
Total runs               : 10

DATA LOG (per run):
| Field     | Isi                                      |
| --------- | ---------------------------------------- |
| Run ID    | run-001                                  |
| Timestamp | 2026-06-23 10:30:00                      |
| Skenario  | Dataset Kesehatan Mental Umum            |
| Dataset   | 26de4894-652b-4236-bbdc-6fe3a5d63945.csv |
| Peneliti  | Tyas Nurshika Damaia                     |

```

---

## Latihan 1 — Execution Plan

execution plan 

| Run # | Skenario                          | Seed | Parameter Kunci     | Status  |
| ----- | --------------------------------- | ---- | ------------------- | ------- |
| 1     | Baseline Dataset Kesehatan Mental | 42   | TF-IDF, ngram=(1,2) | Planned |
| 2     | Baseline Dataset Kesehatan Mental | 123  | TF-IDF, ngram=(1,2) | Planned |
| 3     | Baseline Dataset Kesehatan Mental | 456  | TF-IDF, ngram=(1,2) | Planned |
| 4     | Baseline Dataset Kesehatan Mental | 789  | TF-IDF, ngram=(1,2) | Planned |
| 5     | Baseline Dataset Kesehatan Mental | 999  | TF-IDF, ngram=(1,2) | Planned |
| 6     | Dataset Personality Disorder      | 42   | TF-IDF, ngram=(1,2) | Planned |
| 7     | Dataset Personality Disorder      | 123  | TF-IDF, ngram=(1,2) | Planned |
| 8     | Dataset Personality Disorder      | 456  | TF-IDF, ngram=(1,2) | Planned |
| 9     | Dataset Personality Disorder      | 789  | TF-IDF, ngram=(1,2) | Planned |
| 10    | Dataset Personality Disorder      | 999  | TF-IDF, ngram=(1,2) | Planned |

**Total skenario:**2
1. Dataset kesehatan mental umum (baseline)
2. Dataset personality disorder (intervensi)
**Run per skenario:** 5
**Total run keseluruhan:**10

---

## Latihan 2 — Data Log Terstruktur

Desain format data log untuk eksperimen Anda. Tentukan field apa saja yang akan dicatat.

**Identitas:**
| Field       | Contoh                |
| ----------- | --------------------- |
| Run ID      | run-001               |
| Timestamp   | 2026-06-23T10:30:00   |
| Skenario    | Baseline              |
| Dataset     | Mental Health Dataset |
| Output File | result_run001.csv     |

**Konfigurasi:**
| Field                | Contoh    |
| -------------------- | --------- |
| Seed                 | 42        |
| Python Version       | 3.11      |
| NLTK Version         | 3.9       |
| Scikit-Learn Version | 1.5.1     |
| Vectorizer           | TF-IDF    |
| N-Gram               | (1,2)     |
| Max Features         | 5000      |
| Code Version         | commit-v1 |


**Hasil:**
| Metrik         | Tipe Data | Range Valid |
| -------------- | --------- | ----------- |
| Accuracy       | Float     | 0.0 – 1.0   |
| Precision      | Float     | 0.0 – 1.0   |
| Recall         | Float     | 0.0 – 1.0   |
| F1-Score       | Float     | 0.0 – 1.0   |
| Jumlah Keyword | Integer   | > 0         |
| Jumlah N-Gram  | Integer   | > 0         |
| Waktu Eksekusi | Float     | > 0 detik   |

Metadata
| Field     | Contoh     |
| --------- | ---------- |
| CPU Usage | 45%        |
| RAM Usage | 3.2 GB     |
| Warning   | None       |
| Error     | None       |
| Notes     | Run normal |

**Format output:** [☑] CSV / [☑] JSON / [ ] Database / [ ] Lainnya: ____

---

## Latihan 3 — Anomaly Protocol

| Jenis Anomali                 | Contoh                              | Tindakan                                            |
| ----------------------------- | ----------------------------------- | --------------------------------------------------- |
| Run gagal (crash)             | File dataset tidak terbaca          | Dokumentasikan error, perbaiki path, jalankan ulang |
| Hasil ekstrem                 | Accuracy turun drastis menjadi 40%  | Periksa preprocessing dan distribusi data           |
| Waktu eksekusi anomali        | Run membutuhkan waktu 3× lebih lama | Cek penggunaan CPU/RAM dan proses background        |
| Inkonsistensi dengan run lain | F1-score berbeda jauh dari run lain | Periksa seed, split data, dan konfigurasi model     |
| Data kosong                   | Setelah filtering tidak ada data    | Periksa proses filtering dan keyword                |
| Error preprocessing           | Tokenisasi gagal                    | Dokumentasikan error dan ulangi proses              |

**Prinsip:** 
Detect
↓
Investigate
↓
Document
↓
Decide

---

## Refleksi

> Pernahkah Anda melaporkan hasil riset/tugas dari single run? Apa risikonya? Bagaimana multiple run mengubah kepercayaan terhadap hasil?

**Pengalaman sebelumnya:**
> Pada beberapa tugas sebelumnya, hasil analisis sering dilaporkan hanya berdasarkan satu kali eksekusi. Risiko dari pendekatan tersebut adalah hasil yang diperoleh belum tentu konsisten karena dapat dipengaruhi oleh random seed, pembagian data, atau kondisi lingkungan komputasi. Akibatnya, kesimpulan penelitian dapat menjadi kurang valid dan sulit direproduksi oleh peneliti lain.
**Yang akan dilakukan berbeda:**
> Pada penelitian ini, eksperimen akan dijalankan sebanyak lima kali untuk setiap skenario menggunakan seed yang berbeda. Seluruh parameter, hasil metrik, dan metadata akan dicatat dalam log terstruktur. Dengan multiple run, hasil penelitian dapat dianalisis berdasarkan rata-rata dan variasi hasil sehingga tingkat kepercayaan terhadap kesimpulan penelitian menjadi lebih tinggi dan lebih mudah direproduksi oleh peneliti lain.

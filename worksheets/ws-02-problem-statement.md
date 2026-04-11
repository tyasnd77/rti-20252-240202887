# WS-02: Problem Statement

> **Bab 2 — Problem Formulation & System Context**

---

## Ringkasan Materi

### Problem Formation Model

Masalah riset melewati 5 tahap transformasi. Melompat langsung dari Reality ke Variable adalah kesalahan paling umum.

```
Reality → Observed Issue (Symptom) → Diagnosed Problem (Root Cause)
→ Researchable Problem (Scoped) → Measurable Variable (Operationalized)
```

### Topic ≠ Problem ≠ Research Problem

| Level | Contoh | Status |
|-------|--------|--------|
| **Topik** | Keamanan IoT | Terlalu luas, tidak bisa diuji |
| **Problem** | MQTT tidak terenkripsi | Spesifik tapi belum riset |
| **Research Problem** | Belum ada studi membandingkan overhead TLS 1.3 vs DTLS pada MQTT di IoT RAM < 64KB | Bisa dirancang eksperimennya |

### Symptom vs Root Cause

Apa yang diamati (gejala) ≠ mengapa terjadi (akar masalah). Gunakan **5 Whys** atau **Fishbone Diagram** untuk menggali.

Contoh: "User meninggalkan checkout" (symptom) → "Waktu loading > 8 detik karena API call sequential" (root cause).

### System Thinking

Setiap masalah riset TI harus terikat pada komponen sistem: **Input → Process → Output → Outcome → Constraints → Stakeholders**.

### Problem Quality Check

Masalah riset yang layak harus memenuhi 5 kriteria:
- **Clarity** — Satu orang membaca akan paham
- **Measurability** — Ada metrik kuantitatif
- **Relevance** — Penting untuk domain
- **Testability** — Bisa gagal (falsifiable)
- **Impact** — Ada kontribusi jika terjawab

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan | Menyelesaikan masalah (*solve*) | Memahami dan membuktikan (*understand & prove*) |
| Masalah | Bug, error, fitur belum ada | Gap dalam pengetahuan |
| Scope | Selesaikan semua yang perlu | Batasi agar bisa dibuktikan |
| Output | Working system | Evidence, paper, replicable findings |

### Istilah Penting

- **Problem Statement** — Formulasi tertulis: konteks sistem + gap + dampak + justifikasi
- **System Context** — Deskripsi lengkap: input, proses, output, outcome, constraints, stakeholders
- **Problem Drift** — Masalah "bermutasi" dari pendahuluan ke metodologi karena statement awal tidak presisi
- **Solution-First Thinking** — Memulai dari solusi tanpa masalah yang jelas — berbahaya dalam riset
- **Operational Definition** — Definisi variabel yang cukup jelas agar peneliti lain bisa mengukur hal yang sama

---

## Template A.2 — Problem Statement Builder

```
PROBLEM STATEMENT BUILDER

Domain & Konteks
  Domain   : Sistem Rekomendasi / Machine Learning
  Konteks  : Platform streaming film yang memberikan rekomendasi berdasarkan rating pengguna

System Context
  Input       : Data rating pengguna terhadap film
  Process     : Pengolahan data menggunakan metode collaborative filtering dengan Matrix Factorization (SVD)
  Output      : Daftar rekomendasi film yang dipersonalisasi
  Outcome     : Peningkatan relevansi rekomendasi yang diterima pengguna
  Constraints : Data sparsity tinggi, jumlah data terbatas, dan variasi preferensi pengguna
  Stakeholders: Pengguna, pengembang sistem, dan platform streaming

Fenomena → Problem
  Fenomena yang diamati             : Pengguna kesulitan menemukan film yang sesuai dengan preferensi mereka
  Gejala (symptom) yang terukur     : Rendahnya tingkat kecocokan rekomendasi dan minimnya interaksi terhadap rekomendasi
  Masalah yang didiagnosis          : Sistem rekomendasi kurang akurat akibat data rating yang tidak lengkap (sparsity tinggi)
  Masalah riset (researchable)      : Belum diketahui seberapa efektif metode Matrix Factorization dalam meningkatkan akurasi rekomendasi pada kondisi data yang sparse
  Variabel yang terukur             : Accuracy, Precision, Recall, F1-score, dan Mean Absolute Error (MAE)

Problem Quality Check
  [☑] Clarity — Apakah satu orang membaca akan paham?
  [☑] Measurability — Apakah ada metrik kuantitatif?
  [☑] Relevance — Apakah penting untuk domain?
  [☑] Testability — Apakah bisa gagal?
  [☑] Impact — Apakah ada kontribusi jika terjawab?

Problem Statement (1 paragraf):
  Pada platform streaming film, pengguna sering mengalami kesulitan dalam menemukan film yang sesuai dengan preferensi mereka karena rekomendasi yang diberikan belum cukup akurat. Hal ini diduga disebabkan oleh data rating pengguna yang tidak lengkap sehingga sistem kesulitan mengenali pola preferensi pengguna. Oleh karena itu, penelitian ini bertujuan untuk mengevaluasi apakah metode Matrix Factorization dapat meningkatkan akurasi sistem rekomendasi dengan menggunakan metrik seperti accuracy, precision, recall, dan MAE, sehingga dapat diketahui seberapa efektif metode tersebut dalam mengatasi permasalahan data yang tidak lengkap.
```

---

## Latihan 1 — Dari Topik ke Masalah Riset

Pilih satu topik di bidang TI yang diminati. Transformasikan melalui 5 tahap Problem Formation Model.

**Topik awal:** Sistem rekomendasi film berbasis collaborative filtering
| Tahap | Hasil |
|-------|-------|
| Reality | Pengguna kesulitan menemukan film yang sesuai di platform streaming |
| Observed Issue (Symptom) | Banyak pengguna tidak menonton rekomendasi yang diberikan sistem |
| Diagnosed Problem (Root Cause) | Sistem rekomendasi kurang akurat karena data rating pengguna tidak lengkap (sparsity tinggi) |
| Researchable Problem | Belum diketahui seberapa akurat metode Matrix Factorization dalam mengatasi sparsity pada sistem rekomendasi film |
| Measurable Variable | Accuracy, Precision, Recall, F1-score, dan MAE |

**Apakah terjebak solution-first thinking?** [ ] Ya / [☑] Tidak

alasan: Karena masalah dirumuskan dari fenomena → bukan langsung dari solusi

---

## Latihan 2 — System Context Decomposition

Gambarkan konteks sistem dari masalah riset di Latihan 1.

| Komponen | Deskripsi |
|----------|----------|
| Input | Data rating pengguna terhadap film yang diperoleh dari dataset publik MovieLens (https://grouplens.org/datasets/movielens/) |
| Process | Pengolahan data menggunakan collaborative filtering dan Matrix Factorization (SVD) |
| Output | Daftar rekomendasi film untuk pengguna |
| Outcome | Pengguna mendapatkan rekomendasi yang lebih sesuai |
| Constraints | Data sparsity tinggi, dataset terbatas, keterbatasan jumlah user dan film |
| Stakeholders | Pengguna, developer sistem, platform streaming |

**Komponen mana yang paling relevan dengan masalah riset?** Process dan Constraints

---

## Latihan 3 — Problem Quality Check

Evaluasi problem statement yang sudah dibuat menggunakan 5 kriteria.

| Kriteria | Skor (1-5) | Justifikasi |
|----------|-----------|-------------|
| Clarity | 4 | Masalah cukup jelas, namun bisa diperjelas pada jenis dataset |
| Measurability | 5 | Menggunakan metrik kuantitatif seperti accuracy dan MAE |
| Relevance | 5 | Sangat relevan dalam sistem rekomendasi |
| Testability | 5 | Dapat diuji dengan eksperimen dan evaluasi model |
| Impact | 4 | Memberikan peningkatan akurasi, namun terbatas pada konteks dataset |

**Skor total:** 23 / 25

**Problem statement versi final (1 paragraf):**
>Pengguna pada platform streaming sering mengalami kesulitan dalam menemukan film yang sesuai dengan preferensi mereka akibat sistem rekomendasi yang kurang akurat. Hal ini disebabkan oleh tingginya tingkat sparsity pada data rating pengguna yang menghambat sistem dalam mempelajari pola preferensi secara optimal. Oleh karena itu, penelitian ini bertujuan untuk mengevaluasi akurasi metode Matrix Factorization dalam meningkatkan kualitas rekomendasi film dengan menggunakan metrik seperti accuracy, precision, recall, F1-score, dan Mean Absolute Error (MAE), sehingga dapat diketahui efektivitas metode tersebut dalam mengatasi permasalahan sparsity pada sistem rekomendasi.
---

## Refleksi

> Bandingkan "masalah" yang biasa ditemui saat coding (bug, error) dengan masalah riset. Apa perbedaan fundamental dalam cara mendefinisikan dan mendekati keduanya?

**Jawaban:**
Masalah dalam coding biasanya berupa bug atau error yang memiliki penyebab langsung dan solusi yang jelas, seperti kesalahan sintaks atau logika program. Sedangkan masalah riset lebih kompleks karena berfokus pada menemukan dan membuktikan penyebab suatu fenomena yang belum tentu terlihat secara langsung. Dalam riset, masalah harus dirumuskan secara sistematis, dapat diukur, dan dapat diuji, bukan hanya sekadar diperbaiki seperti pada kasus bug dalam pemrograman.
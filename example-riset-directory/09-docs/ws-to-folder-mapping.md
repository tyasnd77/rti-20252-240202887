# Mapping: Worksheets ke Struktur Folder

Dokumen ini menunjukkan bagaimana setiap worksheet (ws-01 hingga ws-16) dipetakan ke struktur folder dalam penelitian.

---

## FASE 1: PROPOSAL & PERENCANAAN (ws-01 hingga ws-08)

### **ws-01: Distorsi & Paradigma — Research Mindset in IT**

**Tujuan:** Memahami validitas riset, distorsi dalam research trust model, dan paradigma penelitian (positivist vs interpretivist).

**Aplikasi di Penelitian:**
- Keputusan paradigma riset (positivist + Design Science Research)
- Identifikasi validitas internal, external, construct, conclusion yang harus dijaga
- Pencegahan distorsi di setiap tahap (design, implementation, execution, analysis)

**Tempat Penyimpanan:**
- [00-admin/jadwal-dan-log-penelitian.md](../00-admin/jadwal-dan-log-penelitian.md) — Log keputusan paradigma & validitas
- [09-docs/rencana-penelitian.md](rencana-penelitian.md) — Positioning paradigma riset

---

### **ws-02: Problem Statement — Problem Formulation & System Context**

**Tujuan:** Formulasi masalah spesifik melalui transformasi Reality → Symptom → Root Cause → Research Problem → Variable.

**Deliverable:**
- Problem statement yang jelas & measurable
- System thinking (Input → Process → Output → Outcome)
- 5 kriteria masalah yang baik (Clarity, Measurability, Relevance, Testability, Impact)

**Tempat Penyimpanan:**
- [01-proposal/proposal-penelitian.md](../01-proposal/proposal-penelitian.md) — Problem Statement (Section)

---

### **ws-03: Literature Mapping & Gap — Literature Review & Gap Analysis**

**Tujuan:** Pemetaan sistematis literatur (concept-centric), identifikasi gap (performance, method, data, context).

**Metodologi:**
- Boolean search dengan dokumentasi eksplisit
- Snowballing (backward & forward)
- Matriks literatur konsep vs referensi
- 4 jenis gap: Performance, Method, Data, Context

**Deliverable:**
- Matriks literatur dengan gap teridentifikasi
- Daftar pustaka (BibTeX)
- Summary: Gap analysis (yang spesifik dipilih)

**Tempat Penyimpanan:**
- [02-literatur/matriks-literatur.md](../02-literatur/matriks-literatur.md) — Pemetaan konsep vs referensi
- [02-literatur/daftar-pustaka.bib](../02-literatur/daftar-pustaka.bib) — Bibliography
- [01-proposal/proposal-penelitian.md](../01-proposal/proposal-penelitian.md) — Gap summary

---

### **ws-04: Research Question & Hypothesis — RQ, Contribution & Hypothesis**

**Tujuan:** Formulasi RQ yang falsifiable & hypothesis testable.

**Kriteria RQ yang Baik:**
- Menyebutkan metode spesifik, baseline, metrik terukur, domain, dataset
- 3 jenis RQ: Comparison, Improvement, Exploratory
- Rantai operasionalisasi: RQ → Variable → Metric → Data → Analysis

**Deliverable:**
- Research Question (1-3 RQ jelas & falsifiable)
- Contribution Statement (linked ke gap)
- Hypothesis H₀ & H₁ (testable, pre-specified)

**Tempat Penyimpanan:**
- [01-proposal/proposal-penelitian.md](../01-proposal/proposal-penelitian.md) — RQ, Contribution, Hypothesis

---

### **ws-05: Variabel & Metrik — Metric, Measurement & Data**

**Tujuan:** Operasionalisasi variabel & metrik pengukuran.

**Rantai Measurement:**
```
Problem → Concept → Variable → Metric → Data → Result
```

**Empat Tipe Data (NOIR):**
- Nominal, Ordinal, Interval, Ratio (menentukan uji statistik valid)

**Deliverable:**
- Mapping lengkap: RQ → IV/DV/CV → Metric → Data type
- Justifikasi setiap metrik (representative, sensitive, feasible)
- Primary vs secondary metrics (pre-registration!)

**Tempat Penyimpanan:**
- [01-proposal/proposal-penelitian.md](../01-proposal/proposal-penelitian.md) — Variabel & Metrik section
- [03-teori/arsitektur-dan-skema.md](../03-teori/arsitektur-dan-skema.md) — Mapping ke komponen sistem

---

### **ws-06: System-Experiment Mapping — System Design sebagai Experimental Artifact**

**Tujuan:** Desain sistem yang jelas me-map variabel ke komponen.

**4 Prinsip Desain:**
1. **Traceability** — Tiap komponen → variabel mana?
2. **Modularity** — IV bisa diubah tanpa efek samping
3. **Controllability** — CV externalisasi ke config
4. **Measurability** — Sistem auto-log metrik

**Deliverable:**
- Diagram arsitektur (Gateway, Redis, PostgreSQL)
- Skema database (ERD)
- Skema cache (Redis)
- Mapping IV/DV/CV ke komponen
- Configuration template (YAML/JSON)

**Tempat Penyimpanan:**
- [03-teori/arsitektur-dan-skema.md](../03-teori/arsitektur-dan-skema.md) — Diagram & mapping lengkap
- [05-kode/gateway/.env.example](../05-kode/.env.example) — Config template
- [09-docs/tahap-1-arsitektur-dan-skema-database.md](tahap-1-arsitektur-dan-skema-database.md) — Detail teknis

---

### **ws-07: Experimental Design & Validity — Experimental Design & Validity**

**Tujuan:** Desain eksperimen yang valid (internal, external, construct, conclusion).

**3 Tipe Eksperimen:**
- Comparison study (A vs B)
- Ablation study (full → lepas component)
- Parameter study (variasikan satu parameter)

**Threats to Validity:**
- Internal: Confounding, selection bias
- External: Dataset terlalu spesifik
- Construct: Metrik tidak sesuai
- Conclusion: Sample size kecil, uji salah

**Deliverable:**
- Desain eksperimen jelas (skenario, N run, seed, urutan)
- Threats to validity teidentifikasi & mitigation
- Fairness checklist (kondisi identik untuk semua metode)

**Tempat Penyimpanan:**
- [01-proposal/proposal-penelitian.md](../01-proposal/proposal-penelitian.md) — Experimental Design section
- [09-docs/tahap-3-pengujian-k6.md](tahap-3-pengujian-k6.md) — Rencana eksekusi detail

---

### **ws-08: Proposal Integration — Proposal & Checkpoint (UTS)**

**Tujuan:** Verifikasi koherensi proposal (red thread: Problem → Gap → RQ → Metrik → Sistem → Eksperimen).

**6 Koneksi Kritis:**
```
Problem (ws-02) → Gap (ws-03) → RQ (ws-04) → Metrik (ws-05) → 
Sistem (ws-06) → Eksperimen (ws-07)
```

**Verifikasi:**
- [ ] Gap muncul dari analisis literatur terhadap masalah?
- [ ] RQ langsung menjawab gap?
- [ ] Setiap variabel punya metrik?
- [ ] Metrik bisa diukur sistem?
- [ ] Desain eksperimen menjawab RQ?
- [ ] Terminologi konsisten (same variable name everywhere)?

**Deliverable:**
- Proposal utuh (Introduction, Method, Methodology, Expected Results)
- Integration checklist (5 koneksi kritis OK)
- Red thread map

**Tempat Penyimpanan:**
- [01-proposal/proposal-penelitian.md](../01-proposal/proposal-penelitian.md) — Proposal final
- [01-proposal/README.md](../01-proposal/README.md) — Checklist koherensi

---

## FASE 2: IMPLEMENTASI & EKSEKUSI (ws-09 hingga ws-13)

### **ws-09: Implementation & Environment — Implementasi Riset & Kontrol Lingkungan**

**Tujuan:** Implementasi reproducible (environment terdokumentasi, config-driven, logging aktif).

**Reproducible Implementation Model:**
```
Design → Implementation → Environment Setup → Execution Consistency → 
Reproducibility → Trustworthy Result
```

**Deliverable:**
- Source code dengan mapping variabel ke komponen
- Configuration template (YAML/JSON dengan setiap parameter jelas)
- Structured logging (JSON: run_id, timestamp, metric, value)
- Environment lock (version eksplisit: Go, PostgreSQL, Redis, k6)
- Repeatability test (run ulang → hasil sama)

**Tempat Penyimpanan:**
- [05-kode/gateway/](../05-kode/gateway/) — API Gateway implementation
- [05-kode/k6/](../05-kode/k6/) — Load testing scripts
- [05-kode/README.md](../05-kode/README.md) — Reproducibility checklist
- [09-docs/tahap-2-implementasi-gateway.md](tahap-2-implementasi-gateway.md) — Detail teknis

---

### **ws-10: Experiment Execution & Data Collection — Eksekusi Eksperimen & Pengumpulan Data**

**Tujuan:** Eksekusi terkontrol dengan multiple runs & logging komprehensif.

**Experiment Execution Pipeline:**
```
Design → Execution Plan → Controlled Execution → Data Collection → 
Data Logging → Dataset for Analysis
```

**Non-Negotiable:**
- **Multiple runs** (minimum 5-10 per skenario dengan seed berbeda)
- **Pre-determined execution plan** (daftar skenario, jumlah run, seed sequence, urutan)
- **Comprehensive logging** (run ID, timestamp, config, semua metrik, metadata)

**Deliverable:**
- Raw data: CSV/JSON per run
- Metadata: code version, environment, parameter config, durasi
- Resource metrics: CPU%, Memory timeseries per container
- Execution log: anomali, interrupt, resolution

**Tempat Penyimpanan:**
- [04-data/raw/](../04-data/raw/) — Raw output dari k6 & monitoring
- [04-data/README.md](../04-data/README.md) — Data collection spec
- [09-docs/tahap-3-pengujian-k6.md](tahap-3-pengujian-k6.md) — Execution plan detail

---

### **ws-11: Data Validation & Integrity — Validasi Data & Integritas**

**Tujuan:** Memastikan data trusted sebelum analisis.

**Data Trust Model:**
```
Raw Data → Data Cleaning → Consistency Check → Validation → Trusted Data
```

**4 Pilar Data Quality:**
1. **Accuracy** — Nilai dalam range logis
2. **Consistency** — Format seragam
3. **Completeness** — Tidak ada missing dari plan
4. **Validity** — Sesuai desain eksperimen

**Anomaly Detection (3 Jenis):**
- Statistical outlier (IQR method)
- Contextual anomaly (normal absolut, abnormal dalam konteks)
- Pattern anomaly (pola sistematis)

**Prinsip:** Detect → Investigate → Document → Decide — **JANGAN langsung hapus**

**Deliverable:**
- Validation report (4 pilar check)
- Cleaned dataset
- Anomaly log (detected, investigated, decision)

**Tempat Penyimpanan:**
- [04-data/validated/](../04-data/validated/) — Data lolos validasi
- [04-data/data_validation_report.md](../04-data/data_validation_report.md) — Report 4 pilar
- [04-data/anomaly_log.md](../04-data/anomaly_log.md) — Anomali investigation

---

### **ws-12: Result Presentation & Visualization — Penyajian Hasil & Visualisasi**

**Tujuan:** Transformasi data raw menjadi tabel & grafik yang bermakna.

**Data → Insight Model:**
```
Validated Data → Structured Presentation → Visualization → 
Pattern Recognition → Insight
```

**Prinsip:**
- **Tabel** = Presisi, self-contained, sortable
- **Grafik** = Pola visual, tren, perbandingan cepat
- **Keduanya saling melengkapi** (bukan pilih salah satu)

**Jenis Grafik:**
- Perbandingan → Bar chart
- Distribusi → Box plot / Violin plot
- Tren temporal → Line chart
- Korelasi → Scatter plot

**Visualization Bias (Hindari):**
- Truncated axis
- Inconsistent scale
- Cherry-picked data
- 3D effects tanpa dimensi ke-3

**Deliverable:**
- Tabel statistik deskriptif (mean ± std per skenario)
- Grafik utama (5-10 grafik strategis)
- Caption jelas & self-contained

**Tempat Penyimpanan:**
- [06-output/tables/](../06-output/tables/) — Tabel CSV & markdown
- [06-output/figures/](../06-output/figures/) — Grafik PNG/PDF
- [06-output/README.md](../06-output/README.md) — Struktur & checklist

---

### **ws-13: Data Preprocessing — Preprocessing & Persiapan Data untuk Analisis**

**Tujuan:** Data refinement untuk analisis (cleaning, transformation, normalization).

**Data Refinement Pipeline:**
```
Raw Data → Cleaning → Transformation → Normalization → 
Processed Data → Analysis Ready
```

**4 Prinsip Preprocessing:**
1. **Consistency** — Metode sama untuk data yang sama
2. **Transparency** — Setiap langkah terdokumentasi
3. **Reproducibility** — Orang lain bisa mengulang dengan hasil sama
4. **Minimal Distortion** — Ubah sesedikit mungkin

**Cleaning Triad:**
- Missing values (listwise deletion, imputation, flag & separate)
- Duplikat (identifikasi → verifikasi → hapus)
- Error format (standardisasi tipe, encoding)

**Normalisasi (Kapan & Metode):**
- Min-max: (x-min)/(max-min) → [0,1] (sensitif outlier)
- Z-score: (x-mean)/std → unbounded (lebih robust)
- Robust scaling: (x-median)/IQR → unbounded (paling robust)

**Critical:** Normalization params hitung dari **training set saja** (bukan semua data) → prevent **data leakage**

**Deliverable:**
- Cleaning log (keputusan per langkah, justifikasi)
- Processed dataset (CSV/JSON)
- Data leakage prevention report

**Tempat Penyimpanan:**
- [06-output/preprocessing/](../06-output/preprocessing/) — Cleaning & transformation
- [06-output/preprocessing/cleaning_log.md](../06-output/preprocessing/cleaning_log.md) — Dokumentasi
- [06-output/preprocessing/processed_data.csv](../06-output/preprocessing/processed_data.csv) — Hasil

---

## FASE 3: ANALISIS & PERTAHANAN (ws-14 hingga ws-16)

### **ws-14: Analysis, Interpretation & Failure Analysis — Analisis Data, Interpretasi & Failure Analysis**

**Tujuan:** Transformasi data → analysis → interpretation → knowledge.

**Data → Knowledge Model:**
```
Data → Analysis → Interpretation → Explanation → Knowledge
```

**Beyond p-value:**
Selalu laporkan:
1. **p-value** (signifikansi statistik)
2. **Effect size** (besarnya efek) — Cohen's d: <0.2 small, 0.2-0.8 medium, >0.8 large
3. **Confidence interval** (rentang ketidakpastian)

**Pemilihan Uji Statistik:**
- 2 grup normal paired → Paired t-test
- 2 grup non-normal → Wilcoxon signed-rank
- > 2 grup normal → One-way ANOVA + post-hoc
- > 2 grup non-normal → Kruskal-Wallis + post-hoc
- 2 variabel kontinu → Pearson (normal) / Spearman (rank)

**Failure Analysis as Contribution:**
Hipotesis ditolak = temuan berharga (boundary condition, context limitation). Dokumentasikan:
- Dataset mana hipotesis ditolak?
- Mengapa?
- Apa implikasinya?

**Deliverable:**
- Analysis report (tabel → pattern → insight dengan p-value + effect size + CI)
- Failure analysis (negative results dengan konteks & learning)
- Interpretation vs literatur

**Tempat Penyimpanan:**
- [06-output/analysis/analysis_report.md](../06-output/analysis/analysis_report.md) — Analysis lengkap
- [06-output/analysis/failure_analysis.md](../06-output/analysis/failure_analysis.md) — Negative results

---

### **ws-15: Scientific Writing — Penulisan Ilmiah**

**Tujuan:** Menulis paper ilmiah dengan red thread jelas (Problem → Contribution).

**Scientific Argument Flow:**
```
Problem → Gap → RQ → Method → Result → Analysis → Conclusion → Contribution
```

**Struktur IMRAD:**

| Section | Peran | Pertanyaan |
|---------|-------|-----------|
| **Introduction** | Motivasi & frame | Why is this needed? |
| **Method** | Deskripsi reproducible | How was it done? |
| **Results** | Laporan objektif | What was found? |
| **Discussion** | Interpretasi & refleksi | What does it mean? |
| **Conclusion** | Ringkasan & kontribusi | So what? |

**Logical Flow — Red Thread:**
- Antar-kalimat: Setiap kalimat lanjut dari sebelumnya
- Antar-paragraf: Paragraf dalam section punya coherence
- Antar-section: Alur logis Intro → Method → Results → Discussion → Conclusion

**Internal Consistency Matrix:**
Verifikasi setiap RQ/metrik/variabel muncul konsisten di semua section.

**Writing Quality Triad:**
1. **Clarity** — Kalimat jelas, bukan ambigu
2. **Conciseness** — Tidak bertele-tele
3. **Correctness** — Grammar, terminology, citation format

**Deliverable:**
- Paper lengkap IMRAD (5-8 halaman typical)
- Per section: outline → draf → revisi
- Bibliography (format target journal)

**Tempat Penyimpanan:**
- [07-manuskrip/](../07-manuskrip/) — Per-section markdown
- [07-manuskrip/naskah-jurnal.md](../07-manuskrip/naskah-jurnal.md) — Paper final
- [02-literatur/daftar-pustaka.bib](../02-literatur/daftar-pustaka.bib) — Bibliography

---

### **ws-16: Presentation & Defense — Presentasi & Pertahanan Ilmiah (UAS)**

**Tujuan:** Komunikasikan riset & pertahankan argumen ilmiah.

**Scientific Defense Model:**
```
Research Work → Presentation → Questioning → Defense → Evaluation → Acceptance
```

**Presentasi ≠ Ringkasan Paper:**

| Aspek | Paper | Presentasi |
|------|-------|-----------|
| Media | Dibaca (self-paced) | Didengar (presenter-paced) |
| Isi | Detail lengkap | Ide kunci + highlight |
| Format | Tabel numerik detail | Grafik visual + angka kunci |
| Audiens | Pembaca bisa re-read | Audiens dengar sekali |

**Presentasi membutuhkan REFORMULASI, bukan kompresi.**

**Optimal 9-Slide Plan (15 menit):**

| Slide | Konten | Waktu | Pesan |
|-------|--------|-------|-------|
| 1 | Title + context | 1 min | Apa ini tentang? |
| 2 | Problem + motivation | 2 min | Mengapa penting? |
| 3 | Gap + RQ | 1.5 min | Apa belum dijawab? |
| 4 | Method overview | 2 min | Bagaimana dijawab (diagram)? |
| 5 | Key result — tabel | 2 min | Temuan utama |
| 6 | Visualisasi hasil | 2 min | Grafik penting |
| 7 | Discussion & limitation | 2 min | Konteks & batasan |
| 8 | Conclusion & contribution | 1.5 min | So what? |
| 9 | Q&A / Backup | flex | Siap pertanyaan |

**Claim-Evidence-Reasoning (CER) untuk Defense:**

Setiap jawaban harus punya:
1. **Claim** — Pernyataan/jawaban
2. **Evidence** — Data/fakta pendukung
3. **Reasoning** — Logika connecting evidence → claim

**Deliverable:**
- Slide presentasi (9 slide optimal)
- Backup slides (5-10 untuk anticipate pertanyaan)
- CER FAQ (pertanyaan antisipasi + jawaban)

**Tempat Penyimpanan:**
- [08-laporan/](../08-laporan/) — Slide & backup
- [08-laporan/laporan-penelitian.md](../08-laporan/laporan-penelitian.md) — Report final
- [08-laporan/README.md](../08-laporan/README.md) — Defense prep

---

## Summary: Red Thread Riset

```
┌─────────────────────────────────────────────────────────────────┐
│                  FASE 1: PROPOSAL (ws-01-08)                   │
│                                                                 │
│  ws-01: Paradigma & Validitas                                   │
│    ↓                                                             │
│  ws-02: Problem Statement                                       │
│    ↓ (gap teridentifikasi)                                      │
│  ws-03: Literature Gap                                          │
│    ↓ (RQ dirumuskan untuk jawab gap)                            │
│  ws-04: RQ & Hypothesis                                         │
│    ↓ (metrik operasionalisasi variabel)                         │
│  ws-05: Variabel & Metrik                                       │
│    ↓ (sistem desain untuk ukur metrik)                          │
│  ws-06: System-Experiment Mapping                               │
│    ↓ (desain eksperimen valid)                                  │
│  ws-07: Experimental Design                                     │
│    ↓ (koherensi proposal)                                       │
│  ws-08: Proposal Integration (UTS Checkpoint)                   │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
         ↓
┌─────────────────────────────────────────────────────────────────┐
│              FASE 2: IMPLEMENTASI & EKSEKUSI (ws-09-13)         │
│                                                                 │
│  ws-09: Implementation (reproducible environment)               │
│    ↓                                                             │
│  ws-10: Experiment Execution (multiple runs, logging)           │
│    ↓                                                             │
│  ws-11: Data Validation (4 pilar quality)                       │
│    ↓                                                             │
│  ws-12: Result Presentation (tabel & grafik)                    │
│    ↓                                                             │
│  ws-13: Data Preprocessing (cleaning & transformation)          │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
         ↓
┌─────────────────────────────────────────────────────────────────┐
│             FASE 3: ANALISIS & PERTAHANAN (ws-14-16)            │
│                                                                 │
│  ws-14: Analysis & Interpretation (p-value + effect size + CI)  │
│    ↓                                                             │
│  ws-15: Scientific Writing (IMRAD red thread)                   │
│    ↓                                                             │
│  ws-16: Presentation & Defense (CER format, 9-slide plan)       │
│         (UAS Checkpoint)                                        │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
         ↓
     ✓ RISET SELESAI & TERPUBLIKASI
```

---

## Catatan Penting

1. **Benang Merah:** Setiap tahap membangun di atas yang sebelumnya. Jika ada lompatan → koherensi hilang.
2. **Dokumentasi:** Setiap keputusan (desain, preprocessing, analisis) harus terdokumentasi dengan justifikasi.
3. **Reproducibility:** Orang lain harus bisa follow dokumentasi → hasil sama/serupa.
4. **Red Thread:** Problem → Gap → RQ → Metrik → Sistem → Eksperimen → Analisis → Paper.

---

*Terakhir diupdate: 2025 — Aligned dengan ws-01 hingga ws-16*

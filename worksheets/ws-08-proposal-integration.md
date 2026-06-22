# WS-08: Proposal Integration (UTS)

> **Bab 8 — Proposal & Checkpoint**

---

## Ringkasan Materi

### Proposal = Satu Argumen Utuh

Proposal riset bukan kumpulan bab yang independen. Ia adalah **satu argumen** yang mengalir dari masalah ke rencana solusi. Jika satu koneksi putus, seluruh proposal kehilangan koherensi.

### Integration Map — 6 Koneksi Kritis

```
Problem (Bab 2) → Gap (Bab 3) → RQ & H (Bab 4) → Metrik (Bab 5) → Sistem (Bab 6) → Eksperimen (Bab 7)
```

| Koneksi | Pertanyaan Verifikasi |
|---------|----------------------|
| Problem → Gap | Apakah gap muncul dari analisis literatur terhadap masalah? |
| Gap → RQ | Apakah RQ langsung menjawab gap yang teridentifikasi? |
| RQ → Metrik | Apakah setiap variabel di RQ punya metrik terdefinisi? |
| Metrik → Sistem | Apakah setiap metrik bisa diukur oleh komponen sistem? |
| Sistem → Eksperimen | Apakah desain eksperimen menggunakan sistem sebagai instrumen? |

### Koherensi Vertikal + Horizontal

- **Vertikal** — Alur logis atas-ke-bawah (problem → experiment). Setiap section menjawab pertanyaan yang diangkat section sebelumnya dan memunculkan pertanyaan baru.
- **Horizontal** — Konsistensi terminologi (nama variabel di RQ = di hipotesis = di metrik = di desain)

**Operasionalisasi Red Thread** (benang merah):
```
Bab 2 (Problem) → | memperkenalkan masalah X + evidensi |
                          ↓ menimbulkan pertanyaan: "apa akar gap-nya?"
Bab 3 (Gap)     → | menjawab pertanyaan tadi + membuka "lalu apa yang perlu diteliti?" |
                          ↓
Bab 4 (RQ/H)    → | menjawab gap dengan pertanyaan spesifik + prediksi terukur |
                          ↓
Bab 5-7 (Method)→ | menjawab RQ melalui desain eksperimen yang tepat |
```
Jika ada lompatan (section B tidak menjawab pertanyaan section A), red thread putus.

### Jebakan Kognitif

| Jebakan | Deskripsi |
|---------|----------|
| "Selling" Introduction | Menulis promosi, bukan menyajikan data dan gap |
| Copy-paste Methodology | Menyalin deskripsi tekstbook tanpa menyesuaikan ke RQ |
| Optimistic Timeline | Meremehkan waktu implementasi; selalu tambah buffer 30-50% |
| No Possibility of Failure | Mengimplikasikan hasil pasti sukses — proposal jujur mengakui H₀ mungkin tidak ditolak |

### Struktur Proposal

1. **Pendahuluan** — Latar belakang + problem statement (Bab 1-2)
2. **Tinjauan Pustaka** — Literature review + gap + baseline (Bab 3)
3. **RQ / Kontribusi / Hipotesis** — (Bab 4)
4. **Metodologi** — Metrik + sistem + desain eksperimen (Bab 5-7)
5. **Timeline & Output**

### Istilah Penting

- **Integration Map** — Diagram 6 koneksi kritis antar komponen proposal
- **Vertical Coherence** — Alur logis atas-ke-bawah
- **Horizontal Coherence** — Konsistensi terminologi di semua bagian
- **Checkpoint** — Titik self-assessment sebelum transisi dari desain ke eksekusi

---

## Template A.8 — Integration Checklist

```
PROPOSAL INTEGRATION CHECKLIST

Koneksi Vertikal (Flow Atas-Bawah):
  [✓] Problem → Gap: masalah terdokumentasi di literatur
  [✓] Gap → RQ: pertanyaan menjawab gap spesifik
  [✓] RQ → Hypothesis: hipotesis memprediksi jawaban
  [✓] Hypothesis → Metric: metrik mengukur variabel dalam hipotesis
  [✓] Metric → System: komponen sistem menghasilkan/mengukur metrik
  [✓] System → Experiment: desain eksperimen menggunakan sistem

Koneksi Horizontal (Konsistensi):
  [✓] Istilah sama di semua bagian
  [✓] Variabel di RQ = variabel di hipotesis = metrik di desain
  [✓] Scope tidak berubah dari masalah ke eksperimen

Cognitive Trap Checklist:
  [ ] Tidak ada paragraf "promosi" di pendahuluan (hanya data & gap)
  [ ] Metodologi disesuaikan ke RQ, bukan copy-paste textbook
  [ ] Timeline sudah ditambah buffer 30-50% dari estimasi awal
  [ ] Proposal mengakui kemungkinan H0 tidak ditolak (honest uncertainty)
  [ ] Tidak ada klaim "pasti berhasil" atau "meningkatkan signifikan"

Rubrik Self-Assessment:

| Kriteria     | 1 (Lemah) | 2 (Cukup) | 3 (Baik) | Skor |
|--------------|------------|------------|-----------|------|
| Koherensi    |            |            | ✓         | 3    |
| Specificity  |            |            | ✓         | 3    |
| Feasibility  |            | ✓          |           | 2    |
| Rigor        |            | ✓          |           | 2    |

Total Skor: 10 / 12
```

---

## Latihan 1 — Kompilasi Proposal Mini

Kumpulkan hasil dari WS-02 sampai WS-07 menjadi satu ringkasan proposal.

| Komponen | Sumber | Isi (1-2 kalimat) |
|-----------|--------|-------------------|
| Problem Statement | WS-02 | Penggunaan ChatGPT untuk mencari informasi mental health semakin meningkat di kalangan mahasiswa. Namun, informasi dari AI dapat memicu kecenderungan self-diagnosis gangguan mental seperti Borderline Personality Disorder (BPD) tanpa validasi profesional. |
| Gap | WS-03 | Sebagian besar penelitian masih bersifat kualitatif dan literature review, serta belum ada penelitian yang secara spesifik membahas pengaruh ChatGPT terhadap self-diagnosis BPD pada mahasiswa menggunakan pendekatan NLP dan data empiris. |
| RQ | WS-04 | Bagaimana pengaruh penggunaan ChatGPT terhadap kecenderungan self-diagnosis Borderline Personality Disorder (BPD) pada mahasiswa berdasarkan interpretasi informasi mental health yang diberikan AI? |
| Hipotesis | WS-04 | H₁: Penggunaan ChatGPT memiliki pengaruh terhadap meningkatnya kecenderungan self-diagnosis BPD pada mahasiswa. |
| Variabel & Metrik | WS-05 | IV = penggunaan ChatGPT; DV = kecenderungan self-diagnosis BPD; CV = literasi mental health. Metrik menggunakan skor Likert, keyword extraction, dan sentiment analysis. |
| Sistem | WS-06 | Sistem terdiri dari modul input data, preprocessing teks, keyword extraction, sentiment analysis, dan visualisasi hasil analisis. |
| Desain Eksperimen | WS-07 | Penelitian menggunakan comparison study antara mahasiswa dengan tingkat penggunaan ChatGPT tinggi dan rendah menggunakan data kuesioner dan analisis NLP sederhana. |

---

## Latihan 2 — Integration Checklist

Verifikasi 6 koneksi kritis. Isi dengan merujuk tabel di Latihan 1.

| Koneksi | Status | Bukti |
|-----------|--------|--------|
| Problem → Gap | ✅ | Gap ditemukan dari beberapa jurnal yang belum membahas ChatGPT dan self-diagnosis BPD secara spesifik |
| Gap → RQ | ✅ | RQ secara langsung membahas pengaruh ChatGPT terhadap self-diagnosis BPD |
| RQ → Hypothesis | ✅ | Hipotesis memprediksi adanya pengaruh penggunaan ChatGPT terhadap self-diagnosis |
| Hypothesis → Metric | ✅ | Hipotesis diukur menggunakan skor Likert, keyword extraction, dan sentiment analysis |
| Metric → System | ✅ | Sistem NLP digunakan untuk menghasilkan keyword dan analisis sentimen |
| System → Experiment | ✅ | Sistem digunakan sebagai alat analisis pada eksperimen comparison study |

**Koneksi mana yang paling lemah?** system
**Bagaimana cara memperkuatnya?**
> Menambahkan penjelasan lebih detail mengenai proses NLP, preprocessing data, dan cara sistem menghasilkan analisis keyword serta sentimen.

**Konsistensi horizontal — apakah istilah dan scope konsisten?** [✓] Ya / [ ] Tidak
Istilah penggunaan ChatGPT, self-diagnosis BPD, mahasiswa, dan NLP digunakan secara konsisten di seluruh bagian proposal.

---

## Latihan 3 — Rubrik Self-Assessment

Evaluasi proposal mini menggunakan rubrik.

| Kriteria | Skor (1-3) | Justifikasi |
|-----------|-------------|--------------|
| Koherensi | 3 | Alur dari problem, gap, RQ, hingga eksperimen sudah saling terhubung |
| Specificity | 3 | Variabel, metrik, dan metode penelitian sudah dijelaskan secara spesifik |
| Feasibility | 2 | Penelitian memungkinkan dilakukan, tetapi pengumpulan data responden membutuhkan waktu |
| Rigor | 2 | Metode sudah cukup jelas, namun analisis NLP masih sederhana |

**Skor total:** 10 / 12

**Apakah proposal siap untuk fase eksekusi?** [ ] Ya / [✓] Belum
> Jika belum, apa yang perlu diperbaiki? 
Proposal sudah memiliki alur yang jelas, tetapi perlu memperjelas detail implementasi NLP dan teknik analisis data sebelum tahap pelaksanaan.

---

## Refleksi

> Dari seluruh proses WS-01 sampai WS-08, bagian mana yang paling mudah dan paling sulit? Mengapa? Apa yang akan dilakukan berbeda jika mengulang dari awal?

**Bagian termudah:** Menentukan problem statement dan research gap karena didukung oleh banyak jurnal terkait AI dan self-diagnosis mental health.

**Bagian tersulit:** Menentukan research gap dan menyusun Research Question agar lebih spesifik, terukur, dan sesuai dengan metode penelitian. Selain itu, topik mengenai pengaruh ChatGPT terhadap self-diagnosis BPD pada mahasiswa masih belum banyak dibahas secara spesifik, sehingga cukup sulit mencari referensi dan penelitian terdahulu yang benar-benar sesuai dengan topik penelitian.

**Yang akan dilakukan berbeda:**
Jika mengulang dari awal, saya akan lebih awal menentukan fokus metode penelitian agar proses penyusunan variabel, metrik, dan eksperimen menjadi lebih konsisten.

Saya juga akan mencari dataset dan referensi NLP lebih awal supaya desain sistem dan analisis data lebih matang sejak awal.

# WS-03: Literature Mapping & Gap

> **Bab 3 — Literature Review, Research Gap & Baseline**

---

## Ringkasan Materi

### Literature Review = Positioning, Bukan Ringkasan

Literature review bukan merangkum paper satu per satu. Pendekatan yang benar adalah **concept-centric** — organisasi berdasarkan tema, metode, atau variabel. Tujuan: menemukan **pola, kontradiksi, dan gap**.

### Empat Jenis Research Gap

| Jenis Gap | Deskripsi | Contoh |
|-----------|----------|--------|
| **Performance Gap** | Performa belum memadai | Akurasi deteksi hanya 78% pada kasus tertentu |
| **Method Gap** | Pendekatan belum diterapkan | Belum ada yang pakai transformer untuk task ini |
| **Data Gap** | Dataset terbatas/tidak representatif | Semua studi pakai dataset sintetis |
| **Context Gap** | Belum diuji pada konteks berbeda | Belum ada evaluasi di negara berkembang |

Gap terkuat = kombinasi 2+ jenis.

### Systematic Search Strategy

1. **Database**: IEEE Xplore, ACM DL, Scopus, Google Scholar
2. **Boolean query** yang terdokumentasi eksplisit
3. **Snowballing**: backward (telusuri referensi) + forward (cari yang mengutip)
4. Klaim "belum ada penelitian" harus didukung **bukti pencarian**

### Baseline Selection — 3 Kriteria

| Kriteria | Pertanyaan |
|----------|-----------|
| **Relevan** | Apakah menyelesaikan masalah yang sama? |
| **Representatif** | Apakah mewakili common practice? |
| **State-of-the-Art** | Apakah terbaru/terbaik? |

Membandingkan deep learning 2024 dengan decision tree sederhana tanpa justifikasi = **straw man comparison** (perbandingan tidak jujur).

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan baca literatur | Mencari solusi yang sudah ada | Memahami apa yang belum terjawab |
| Cara membaca paper | Tutorial, how-to | Metode, limitasi, gap |
| Baseline | Framework terpopuler | State-of-the-art yang rigorous |
| Dokumentasi pencarian | Tidak diperlukan | Wajib (reproducible) |

### Istilah Penting

- **Concept-centric** — Organisasi literatur berdasarkan konsep/metode, bukan per penulis
- **Snowballing** — Backward (telusuri referensi) + Forward (cari yang mengutip paper kunci)
- **Research Position** — Pernyataan eksplisit posisi riset terhadap studi sebelumnya
- **Straw man comparison** — Memilih baseline lemah agar metode sendiri terlihat lebih baik

---

## Template A.3 — Literature Mapping & Gap Identification

```
LITERATURE MAPPING

Topik      : Pengaruh penggunaan AI (ChatGPT) terhadap self-diagnosis Borderline Personality Disorder (BPD) pada mahasiswa
Database   : Google Scholar, PubMed
Query      : ("AI chatbot" OR "ChatGPT") AND ("self diagnosis" OR "mental health self assessment") AND ("BPD" OR "borderline personality disorder") AND ("students")
Tahun      : 2019 -2024
Hasil awal : 20 paper → Screening → 5 paper final

Literature Matrix (concept-centric):

| Study | Tahun | Method | Data | Result | Limitation |
|-------|-------|--------|------|--------|------------|
|   Fadhillah & Lestari    |    2024   |     Kualitatif (studi kasus)   |   3 mahasiswa psikologi (wawancara)   |    AI membantu tugas & memberi informasi mental health, tetapi memicu self-diagnosis dan ketergantungan    |      Sampel sangat kecil, tidak spesifik BPD, tidak mengukur akurasi diagnosis      |
|   Chung & Teo    |    2022   |     Systematic Literature Review (PRISMA)   |   142 paper awal → 30 paper final   |    Machine learning efektif untuk prediksi berbagai gangguan mental dengan akurasi bervariasi (±60%–96%)    |      Banyak studi pakai data kecil, tidak fokus chatbot/ChatGPT, tidak membahas self-diagnosis      |
|   Wimbarti et al.    |    2024   |     Critical Review   |   Literatur terkait AI & self-diagnosis mental health   |    Self-diagnosis menggunakan AI berisiko (misinformasi, kesalahan interpretasi, dampak psikologis & sosial)    |      Tidak spesifik mahasiswa, tidak fokus BPD, tidak ada data empiris      |
|   Sukmawati et al.    |    2023   |     Systematic Literature Review   |   Literatur tentang self-diagnosis & mental health literacy   |    Terdapat hubungan antara mental health literacy dengan perilaku self-diagnosis, serta ada potensi dampak positif    |      Tidak spesifik AI/ChatGPT, tidak fokus BPD, tidak berbasis data empiris langsung     |
|   Fajarica et al.    |    2023   |     Kualitatif / studi media audience  |   Remaja (pengguna media digital)   |    Remaja cenderung melakukan self-diagnosis dari informasi digital yang dikonsumsi    |      Tidak spesifik AI/ChatGPT, tidak fokus BPD, bukan mahasiswa     |

Pola yang ditemukan:
  Metode dominan     : Systematic literature review, critical review, dan kualitatif (studi kasus)
  Dataset umum       : Literatur (secondary data) dan sampel kecil (mahasiswa/remaja)
  Limitasi berulang  : Tidak spesifik BPD, tidak fokus pada ChatGPT secara langsung, banyak penelitian tidak berbasis data empiris, serta cakupan responden terbatas

GAP IDENTIFICATION

Gap 1: Method + Data Gap
  Deskripsi    : Sebagian besar penelitian masih menggunakan metode kualitatif atau literature review, belum banyak penelitian yang menguji secara langsung penggunaan AI dalam self-diagnosis mental health.
  Bukti        : Fadhillah (2024) hanya menggunakan 3 responden, sementara Chung (2022), Wimbarti (2024), dan Sukmawati (2023) berbasis literature review.
  Signifikansi : Tanpa data empiris yang kuat, sulit untuk mengukur dampak nyata penggunaan AI terhadap perilaku self-diagnosis, sehingga diperlukan penelitian dengan pendekatan yang lebih terukur.

Gap 2: Context + Specificity Gap
  Deskripsi    : Belum ada penelitian yang secara spesifik mengkaji penggunaan ChatGPT dalam self-diagnosis gangguan tertentu seperti Borderline Personality Disorder (BPD) pada mahasiswa.
  Bukti        : Seluruh studi yang dianalisis masih membahas mental health secara umum dan tidak fokus pada BPD maupun penggunaan AI generatif seperti ChatGPT.
  Signifikansi : BPD merupakan gangguan yang kompleks dan sering disalahartikan, sehingga penting untuk diteliti dalam konteks penggunaan AI agar dapat mencegah kesalahan diagnosis mandiri.

Baseline Selection:
| Baseline | Relevansi | Representatif | Source |
|Penggunaan AI pada mahasiswa (self-diagnosis)|Sama-sama membahas AI & perilaku mahasiswa|Mewakili penggunaan nyata AI|Fadhillah et al., 2024|
|Self-diagnosis mental health (tanpa AI spesifik)|Sama-sama membahas self-diagnosis|Banyak digunakan dalam penelitian awal|Sukmawati et al., 2023|
```

---

## Latihan 1 — Concept-Centric Literature Table

Gunakan topik riset dari WS-02. Cari minimal 5 paper relevan menggunakan Google Scholar atau database lain.

**Topik riset:** Pengaruh penggunaan AI (ChatGPT) terhadap self-diagnosis Borderline Personality Disorder (BPD) pada mahasiswa
**Query pencarian:** ("AI chatbot" OR "ChatGPT") AND ("self diagnosis" OR "mental health self assessment") AND ("BPD" OR "borderline personality disorder") AND ("students")
**Database:** Google Scholar, PubMed

| # | Study | Tahun | Method | Dataset | Result | Limitasi |
|---|-------|-------|--------|---------|--------|----------|
| 1 |Fadhillah & Lestari|2024|Kualitatif (studi kasus)|3 mahasiswa psikologi (wawancara)|AI membantu tugas & memberi informasi mental health, tetapi memicu self-diagnosis dan ketergantungan|Sampel sangat kecil, tidak spesifik BPD, tidak mengukur akurasi diagnosis|
| 2 |Chung & Teo|2022|Systematic Literature Review (PRISMA)|142 paper awal → 30 paper final|Machine learning efektif untuk prediksi berbagai gangguan mental dengan akurasi bervariasi (±60%–96%)|Banyak studi pakai data kecil, tidak fokus chatbot/ChatGPT, tidak membahas self-diagnosis|
| 3 |Wimbarti et al.|2024|Critical Review|Literatur terkait AI & self-diagnosis mental health|Self-diagnosis menggunakan AI berisiko (misinformasi, kesalahan interpretasi, dampak psikologis & sosial)|Tidak spesifik mahasiswa, tidak fokus BPD, tidak ada data empiris|
| 4 |Sukmawati et al.|2023|Systematic Literature Review|Literatur tentang self-diagnosis & mental health literacy|Terdapat hubungan antara mental health literacy dengan perilaku self-diagnosis, serta ada potensi dampak positif|Tidak spesifik AI/ChatGPT, tidak fokus BPD, tidak berbasis data empiris langsung|
| 5 |Fajarica et al.    |    2023   |     Kualitatif / studi media audience  |   Remaja (pengguna media digital)   |    Remaja cenderung melakukan self-diagnosis dari informasi digital yang dikonsumsi    |      Tidak spesifik AI/ChatGPT, tidak fokus BPD, bukan mahasiswa     |

**Pola yang terlihat — Metode dominan:** Systematic literature review, critical review, dan kualitatif (studi kasus)

**Limitasi yang berulang:** Tidak spesifik BPD, tidak fokus pada ChatGPT secara langsung, banyak penelitian tidak berbasis data empiris, serta cakupan responden terbatas

---

## Latihan 2 — Gap Identification

Berdasarkan tabel di Latihan 1, identifikasi gap.

| Jenis Gap | Ditemukan? | Gap Statement |
|-----------|-----------|---------------|
| Performance Gap | [ ] Ya / [☑] Tidak | Tidak ditemukan pengukuran performa karena sebagian besar penelitian tidak menguji akurasi AI dalam diagnosis secara langsung |
| Method Gap | [☑] Ya / [ ] Tidak |Sebagian besar penelitian menggunakan metode kualitatif dan literature review, sehingga belum banyak penelitian empiris kuantitatif yang menguji penggunaan ChatGPT dalam self-diagnosis|
| Data Gap | [☑] Ya / [ ] Tidak |Data yang digunakan masih terbatas, seperti sampel kecil atau hanya berbasis literatur, sehingga kurang representatif|
| Context Gap | [☑] Ya / [ ] Tidak |Belum ada penelitian yang secara spesifik mengkaji penggunaan ChatGPT dalam self-diagnosis BPD pada mahasiswa|

**Gap utama yang dipilih:** Method + Context Gap
**Mengapa gap ini penting (bukan sekadar "belum ada yang meneliti")?**
> Gap ini penting karena meskipun penelitian sebelumnya telah membahas penggunaan AI dan fenomena self-diagnosis dalam kesehatan mental, sebagian besar masih bersifat konseptual dan belum berbasis data empiris. Selain itu, belum terdapat kajian yang secara spesifik meneliti penggunaan ChatGPT dalam self-diagnosis gangguan tertentu seperti Borderline Personality Disorder (BPD) pada mahasiswa. Mengingat kompleksitas BPD dan tingginya penggunaan AI di kalangan mahasiswa, penelitian ini diperlukan untuk memahami dampak nyata serta potensi risiko yang dapat ditimbulkan, sehingga dapat memberikan kontribusi yang lebih relevan secara akademik maupun praktis.

---

## Latihan 3 — Baseline Selection

Pilih 2 baseline dari literatur yang sudah dibaca.

| # | Baseline | Mengapa Relevan | Mengapa Representatif | Apakah SOTA? | Sumber |
|---|----------|----------------|----------------------|-------------|--------|
| 1 | |Penggunaan AI pada mahasiswa (self-diagnosis)|Sama-sama membahas AI & perilaku mahasiswa|Mewakili penggunaan nyata AI|Bukan, tapi common practice|Fadhillah et al., 2024|
| 2 |Self-diagnosis mental health (tanpa AI spesifik)|Sama-sama membahas self-diagnosis|Banyak digunakan dalam penelitian awal|Bukan|Sukmawati et al., 2023|

**Apakah pemilihan baseline ini bisa dianggap straw man?** [ ] Ya / [☑] Tidak
> Justifikasi: Baseline dipilih dari penelitian yang relevan dengan topik dan mewakili kondisi nyata di lapangan, sehingga tidak menggunakan metode yang lemah untuk memperkuat hasil penelitian secara tidak adil.

---

## Refleksi

> Apa perbedaan antara "belum ada yang meneliti ini" (klaim tanpa bukti) dengan research gap yang valid? Bagaimana cara membuktikan bahwa sebuah gap benar-benar ada?

**Jawaban:**
>Perbedaan antara “belum ada yang meneliti ini” dengan research gap yang valid adalah pada adanya bukti yang mendukung. Klaim tanpa bukti hanya berupa asumsi, sedangkan research gap yang valid didasarkan pada hasil analisis beberapa penelitian yang menunjukkan keterbatasan atau kekurangan yang konsisten.
> Cara membuktikan gap adalah dengan melakukan pencarian literatur secara sistematis menggunakan database ilmiah, kemudian membandingkan beberapa penelitian untuk menemukan pola dan keterbatasan yang berulang. Dengan demikian, gap yang dihasilkan benar-benar berdasarkan data dan analisis, bukan sekadar pendapat.

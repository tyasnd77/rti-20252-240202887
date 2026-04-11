# WS-01: Distorsi & Paradigma

> **Bab 1 — Research Mindset in IT**

---

## Ringkasan Materi

### Research Trust Model

Pengetahuan ilmiah tidak muncul langsung dari kenyataan. Ia melewati **6 tahap transformasi** yang masing-masing rawan distorsi:

```
Reality → Data → Processing → Analysis → Inference → Knowledge
```

Etika mencegah distorsi yang disengaja (fabrikasi, cherry-picking). Validitas mendeteksi distorsi yang tidak disengaja (confounding variable, sampling bias).

### Tiga Jenis Validitas

| Jenis | Pertanyaan | Contoh Ancaman |
|-------|-----------|----------------|
| **Internal Validity** | Apakah hubungan kausal benar ada? | Confounding variable |
| **External Validity** | Apakah bisa digeneralisasi? | Dataset terlalu homogen |
| **Construct Validity** | Apakah mengukur hal yang benar? | Metrik tidak sesuai klaim |

### Paradigma Riset

Mata kuliah ini menggunakan pendekatan **Positivist** (fenomena TI bisa diukur objektif melalui eksperimen terkontrol) diperkuat **Design Science Research** (artefak dibuat sebagai instrumen pengujian hipotesis, bukan tujuan akhir).

### Mode Berpikir Peneliti

**Curious** (mempertanyakan fenomena) → **Critical** (mengevaluasi klaim berdasarkan bukti) → **Systematic** (merancang investigasi terstruktur dan reproducible).

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan | Membuat sistem yang bekerja | Menghasilkan pengetahuan yang valid |
| Pertanyaan khas | "Bagaimana membuatnya jalan?" | "Apakah klaim ini benar?" |
| Ukuran sukses | Sistem berfungsi, client puas | Hipotesis terjawab, temuan tervalidasi |
| Kegagalan | Harus dihindari | Harus dilaporkan (negative result = kontribusi) |

### Istilah Penting

- **Research Mindset** — Pola pikir yang menuntut bukti dan mempertanyakan asumsi
- **Research Ethics** — Prinsip perilaku: kejujuran, objektivitas, keterbukaan, akuntabilitas
- **HARKing** — Hypothesizing After Results are Known — merumuskan hipotesis setelah melihat data
- **Falsifiability** — Hipotesis harus bisa dibuktikan salah

---

## Template A.1 — Research Mindset Self-Assessment

```
Nama Peneliti    : Tyas Nurshika Damaia
Tanggal          : 6 April 2026

1. Ketika membaca klaim "metode X 95% akurat":
   - Pertanyaan pertama saya: Bagaimana metode pengukuran akurasi dilakukan dan dataset apa yang digunakan?
   - Data yang dibutuhkan untuk verifikasi: Dataset rating pengguna, jumlah data (user & film), metode evaluasi (confusion matrix, MAE), serta pembagian data training dan testing.

2. Posisi paradigma:
   - Pendekatan: [ ☑] Positivis  [ ] Interpretivis  [☑] Design Science  [ ] Mixed
   - Alasan: Penelitian menggunakan data kuantitatif berupa rating pengguna dan melakukan eksperimen menggunakan algoritma Matrix Factorization untuk mengukur akurasi sistem secara objektif.
3. Identifikasi distorsi:
   - Asumsi tersembunyi: Data rating pengguna dianggap mewakili preferensi sebenarnya pengguna secara akurat.
   - Sumber bias potensial: Dataset yang digunakan terbatas (hanya sekitar 200 pengguna dan 30 film), serta data bersifat sparse (banyak nilai kosong).
   - Langkah mitigasi: Menggunakan metode Matrix Factorization (SVD) untuk mengatasi kekosongan data dan meningkatkan akurasi prediksi.

4. Komitmen etika:
   - Data yang tidak akan dimanipulasi: Data rating pengguna asli dan hasil evaluasi (accuracy, precision, recall, MAE).
   - Batasan yang diakui sejak awal: Dataset memiliki tingkat sparsity tinggi (sekitar 78,78%) sehingga dapat mempengaruhi hasil akurasi sistem.
```

---

## Latihan 1 — Identifikasi Distorsi

Pilih satu paper riset di bidang TI yang mengklaim "metode X meningkatkan performa." Telusuri setiap tahap Research Trust Model.

**Paper yang dipilih:**

- Judul: Sistem Rekomendasi Film Berbasis Collaborative Filtering Menggunakan Algoritma Matrix Factorization
- Penulis (Tahun): Farah Zhafira Munthe & Farid Akbar Siregar (2025)

| Tahap | Apa yang Dilakukan | Potensi Distorsi |
|-------|-------------------|-----------------|
| Reality → Data | Mengumpulkan data rating pengguna terhadap film (±200 user, 30 film)|Dataset kecil dan tidak representatif, hanya mencakup sedikit film dan pengguna |
| Data → Processing | Data dibentuk menjadi matriks user-item, terdapat banyak data kosong (sparsity tinggi) | Data kosong dapat menyebabkan bias karena tidak semua preferensi pengguna terekam |
| Processing → Analysis | Menggunakan Matrix Factorization dengan metode SVD untuk memprediksi rating | Model bisa overfitting atau terlalu menyesuaikan dengan data yang terbatas |
| Analysis → Inference | Menghitung akurasi menggunakan confusion matrix dan MAE | Pemilihan metrik bisa menyesatkan (misalnya hanya fokus pada accuracy tanpa konteks) |
| Inference → Knowledge | Menyimpulkan bahwa metode cukup akurat dan efektif | Klaim bisa terlalu general padahal hanya diuji pada dataset kecil |

**Distorsi paling besar di tahap:** Reality → Data

**Dua distorsi spesifik yang teridentifikasi:**
1. Dataset yang digunakan terlalu kecil dan tidak merepresentasikan pengguna secara umum sehingga hasil tidak bisa digeneralisasi.
2. Tingkat sparsity (data kosong) yang tinggi menyebabkan sistem memprediksi berdasarkan data terbatas, sehingga akurasi bisa bias.
---

## Latihan 2 — Analisis Kasus Etika

Skenario: Seorang peneliti menemukan bahwa jika 3 data point outlier dihapus, hasil eksperimennya menjadi signifikan. Dengan outlier, hasilnya tidak signifikan.

| Perspektif | Analisis |
|------------|---------|
| Kejujuran ilmiah | Peneliti tidak boleh menghapus data hanya untuk membuat hasil terlihat signifikan. Semua data, termasuk outlier, harus dipertimbangkan atau dijelaskan alasannya jika dihapus. |
| Transparansi | Peneliti harus melaporkan kedua hasil, yaitu dengan outlier dan tanpa outlier, serta menjelaskan alasan penghapusan data tersebut secara jelas. |
| Peer review | Reviewer akan mempertanyakan alasan penghapusan data. Jika tidak ada justifikasi yang kuat, penelitian bisa dianggap bias atau tidak valid. |

**Keputusan akhir dan justifikasi:**
> Data outlier tidak boleh dihapus sembarangan hanya untuk mendapatkan hasil yang signifikan. Peneliti harus menganalisis apakah outlier tersebut merupakan kesalahan data atau bagian dari fenomena yang valid. Jika dihapus, harus disertai alasan yang jelas dan tetap melaporkan kedua hasil (dengan dan tanpa outlier) untuk menjaga kejujuran dan transparansi penelitian.

---

## Latihan 3 — Posisi Paradigma

**Topik riset:** Evaluasi akurasi sistem rekomendasi film berbasis collaborative filtering menggunakan metode Matrix Factorization (SVD)

| Kriteria | Positivis | Interpretivis | Design Science |
|----------|-----------|---------------|----------------|
| Kesesuaian dengan topik (1–5) | 5 | 2 | 5 |
| Jenis data yang dikumpulkan | Data kuantitatif yang dikumpulkan meliputi rating pengguna, jumlah pengguna dan film, jumlah interaksi (rating), tingkat sparsity data, serta hasil evaluasi sistem seperti accuracy, precision, recall, F1-score, confusion matrix, dan Mean Absolute Error (MAE). | Data kualitatif (opini pengguna, wawancara) | Data sistem & hasil implementasi (output rekomendasi) |
| Limitasi paradigma | Tidak menangkap faktor subjektif (selera pengguna) | Sulit diukur secara numerik | Fokus pada sistem, bukan generalisasi luas |

**Paradigma yang dipilih:** Positivis dan Design Science

**Alasan:** Penelitian ini menggunakan pendekatan positivis karena berfokus pada pengukuran akurasi sistem secara kuantitatif menggunakan metrik seperti accuracy, precision, recall, dan MAE. Selain itu, penelitian juga termasuk dalam design science karena melibatkan perancangan dan implementasi sistem rekomendasi sebagai artefak untuk menguji metode yang digunakan.

---

## Refleksi

> Sebelum membaca materi ini, apakah pernah mempertanyakan klaim "95% akurat"? Setelah memahami rantai distorsi, pertanyaan apa yang sekarang akan diajukan saat membaca paper?

**Jawaban:**
Sebelum membaca materi ini, saya cenderung langsung menerima klaim seperti “95% akurat” tanpa mempertanyakan bagaimana hasil tersebut diperoleh. Saya menganggap bahwa angka akurasi yang tinggi sudah cukup untuk membuktikan bahwa suatu metode benar dan efektif.

Namun, setelah memahami konsep Research Trust Model dan potensi distorsi dalam setiap tahap penelitian, saya menyadari bahwa hasil tersebut belum tentu sepenuhnya valid. Banyak faktor yang perlu diperhatikan, seperti kualitas dataset, metode pengolahan data, pemilihan metrik evaluasi, serta kemungkinan bias yang terjadi selama proses penelitian.

Sekarang, ketika membaca sebuah paper, saya akan lebih kritis dengan mempertanyakan sumber data yang digunakan, cara evaluasi dilakukan, serta apakah hasil penelitian tersebut dapat digeneralisasikan atau tidak. Dengan demikian, saya tidak hanya menerima hasil penelitian, tetapi juga mampu menganalisis dan mengevaluasi kebenarannya secara lebih objektif.

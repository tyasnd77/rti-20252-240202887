# WS-06: System-Experiment Mapping

> **Bab 6 — System Design sebagai Experimental Artifact**

---

## Ringkasan Materi

### Sistem = Instrumen Pengujian, Bukan Produk

Seorang engineer bertanya "apakah sistem bekerja?" — seorang peneliti bertanya "apa yang bisa dibuktikan sistem ini?" Sistem dalam riset adalah **artifact** — objek yang sengaja dibuat untuk menguji klaim spesifik.

### System as Experiment Model

```
RQ → Variable → System Component → Experimental Setup → Output
```

Setiap komponen sistem harus bisa ditelusuri ke variabel riset (top-down), dan setiap pengukuran harus menjawab RQ (bottom-up).

### Mapping Variabel ke Komponen

| Tipe Variabel | Peran di Sistem | Contoh |
|---------------|----------------|--------|
| **IV** (Independent) | Modul yang bisa di-toggle/swap | Algoritma A vs B |
| **DV** (Dependent) | Modul pengukuran | Logger, metrics collector |
| **CV** (Control) | Config yang dikunci | Dataset, parameter tetap |

Jika variabel tidak bisa di-map ke komponen apapun → arsitektur perlu didesain ulang.

### 4 Prinsip Desain Eksperimental

| Prinsip | Pertanyaan Kunci |
|---------|-----------------|
| **Traceability** | Komponen ini melayani variabel yang mana? |
| **Modularity** | Bisakah IV diubah tanpa memengaruhi yang lain? |
| **Controllability** | Apakah CV dieksternalisasi ke config file? |
| **Measurability** | Apakah sistem otomatis menghasilkan data yang dibutuhkan? |

### Variable Isolation melalui Arsitektur

- **Modular architecture** — Pisahkan berdasarkan variabel
- **Configuration-driven** — Ubah config (YAML/JSON), bukan code
- **Feature toggles** — On/off flag untuk ablation study

  Contoh config YAML dengan feature toggles:
  ```yaml
  model:
    type: cnn          # IV: ganti "rf" untuk kondisi baseline
  features:
    use_temporal: true  # toggle komponen temporal
    use_normalization: true  # toggle preprocessing
  experiment:
    seed: 42
    runs: 5
  ```
  Dengan pendekatan ini, berbeda kondisi eksperimen = berbeda satu baris config, **tanpa mengubah kode**.

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan sistem | Memenuhi kebutuhan user | Menguji hipotesis, menghasilkan bukti |
| Arsitektur | Optimasi performa & skalabilitas | Optimasi isolasi variabel & reprodusibilitas |
| Konfigurasi | Sering hardcoded | Dieksternalisasi ke config file |
| Fitur tambahan | Menambah nilai user | Menambah noise jika tidak terkait RQ |

### Istilah Penting

- **Artifact** — Objek yang sengaja dibuat untuk memecahkan masalah atau menguji proposisi
- **Traceability** — Kemampuan menelusuri hubungan RQ → variabel → komponen → output
- **Variable Isolation** — Mengubah hanya satu variabel sambil menahan yang lain konstan
- **Ablation Study** — Menguji kontribusi tiap komponen dengan melepasnya satu per satu
- **Configuration-driven Execution** — Semua parameter di config file, bukan hardcoded

---

## Template A.6 — Mapping RQ ke Arsitektur Sistem

```
SYSTEM-EXPERIMENT MAPPING

Research Question:
Bagaimana pengaruh penggunaan ChatGPT terhadap kecenderungan self-diagnosis Borderline Personality Disorder (BPD) pada mahasiswa, menggunakan metode survei kuantitatif dengan analisis regresi, metrik berupa skor skala Likert dan nilai korelasi, dataset berupa data kuesioner mahasiswa, serta dibandingkan dengan baseline mahasiswa yang tidak menggunakan AI dalam self-diagnosis?

Variable → Component Mapping:

| Variabel | Tipe | Komponen Sistem | Cara Manipulasi/Pengukuran |
|----------|------|-----------------|----------------------------|
| Penggunaan ChatGPT | IV | Modul input kuesioner & dataset teks | Mengukur frekuensi penggunaan dan tingkat kepercayaan terhadap AI |
| Self-diagnosis BPD | DV | Modul analisis hasil dan NLP | Mengukur skor self-diagnosis, keyword, dan sentimen |
| Literasi mental health | CV | Modul data responden | Dikontrol melalui pertanyaan latar belakang responden |

4 Prinsip Desain:
[✓] Traceability — Setiap komponen bisa ditelusuri ke variabel
[✓] Variable Isolation — IV bisa diubah tanpa mengubah CV
[✓] Measurement Integration — Pengukuran DV built-in
[✓] Reproducibility — Setup bisa direkonstruksi

Experimental Setup:
Input data     : Dataset Reddit mental health dan data kuesioner mahasiswa
Parameter      : Frekuensi penggunaan ChatGPT, skor Likert, keyword self-diagnosis
Output format  : Grafik, tabel hasil analisis, dan nilai korelasi
```

---

## Latihan 1 — Variable-to-Component Mapping

Gunakan RQ dan variabel dari WS-05. Petakan ke komponen sistem.

**RQ:**Bagaimana pengaruh penggunaan ChatGPT terhadap kecenderungan self-diagnosis Borderline Personality Disorder (BPD) pada mahasiswa, menggunakan metode survei kuantitatif dengan analisis regresi, metrik berupa skor skala Likert dan nilai korelasi, dataset berupa data kuesioner mahasiswa, serta dibandingkan dengan baseline mahasiswa yang tidak menggunakan AI dalam self-diagnosis?

| Variabel | Tipe | Komponen Sistem | Cara Manipulasi / Pengukuran |
|----------|------|-----------------|------------------------------|
| Penggunaan ChatGPT | IV | Modul input data | Mengukur intensitas penggunaan ChatGPT melalui kuesioner |
| Self-diagnosis BPD | DV | Modul NLP dan analisis | Mengukur keyword self-diagnosis dan sentimen |
| Literasi mental health | CV | Modul profil responden | Dikontrol menggunakan pertanyaan tambahan pada kuesioner |

**Apakah semua variabel bisa di-map?** [✓] Ya / [ ] Tidak
> Jika tidak, komponen apa yang perlu ditambahkan? 
Semua variabel sudah memiliki komponen sistem yang sesuai untuk proses pengukuran dan analisis.

---

## Latihan 2 — 4 Prinsip Desain

Evaluasi desain sistem terhadap 4 prinsip.

| Prinsip | Status | Bukti / Penjelasan |
|----------|--------|--------------------|
| Traceability | ✅ | Setiap komponen sistem berhubungan langsung dengan variabel penelitian |
| Modularity | ✅ | Modul input, NLP, dan analisis dipisahkan sehingga mudah dikembangkan |
| Controllability | ✅ | Variabel kontrol dipisahkan dalam data responden |
| Measurability | ✅ | Sistem menghasilkan skor, keyword, dan hasil sentimen secara otomatis |

**Prinsip mana yang paling sulit dipenuhi?** Measurability
**Strategi untuk mengatasinya:**
> Menggunakan indikator yang jelas dan preprocessing data agar hasil NLP lebih konsisten dan mudah dianalisis.
---

## Latihan 3 — Ablation Study Planning

Jika sistem memiliki 3 komponen utama, rencanakan ablation study.

> **Panduan jumlah kondisi:** Untuk 3 komponen (A, B, C), kondisi minimal yang direkomendasikan:
> Full + (-A) + (-B) + (-C) = **4 kondisi dasar**. Jika waktu memungkinkan, tambahkan kombinasi ganda: (-A,-B), (-A,-C), (-B,-C) = **7 kondisi**. Sesuaikan dengan *computational cost* dan tenggat waktu penelitian.

| Kondisi | Komponen A | Komponen B | Komponen C | Hasil yang Diharapkan |
|----------|-------------|-------------|-------------|------------------------|
| Full | ✅ Kuesioner | ✅ Keyword Extraction | ✅ Sentiment Analysis | Hasil analisis lengkap |
| – A | ❌ | ✅ | ✅ | Hasil hanya berdasarkan teks tanpa data responden |
| – B | ✅ | ❌ | ✅ | Pola keyword self-diagnosis tidak terlihat jelas |
| – C | ✅ | ✅ | ❌ | Emosi atau sentimen responden tidak terlihat |

**Komponen mana yang diprediksi paling berkontribusi?** Keyword Extraction
**Mengapa?**
> Karena keyword extraction dapat menunjukkan pola kata yang mengarah pada self-diagnosis seperti “merasa BPD”, “takut ditinggalkan”, atau “emosi tidak stabil”.

---

## Refleksi

> Apa risiko jika sistem dibangun seperti produk (monolitik, fitur lengkap) lalu baru dilakukan eksperimen? Mengapa arsitektur modular penting untuk riset?

**Jawaban:**
Jika sistem dibangun seperti produk yang monolitik dan terlalu banyak fitur, maka proses eksperimen menjadi sulit karena variabel penelitian tidak dapat dipisahkan dengan jelas. Hal tersebut dapat menyebabkan hasil penelitian sulit dianalisis dan kurang valid.

Arsitektur modular penting dalam riset karena setiap komponen dapat diuji secara terpisah, sehingga hubungan antara variabel dan hasil penelitian menjadi lebih jelas serta lebih mudah direproduksi.
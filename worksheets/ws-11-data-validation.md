# WS-11: Data Validation & Integrity

> **Bab 11 — Validasi Data & Integritas**

---

## Ringkasan Materi

### Data Trust Model

```
Raw Data → Data Cleaning → Consistency Check → Validation Process → Trusted Data
```

Data mentah belum bisa dipercaya. Harus melewati pipeline validasi sebelum siap untuk analisis statistik.

### Empat Pilar Data Quality

| Pilar | Deskripsi | Contoh Pelanggaran |
|-------|----------|-------------------|
| **Accuracy** | Nilai dalam range masuk akal | Akurasi = 1.5 (di luar [0,1]) |
| **Consistency** | Format seragam di semua run | Run 1: CSV, Run 2: JSON |
| **Completeness** | Tidak ada data hilang dari plan | 97 dari 100 run tercatat |
| **Validity** | Data sesuai desain eksperimen | Parameter baseline tercampur treatment |

### Proses Validasi Progresif

1. **Format validation** — Tipe file, header, kolom
2. **Range validation** — Nilai dalam batas logis
3. **Consistency validation** — Format seragam antar-run
4. **Logic validation** — Data cocok dengan desain eksperimen

Jika gagal di langkah awal → tidak perlu lanjut.

### Anomaly Detection — 3 Jenis

| Jenis | Deskripsi | Deteksi |
|-------|----------|---------|
| **Statistical outlier** | Nilai di luar distribusi normal | IQR: < Q1-1.5×IQR atau > Q3+1.5×IQR |
| **Contextual anomaly** | Normal absolut, abnormal dalam konteks | Run 1-10: ~91%, Run 11-20: ~88% |
| **Pattern anomaly** | Pola sistematis (bukan random) | Performa menurun berurutan |

**Prinsip:** Detect → Investigate → Document → Decide — **JANGAN langsung hapus.**

### Engineering vs Research Validation

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Tujuan | Data sesuai spesifikasi bisnis | Data layak untuk analisis statistik |
| Missing data | Impute / set default | Investigasi penyebab → dokumentasi |
| Outlier | Bug → fix | Mungkin temuan → investigasi |
| Dokumentasi | Minimal (log error) | Komprehensif (anomali + keputusan) |

### Jebakan Kognitif

1. "Logging otomatis ≠ data benar" → bisa ada bug di logger
2. "Outlier = hapus" → bisa jadi temuan penting
3. "Dataset kecil tidak perlu validasi" → justru lebih rentan
4. "Mean normal = data benar" → [94, 95, 93, **44**, 94] → mean 84% terlihat wajar

---

## Template A.11 — Data Validation Checklist

```
DATA VALIDATION CHECKLIST

Completeness:
  [✓] Semua skenario tercakup
  [✓] Jumlah run sesuai rencana
  [✓] Tidak ada file output hilang

  Missing: 0 dari 10 data points

Format Consistency:
  [✓] Semua file menggunakan format CSV
  [✓] Header konsisten
  [✓] Tipe data konsisten

Range & Logic:
  [✓] Nilai dalam range masuk akal
  [✓] Tidak ada waktu negatif
  [✓] Metrik berada pada rentang valid

  Anomali ditemukan:
  Tidak ada

Cross-Validation:
  [✓] Run identik menghasilkan nilai yang mendekati
  [✓] Hasil sesuai ekspektasi teori

Keputusan:
  [✓] Data siap analisis
  [ ] Perlu cleaning
  [ ] Perlu re-run
```

---

## Latihan 1 — Completeness Check

| Skenario                      | Run Direncanakan | Run Tercatat | Missing | Alasan             |
| ----------------------------- | ---------------- | ------------ | ------- | ------------------ |
| Dataset Kesehatan Mental Umum | 5                | 5            | 0       | Semua run berhasil |
| Dataset Personality Disorder  | 5                | 5            | 0       | Semua run berhasil |


**Total expected:** 10 | **Total actual:** 10 | **Missing:** 0

**Keputusan untuk data missing:**
> Tidak terdapat data yang hilang karena seluruh run berhasil dijalankan sesuai execution plan. Semua output tersimpan dan dapat digunakan untuk tahap analisis berikutnya.

---

## Latihan 2 — Anomaly Investigation

**Dataset sampel :**
| Run | Accuracy (%) |
| --- | ------------ |
| 1   | 91.2         |
| 2   | 90.8         |
| 3   | 91.5         |
| 4   | 89.9         |
| 5   | 91.0         |


**Deteksi outlier:**
data terurut
89.9, 90.8, 91.0, 91.2, 91.5
Q1 = 90.8
Q3 = 91.2
IQR = Q3 − Q1
IQR = 91.2 − 90.8 = 0.4

Batas bawah:
90.8 − (1.5 × 0.4)
= 90.2

Batas atas:
91.2 + (1.5 × 0.4)
= 91.8

Hasil
Q1 = 90.8
Q3 = 91.2
IQR = 0.4
Batas bawah = 90.2
Batas atas = 91.8
Outlier terdeteksi = Tidak ada

**Investigasi (untuk setiap outlier):**

| Outlier   | Nilai | Kemungkinan Penyebab | Keputusan          |
| --------- | ----- | -------------------- | ------------------ |
| Tidak ada | -     | -                    | Data dipertahankan |

---

## Latihan 3 — Validation Report

Buat laporan validasi ringkas untuk dataset eksperimen Anda.

**1. Completeness:** 100% data terkumpul
**2. Format:** [☑] Konsisten / [ ] Ada inkonsistensi: ____
**3. Range check (anomali):** 0
**4. Logic check:** [☑] Parameter sesuai plan / [ ] Ada ketidaksesuaian: ____

**Kesimpulan:** [☑] Data siap analisis / [ ] Perlu tindakan: ____

---

## Refleksi

> Apa perbedaan antara "data yang benar" dan "data yang dipercaya"? Mengapa proses validasi formal diperlukan meskipun data dikumpulkan secara otomatis?

>Data yang benar belum tentu dapat dipercaya apabila tidak melalui proses validasi. Data yang benar hanya menunjukkan bahwa nilai yang tercatat sesuai dengan hasil pengukuran, sedangkan data yang dipercaya telah melalui pemeriksaan kelengkapan, konsistensi, validitas, dan logika sehingga layak digunakan sebagai dasar pengambilan kesimpulan. Meskipun data dikumpulkan secara otomatis, kesalahan masih dapat terjadi akibat bug program, kesalahan konfigurasi, data yang hilang, atau proses logging yang tidak sempurna. Oleh karena itu, validasi formal diperlukan untuk memastikan bahwa data yang digunakan benar-benar mencerminkan hasil eksperimen dan dapat dipertanggungjawabkan secara ilmiah.

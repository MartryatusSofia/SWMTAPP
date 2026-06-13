# 📋 SWMT Test Case Execution Documents
## Ringkasan Dokumen Pengujian

---

## 📁 File-File yang Tersedia

### 1. **TEST_EXECUTION_FORM_CLEAN.html** ✅ **[RECOMMENDED]**
**Format:** Paragraf biasa (tanpa input field)

**Fitur:**
- ✅ 59 Test Case untuk semua fitur SWMT
- ✅ Kolom "Hasil Pengujian" → Garis putus untuk diisi manual
- ✅ Kolom "Kesimpulan" → Status badge "Perlu Diuji"
- ✅ Rapi dan siap untuk cetak (Print-friendly)
- ✅ Bisa dibuka di browser dan di-print sebagai PDF
- ✅ Semua teks dalam Bahasa Indonesia
- ✅ Format 6 kolom yang ringkas

**Cara Menggunakan:**
1. Buka file `TEST_EXECUTION_FORM_CLEAN.html` di browser
2. Jalankan test case satu per satu
3. Catat hasil di kolom "Hasil Pengujian"
4. Tulis PASS/FAIL di kolom "Kesimpulan"
5. Klik Print (Ctrl+P) → Simpan sebagai PDF atau cetak

---

### 2. **TEST_EXECUTION_FORM.html** (Versi Lama)
**Format:** Dengan interactive input field dan select dropdown

**Catatan:** File ini memiliki form interaktif untuk diisi digital, tapi versi CLEAN lebih direkomendasikan untuk laporan formal.

---

### 3. **TEST_CASES_BLACKBOX.md**
**Format:** Markdown documentation

**Fitur:**
- 183 test case lengkap dan detail
- Penjelasan mendalam setiap test
- Format referensi
- Cocok untuk dokumentasi teknis

---

## 🎯 Struktur 59 Test Case (Versi Clean)

| Sesi | Jumlah TC | Deskripsi |
|------|-----------|-----------|
| 1️⃣  | 12 | Autentikasi Siswa |
| 2️⃣  | 8 | Autentikasi Guru |
| 3️⃣  | 8 | Pendaftaran Test |
| 4️⃣  | 6 | Manajemen Kelas |
| 5️⃣  | 6 | Manajemen Registrasi Siswa |
| 6️⃣  | 6 | Eksekusi Test |
| 7️⃣  | 3 | Ekspor Data |
| 8️⃣  | 4 | Fitur Super Admin |
| 9️⃣  | 6 | Keamanan & Kasus Khusus |
| **Total** | **59** | **Semua Fitur SWMT** |

---

## ✨ Fitur Dokumen CLEAN

### Kolom-Kolom:
1. **No.** - Nomor urut (1-59)
2. **Skenario Pengujian** - Deskripsi singkat skenario
3. **Test Case** - Langkah-langkah testing
4. **Hasil yang Diharapkan** - Expected output
5. **Hasil Pengujian** - _(Kosong untuk diisi tester)_
6. **Kesimpulan** - Status "Perlu Diuji" / PASS / FAIL

### Fitur Tambahan:
- ✅ Header dengan logo SWMT
- ✅ Instruksi penggunaan
- ✅ Ringkasan hasil di akhir
- ✅ Form tanda tangan dan catatan tester
- ✅ Professional styling untuk laporan

---

## 📖 Cara Menggunakan Dokumen

### Langkah 1: Buka File
```
Buka file HTML dengan browser:
file:///D:/SEMESTER%206/projek/swmt/TEST_EXECUTION_FORM_CLEAN.html
```

### Langkah 2: Jalankan Test Cases
- Baca setiap test case dengan cermat
- Jalankan sesuai instruksi di kolom "Test Case"
- Catat hasil aktual di kolom "Hasil Pengujian"
- Bandingkan dengan "Hasil yang Diharapkan"

### Langkah 3: Isi Kesimpulan
- PASS ✓ → Jika hasil sesuai dengan yang diharapkan
- FAIL ✗ → Jika hasil tidak sesuai (tulis error di Hasil Pengujian)

### Langkah 4: Simpan Laporan
1. **Print ke PDF:**
   - Tekan Ctrl+P
   - Pilih "Save as PDF"
   - Sesuaikan nama file & lokasi
   - Klik Save

2. **Print Fisik:**
   - Tekan Ctrl+P
   - Pilih printer
   - Rekomendasi: Landscape mode agar semua kolom terlihat

---

## 📊 Template Ringkasan Hasil

Di bagian bawah dokumen terdapat section "RINGKASAN PENGUJIAN" dengan template:
- **Total Test Cases:** 59
- **Test Cases PASS (Lulus):** ___
- **Test Cases FAIL (Gagal):** ___
- **Success Rate (%):** ___
- **Tanggal Pengujian:** ___
- **Nama Tester:** ___
- **Tanda Tangan:** ___
- **Catatan Umum:** (textarea untuk catatan)

---

## 💡 Tips Penggunaan

### Format Laporan Professional:
1. Isi semua 59 test case secara sistematis
2. Gunakan bahasa yang jelas dan singkat di kolom "Hasil Pengujian"
3. Dokumentasikan setiap error/bug yang ditemukan
4. Isi form tanda tangan di akhir
5. Export/Print sebagai PDF untuk arsip

### Untuk Bug Report:
Jika test FAIL, format penulisan di "Hasil Pengujian":
```
Expected: [hasil yang diharapkan]
Actual: [hasil yang diperoleh]
Error: [pesan error jika ada]
```

### Kolaborasi Tim:
1. Setiap tester dapat membuka file HTML
2. Buat copy dengan nama: `TEST_EXECUTION_FORM_CLEAN_[NamaTester].html`
3. Setiap orang isi test case mereka
4. Compile hasil di spreadsheet Excel jika diperlukan

---

## 📋 Perbedaan File HTML

| Fitur | CLEAN | ORIGINAL |
|-------|-------|----------|
| Input Fields | ❌ Paragraf | ✅ Text input |
| Validasi JS | ❌ Tidak | ✅ Ya |
| Print-friendly | ✅ Ya | ⚠️ Partial |
| Untuk Laporan | ✅ Ya | ❌ Untuk Draft |
| Untuk Form | ❌ Tidak | ✅ Ya |

---

## 🚀 Next Steps

1. **Langsung gunakan:** `TEST_EXECUTION_FORM_CLEAN.html`
2. **Jalankan testing** untuk semua 59 test case
3. **Dokumentasikan hasil** dengan baik
4. **Print/Export PDF** untuk laporan final

---

**Status:** ✅ Dokumen siap digunakan  
**Tanggal:** 25 Mei 2026  
**Testing Method:** Black-Box Testing  
**Language:** Bahasa Indonesia  

---

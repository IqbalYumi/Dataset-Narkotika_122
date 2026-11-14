# Dataset Putusan Perkara Pidana Khusus Narkotika — Pengadilan Negeri Kotabaru (2025–2026)

Repositori ini berisi kumpulan dokumen salinan putusan perkara pidana khusus tindak pidana **Narkotika** dari **Pengadilan Negeri Kotabaru (`PN Ktb`)** yang dihimpun dari [Direktori Putusan Mahkamah Agung Republik Indonesia](https://putusan3.mahkamahagung.go.id/), beserta hasil ekstraksi terstrukturnya dalam format spreadsheet.

Dataset ini disusun untuk mendukung kebutuhan **Temu Kembali Informasi (*Information Retrieval*)**, pemrosesan bahasa alami (*Natural Language Processing* / NLP) domain hukum Indonesia, ekstraksi entitas hukum, dan analisis putusan pengadilan.

---

## Struktur Repositori

| Nama File | Format | Deskripsi |
| :--- | :--- | :--- |
| `Narkotika.zip` | `.zip` (PDF) | Arsip dokumen salinan putusan asli dalam format PDF (berisi 60 berkas PDF, terdiri atas **59 dokumen putusan unik** dan 1 berkas duplikat pada perkara `86/Pid.Sus/2026/PN Ktb`). |
| `Data_Putusan_Narkotika_PN_Kotabaru.xlsx` | `.xlsx` | Dataset hasil ekstraksi terstruktur dari seluruh 59 dokumen putusan unik, dilengkapi sheet ringkasan statistik. |
| `README.md` | `.md` | Dokumentasi deskripsi dataset, skema kolom, dan statistik ringkas. |

---

## Statistik Dataset

* **Lembaga Peradilan:** Pengadilan Negeri Kotabaru (`PN Ktb`)
* **Klasifikasi Perkara:** Pidana Khusus (`Pid.Sus`) — Narkotika (UU No. 35 Tahun 2009 tentang Narkotika)
* **Total Dokumen Unik:** 59 Putusan
  * **Tahun 2025:** 18 Putusan (rentang `56/Pid.Sus/2025/PN Ktb` s.d. `163/Pid.Sus/2025/PN Ktb`)
  * **Tahun 2026:** 41 Putusan (rentang `8/Pid.Sus/2026/PN Ktb` s.d. `126/Pid.Sus/2026/PN Ktb`, termasuk 1 Putusan Sela pada perkara `105/Pid.Sus/2026/PN Ktb`)

---

## Skema Kolom (`Data_Putusan_Narkotika_PN_Kotabaru.xlsx`)

Sheet **`Data Putusan`** terdiri atas 5 kolom utama:

| Kolom | Tipe Data | Deskripsi |
| :--- | :--- | :--- |
| `No` | Integer | Nomor urut data (`1` – `59`), diurutkan berdasarkan tahun dan nomor register perkara. |
| `No Putusan` | String | Nomor register putusan resmi pengadilan (contoh: `56/Pid.Sus/2025/PN Ktb`). |
| `Lembaga Peradilan` | String | Nama instansi pengadilan tingkat pertama yang memutus perkara (`Pengadilan Negeri Kotabaru`). |
| `Barang Bukti` | Text | Daftar barang bukti yang dirinci dan ditetapkan statusnya dalam putusan (jenis narkotika, berat kotor/bersih, alat komunikasi, timbangan, kendaraan, dan status perampasan/pemusnahan). Bernilai `-` jika perkara berupa Putusan Sela. |
| `Amar Putusan` | Text | Isi lengkap bagian diktum (`MENGADILI`) yang memuat pernyataan terbukti/tidaknya dakwaan, kualifikasi tindak pidana, lama pidana penjara, pidana denda/subsider, status penahanan terdakwa, penetapan barang bukti, dan pembebanan biaya perkara. |

---

## Metode Ekstraksi & Pembersihan Data

1. **Deduplikasi Berkas:** Berkas PDF identik disaring menggunakan *hash* MD5 sehingga setiap baris merepresentasikan satu nomor perkara unik.
2. **Pembersihan Derau (*Noise Removal*):** *Header* berulang (`Mahkamah Agung Republik Indonesia`, `Direktori Putusan...`), nomor halaman, serta blok *Disclaimer* di bagian bawah setiap halaman PDF dihapus sebelum ekstraksi.
3. **Ekstraksi Berbasis Pola (*Regex Parsing*):** Nomor putusan, nama lembaga peradilan, diktum `MENGADILI`, dan rincian barang bukti diekstrak secara otomatis serta dinormalisasi spasinya.

---

## Sumber & Catatan Penggunaan

* **Sumber Data:** Direktori Putusan Mahkamah Agung Republik Indonesia (`putusan.mahkamahagung.go.id`).
* **Tujuan Penggunaan:** Diperuntukkan bagi penelitian akademik, pengembangan sistem temu kembali informasi (*Information Retrieval*), dan analisis teks hukum.

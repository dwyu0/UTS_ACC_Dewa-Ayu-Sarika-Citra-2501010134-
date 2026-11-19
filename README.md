# UTS Data Acquisition & Management — Semester Ganjil 2026
* **Mata Kuliah:** Data Acquisition & Management (Kelas E)
* **Program Studi:** S1 Informatika — INSTIKI
* **Dosen Pengampu:** Dr. I Gede Totok Suryawan, S.Kom., M.T.
* **Nama Mahasiswa:** Dewa Ayu Sarika Citra
* **NIM:** 2501010134
* **Repositori:** https://github.com/dwyu0/UTS_ACC_2501010134

---

## 📌 Deskripsi Proyek
Repositori ini berisi implementasi pipeline akuisisi data multi-sumber, audit etika (*Data Ethics Checklist* & *Robots.txt*), penyimpanan data mentah yang dapat diaudit (*Data Provenance*), pembersihan data, penggabungan (*merge* dengan validasi relasi), dan analisis korelasi antara sampel kunjungan wisata di Bali (Klaster Bali Greater Hub) dengan parameter iklim cuaca harian.

---

## 📂 Struktur Repositori
```text
├── data/
│   ├── raw/
│   │   ├── indonesia_pariwisata_super_prioritas_enriched.csv  # Sumber 1: Berkas Kaggle (CC0 Public Domain)
│   │   ├── cuaca_bali_api.json                                # Sumber 2: API Open-Meteo Mentah (WITA Bali)
│   │   ├── wikipedia_robots.txt                               # Salinan mentah robots.txt Wikipedia
│   │   ├── wikipedia_pariwisata_bali.html                     # Sumber 3: Raw HTML Web Scraping Wikipedia
│   │   ├── tabel_wikipedia_bali.csv                           # Hasil ekstraksi tabel statis Wikipedia
│   │   └── provenance_metadata.json                           # Catatan Provenance & Checksum Hash MD5
│   └── processed/
│       ├── df_bali_final_clean.csv                            # Data pariwisata yang telah dibersihkan
│       ├── df_bali_cuaca_merged.csv                           # Data gabungan (Merge Soal 5)
│       ├── df_bali_cuaca_merged_metadata.json                 # Kamus data & metadata hasil penggabungan
│       └── diagram_cuaca_vs_kunjungan.png                     # Visualisasi scatter plot
├── UTS_ACC_2501010134.ipynb                                   # Notebook utama (eksekusi run berurutan)
├── .gitignore
└── README.md
```

---

## 🌐 Tiga Sumber Data & Bukti Lisensi

1. **Sumber 1 (Dataset Berkas Terbuka):**
   * **Nama:** Indonesia Pariwisata Destinasi Super Prioritas (oleh Luthfi Muthathohirin)
   * **URL Spesifik:** [Kaggle Dataset](https://www.kaggle.com/datasets/luthfimuthathohirin/indonesia-pariwisata-destinasi-super-prioritas)
   * **Lisensi:** Creative Commons Zero v1.0 Universal (CC0: Public Domain)
   * **Bukti Lisensi:** https://creativecommons.org/publicdomain/zero/1.0/

2. **Sumber 2 (API Publik Resmi):**
   * **Nama:** Open-Meteo Historical Weather API (Koordinat Bali: Latitude -8.4095, Longitude 115.1889, Timezone WITA `Asia/Makassar`)
   * **Lisensi:** Creative Commons Attribution 4.0 International (CC BY 4.0)
   * **Bukti Lisensi:** https://open-meteo.com/en/terms

3. **Sumber 3 (Web Scraping Statis):**
   * **Nama:** Wikipedia Bahasa Indonesia — Pariwisata di Bali
   * **URL:** `https://id.wikipedia.org/wiki/Pariwisata_di_Bali`
   * **Audit Kepatuhan:** Lolos audit robots.txt (`is_allowed = True`). Salinan tersimpan di `data/raw/wikipedia_robots.txt`.
   * **Lisensi:** CC BY-SA 4.0

---

## ⚖️ Catatan Metodologi & Validitas Statistik
Data pariwisata yang digunakan merupakan data sampel survei mobilitas harian (2–9 catatan rombongan per hari), bukan sensus total populasi wisatawan Provinsi Bali. Oleh karena itu, analisis penggabungan secara valid mengagregasikan jumlah individu dalam rombongan sampel (`travel_party_size.sum()`) serta rata-rata pengeluaran harian, bukan menghitung baris secara mentah.

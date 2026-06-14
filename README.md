# UAS-BigData-NoShow-Analytics

# Pembangunan Data Warehouse & Analisis Komparatif ETL vs ELT (Studi Kasus: No-Show Pasien Medis)

Proyek ini adalah Tugas Besar Mata Kuliah Big Data. Berisi implementasi arsitektur pemrosesan data berskala besar menggunakan dua pendekatan pipeline (*ETL* dan *ELT*) untuk menganalisis faktor ketidakhadiran pasien (*no-show*) medis.

## 📂 Struktur Repository
* `Pipeline_ETL_ELT.ipynb`: Source code Python (Pandas) untuk ekstraksi, pembersihan data, dan load ke database.
* `Database_Documentation.pdf`: Dokumentasi Star Schema (SQLite), struktur tabel, dan 8 SQL Query analitik.
* `Dashboard.pbix`: File mentah eksekutif dashboard interaktif.
* `screenshot_dashboard.png`: Tampilan visualisasi akhir dari dashboard.
* `Report_Paper_IEEE.pdf`: Laporan analisis komparatif performa ETL vs ELT berformat IEEE.
* `architecture_diagram.png`: Visualisasi alur data dual-pipeline.
* `Dataset_Info.md`: Keterangan dan tautan sumber data.

## 🛠️ Tools yang Digunakan
* **Bahasa Pemrograman:** Python (Pandas)
* **Database / Data Warehouse:** SQLite
* **Business Intelligence:** Microsoft Power BI (DAX & Power Query)

## 🚀 Cara Menjalankan Project
1. Clone repository ini.
2. Unduh dataset dari tautan yang tersedia di `Dataset_Info.md` dan letakkan di folder `/raw` (jika dijalankan lokal).
3. Buka file `.ipynb` menggunakan Google Colab atau Jupyter Notebook dan jalankan sel (*Run All*) secara berurutan.
4. Buka file `.pbix` menggunakan Power BI Desktop untuk melihat dashboard dan transformasi ELT (Unpivot & DAX).

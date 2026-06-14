# Dokumentasi Database & Data Warehouse

Dokumen ini berisi rincian arsitektur Data Warehouse yang dibangun menggunakan SQLite untuk memproses dataset Medical Appointment No Shows.

## 1. Skema Database (Star Schema)
Pemodelan data menggunakan pendekatan **Star Schema** untuk mengoptimalkan performa kueri analitik. Skema ini terdiri dari satu Tabel Fakta sebagai pusat metrik operasional, yang dikelilingi oleh Tabel Dimensi untuk konteks deskriptif.


## 2. Struktur Tabel

### A. Tabel Fakta: `fact_appointments`
Tabel ini menyimpan metrik utama dan *foreign key* yang menghubungkan ke tabel dimensi.
* `appointment_id` (Primary Key, VARCHAR): ID unik pendaftaran medis.
* `patient_id` (Foreign Key, VARCHAR): Merujuk ke `dim_patient`.
* `location_id` (Foreign Key, VARCHAR): Merujuk ke `dim_location`.
* `scheduled_date` (DATETIME): Waktu pasien melakukan pendaftaran.
* `appointment_date` (DATE): Tanggal janji temu medis.
* `lead_time_days` (INTEGER): Selisih hari antara pendaftaran dan hari H.
* `no_show` (INTEGER): Status kehadiran (0 = Hadir, 1 = Mangkir).

### B. Tabel Dimensi: `dim_patient`
Tabel ini memuat profil demografi dan riwayat medis (komorbiditas) pasien.
* `patient_id` (Primary Key, VARCHAR): ID unik pasien.
* `gender` (VARCHAR): Jenis kelamin pasien (M/F).
* `age` (INTEGER): Umur pasien.
* `age_group` (VARCHAR): Kategori umur pasien.
* `hipertension` (INTEGER): Indikator hipertensi (0/1).
* `diabetes` (INTEGER): Indikator diabetes (0/1).
* `alcoholism` (INTEGER): Indikator alkoholisme (0/1).
* `handcap` (INTEGER): Indikator disabilitas (0/1).
* `total_comorbidities` (INTEGER): Total penyakit bawaan yang dimiliki.

### C. Tabel Dimensi: `dim_location`
Tabel ini memuat informasi geografis wilayah klinik/pasien.
* `location_id` (Primary Key, VARCHAR): ID unik wilayah.
* `neighbourhood` (VARCHAR): Nama lingkungan/kelurahan asal.
* `region` (VARCHAR): Nama region yang lebih luas.

---

## 3. Query SQL Analitik
Berikut adalah 8 kueri SQL yang dijalankan di Data Warehouse untuk memverifikasi data dan mengekstrak *insight* analitik:

**Query 1: Menghitung total pasien dan persentase keseluruhan No-Show**
**Query 2: Menganalisis tingkat No-Show berdasarkan kelompok umur (Age Group)
**Query 3: Mencari 5 Neighbourhood (wilayah) dengan angka pasien mangkir tertinggi
**Query 4: Menganalisis korelasi antara penyakit bawaan (Hipertensi/Diabetes) dengan tingkat kehadiran
**Query 5: Menganalisis rata-rata waktu tunggu (Lead Time Days) per status kehadiran
**Query 6: Melihat tren pendaftaran terbanyak berdasarkan hari (Senin-Minggu)
**Query 7:Menghitung komposisi pasien laki-laki dan perempuan yang mangkir
**Query 8: Mengecek integritas data (memastikan tidak ada data kosong di tabel fakta)

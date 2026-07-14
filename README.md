# Sistem Konten Planner SMK Bhakti Praja Adiwerna

Aplikasi web responsif untuk membantu perencanaan, pembagian tugas, penjadwalan publikasi, pemantauan progres, penyimpanan file, pencatatan engagement, dan pelaporan konten media sosial sekolah.

Proyek ini dibuat sebagai implementasi hasil PKL dan memenuhi tugas UAS mata kuliah **Komputasi Awan dan Perangkat Bergerak**.

## Identitas Mahasiswa

| Keterangan | Data |
|---|---|
| Nama | **Eska Pandu Buana** |
| NIM | **23.21.5044** |
| Program Studi | S1 Teknik Informatika |
| Tempat PKL | **SMK Bhakti Praja Adiwerna** |
| Judul Sistem | **Sistem Konten Planner untuk Optimalisasi Pengelolaan Media Sosial di SMK Bhakti Praja Adiwerna** |

## Fitur Utama

- Login dengan tiga role: **Admin Media Sosial**, **Tim Konten**, dan **Humas/Pihak Sekolah**.
- Dashboard ringkasan status produksi, jadwal publikasi, tugas prioritas, jangkauan, dan interaksi.
- CRUD bank ide konten.
- CRUD data konten lengkap dengan kategori, platform, format, caption, jadwal, status, dan penanggung jawab.
- Kalender publikasi bulanan.
- Manajemen tugas dan pembaruan status pengerjaan.
- Unggah file pendukung konten (JPG, PNG, WEBP, MP4, PDF; maksimal 8 MB).
- Catatan feedback/revisi pada setiap konten.
- Pencatatan engagement: views, likes, komentar, shares, reach, dan saves.
- Laporan per periode dan platform, ranking performa konten, serta ekspor CSV.
- Tampilan responsif untuk laptop, tablet, dan perangkat bergerak.

## Teknologi yang Digunakan

- **PHP 8.1+** (native PHP)
- **SQLite 3** melalui PDO
- **HTML5**
- **CSS3** responsif tanpa framework eksternal
- **JavaScript Vanilla**
- **Docker** (opsional untuk deployment)

## Struktur Basis Data

Basis data mengikuti rancangan pada laporan PKL, terdiri dari tabel:

- `users`
- `content_ideas`
- `contents`
- `tasks`
- `content_files`
- `engagements`
- `feedbacks`

Skema lengkap dan data awal tersedia pada:

```text
database/schema.sql
```

Database SQLite dibuat otomatis pada saat aplikasi pertama kali dijalankan dan disimpan di:

```text
storage/content_planner.sqlite
```

## Cara Menjalankan Secara Lokal

### Pilihan 1 — PHP Built-in Server (paling mudah)

1. Pastikan PHP 8.1 atau versi yang lebih baru sudah terpasang.
2. Pastikan ekstensi `pdo_sqlite` dan `sqlite3` aktif.
3. Buka terminal pada folder proyek.
4. Jalankan perintah:

```bash
php -S localhost:8000
```

5. Buka browser:

```text
http://localhost:8000
```

Database dan data demo akan dibuat otomatis ketika aplikasi pertama kali dibuka.

### Pilihan 2 — XAMPP

1. Salin folder proyek ke:

```text
C:\xampp\htdocs\content-planner-pkl
```

2. Jalankan **Apache** dari XAMPP Control Panel.
3. Buka:

```text
http://localhost/content-planner-pkl
```

> Aplikasi menggunakan SQLite sehingga tidak perlu membuat database melalui phpMyAdmin.

## Akun Demo

| Peran | Email | Kata Sandi |
|---|---|---|
| Admin Media Sosial | `admin@smkbpa.sch.id` | `admin123` |
| Tim Konten | `eska@smkbpa.sch.id` | `team123` |
| Humas/Pihak Sekolah | `humas@smkbpa.sch.id` | `humas123` |

## Reset Database

Untuk menghapus seluruh perubahan dan mengembalikan data demo awal:

```bash
php database/reset_database.php
```

Atau hapus file berikut, lalu buka kembali aplikasi:

```text
storage/content_planner.sqlite
```

## Deployment Cloud (Opsional)

Repository sudah dilengkapi `Dockerfile` dan `render.yaml` sehingga dapat dicoba pada layanan yang mendukung Docker, misalnya Render.

Garis besar deployment:

1. Upload proyek ini ke GitHub.
2. Hubungkan repository GitHub ke layanan cloud.
3. Pilih deployment menggunakan **Docker**.
4. Setelah proses build selesai, buka URL aplikasi yang diberikan layanan cloud.
5. Tambahkan URL tersebut pada bagian ini:

```text
Link aplikasi: BELUM DIISI
```

> Catatan: pada layanan gratis yang tidak menyediakan persistent disk, perubahan data dapat kembali ke data awal ketika service di-restart atau di-deploy ulang. Hal tersebut tidak memengaruhi penilaian source code dan demo lokal.

## Cara Upload ke GitHub

Buat repository public dengan nama sesuai ketentuan tugas:

```text
UAS-PKL_23.21.5044_ESKA-PANDU-BUANA
```

Kemudian jalankan:

```bash
git init
git add .
git commit -m "Initial commit Sistem Konten Planner PKL"
git branch -M main
git remote add origin https://github.com/USERNAME/UAS-PKL_23.21.5044_ESKA-PANDU-BUANA.git
git push -u origin main
```

Ganti `USERNAME` dengan username GitHub masing-masing.

## Pengujian Singkat

Skenario yang dapat digunakan saat demo UAS:

1. Login sebagai admin.
2. Tampilkan dashboard dan jelaskan ringkasan status konten.
3. Tambahkan ide konten baru.
4. Buat konten, tentukan platform, jadwal, penanggung jawab, dan status.
5. Tambahkan tugas untuk anggota tim.
6. Login sebagai Tim Konten dan ubah status tugas.
7. Buka detail konten, tambahkan feedback atau file pendukung.
8. Input data engagement.
9. Buka laporan dan unduh rekap CSV.
10. Tunjukkan tampilan responsif melalui mode perangkat bergerak pada browser.

## Keamanan dan Catatan

- Kata sandi disimpan dalam bentuk hash menggunakan `password_hash()`.
- Semua proses perubahan data menggunakan token CSRF.
- Query database menggunakan prepared statement PDO.
- File yang dapat diunggah dibatasi berdasarkan MIME type dan ukuran.
- Jangan menyimpan data pribadi, password instansi, atau informasi rahasia pada repository public.

## Pengembang

**Eska Pandu Buana**  
NIM: **23.21.5044**  
Program Studi S1 Teknik Informatika — Universitas Harkat Negeri  
2026

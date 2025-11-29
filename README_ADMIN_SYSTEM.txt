======================================================
SISTEM ADMIN DASHBOARD - DOKUMENTASI LENGKAP
======================================================

📋 UPDATE TERBARU:
✨ Sistem Manajemen Sertifikat dengan Upload File
✨ Admin dapat mengelola sertifikat (Tambah, Edit, Hapus)
✨ User dapat melihat dan download sertifikat di e-certificate

======================================================
1. LOGIN.HTML - PENYIMPANAN DATA PENGGUNA
======================================================

Saat pengguna login/mendaftar:
✅ Data pengguna disimpan ke localStorage dengan key 'registeredUsers'
✅ Setiap pengguna baru ditambahkan ke array untuk admin dashboard

Data yang disimpan:
{
  id: timestamp unik,
  name: nama pengguna,
  email: email pengguna,
  joinDate: tanggal bergabung,
  role: "user"
}

======================================================
2. PILIHMENTOR.HTML - PENYIMPANAN DATA PENDAFTARAN
======================================================

Form Pendaftaran menyimpan data lengkap:
✅ Key: 'vinix_registrations'
✅ Berisi: nama, email, no HP, paket, skill, jadwal, metode pembayaran, status

Data yang disimpan:
{
  id: timestamp unik,
  nama: nama peserta,
  email: email peserta,
  noHp: nomor whatsapp,
  paket: "basic" atau "premium",
  skill: jenis skill yang dipilih,
  jadwal: jadwal yang dipilih,
  metodePembayaran: metode pembayaran,
  tanggalDaftar: tanggal daftar,
  status: "pending" atau "completed"
}

======================================================
3. DASHBOARDADMIN.HTML - SISTEM MANAJEMEN LENGKAP
======================================================

TAB 1: OVERVIEW
- Sambutan admin
- Daftar fitur yang tersedia

TAB 2: KELOLA PENGGUNA
Tabel menampilkan:
- No | Nama | Email | Status | Bergabung | Aksi (Edit/Hapus)

TAB 3: PENDAFTARAN PROGRAM
Tabel menampilkan:
- No | Nama Peserta | Email | No.Hp | Paket | Skill | Status | Tanggal

TAB 4: SERTIFIKAT (FITUR BARU) ✨
Tabel menampilkan:
- No | Nama Peserta | Email | Skill | No. Sertifikat | Tanggal | File | Aksi

FITUR SERTIFIKAT LENGKAP:

A. TAMBAH SERTIFIKAT:
   1. Klik tombol "Terbitkan Sertifikat Baru"
   2. Modal form terbuka dengan input:
      - Nama Peserta (required)
      - Email Peserta (required)
      - Pilih Skill (required) - UI/UX, Web Dev, Graphic Design, Aplikasi Perkantoran
      - Upload File Sertifikat PNG/JPG (required)
      - Catatan (optional)
   3. Klik "Simpan Sertifikat"
   4. Sertifikat tersimpan dengan nomor unik CERT-[timestamp]
   5. File disimpan sebagai Base64 di localStorage

B. EDIT SERTIFIKAT:
   1. Di tabel sertifikat, klik tombol "Edit"
   2. Modal terbuka dengan data sertifikat yang ada
   3. Ubah data dan/atau upload file baru
   4. Klik "Simpan Sertifikat"
   5. Perubahan disimpan

C. HAPUS SERTIFIKAT:
   1. Di tabel sertifikat, klik tombol "Hapus"
   2. Konfirmasi penghapusan
   3. Sertifikat dihapus dari database

D. KOLOM FILE:
   - Menampilkan icon file jika ada file upload
   - Menampilkan "-" jika belum ada file

TAB 5: PENGATURAN
- Nama Platform
- Email Support
- WhatsApp Support
- Deskripsi Platform

======================================================
4. E-CERTIFICATE.HTML - TAMPILAN USER (DIPERBARUI) ✨
======================================================

FITUR BARU:

✅ Menampilkan sertifikat sesuai email user yang login
✅ Filter otomatis berdasarkan email pengguna
✅ Preview gambar sertifikat (dari file yang di-upload admin)
✅ Informasi detail sertifikat:
   - No. Sertifikat
   - Tanggal Terbit
   - Catatan dari admin
✅ Tombol Download untuk setiap sertifikat
✅ Pesan "Belum ada sertifikat" jika user tidak punya sertifikat

TAMPILAN:
Untuk setiap sertifikat user:
1. Judul: "E-Certificate - [Nama Skill]"
2. Preview gambar sertifikat
3. Overlay Download saat hover
4. Detail info di bawah gambar

DOWNLOAD:
- Klik tombol Download
- File akan didownload dengan nama: sertifikat-vinix7-[timestamp].jpg

======================================================
5. STATISTICS DASHBOARD (DIPERBARUI)
======================================================

Menampilkan 4 kartu statistik real-time:
✅ Total Pengguna - Jumlah user terdaftar
✅ Total Mentors - 12 mentor (hardcoded)
✅ Pendaftaran Aktif - Jumlah pendaftaran program
✅ Sertifikat Dikeluarkan - Jumlah sertifikat yang diterbitkan

======================================================
ALUR WORKFLOW LENGKAP
======================================================

1. USER MENDAFTAR:
   login.html → Dashboard → Pilih Mentor (Form Registrasi)
   ↓
   Data tersimpan di 'registeredUsers' dan 'vinix_registrations'

2. ADMIN KELOLA SERTIFIKAT:
   Login Admin → Dashboard Admin → Tab Sertifikat
   ↓
   Tambah/Edit/Hapus Sertifikat
   ↓
   Data tersimpan di 'vinix_certificates' dengan file Base64

3. USER LIHAT SERTIFIKAT:
   e-certificate.html → Filter berdasarkan email user
   ↓
   Tampilkan sertifikat yang sesuai
   ↓
   User dapat download

======================================================
LOCAL STORAGE KEYS LENGKAP
======================================================

User Session:
- username: Nama user login
- email: Email user login  
- role: "user" atau "admin"

Data Pengguna:
- registeredUsers: Array pengguna terdaftar

Data Pendaftaran:
- vinix_registrations: Array pendaftaran program
- vinix_selected_skill: Skill dipilih di form
- vinix_selected_jadwal: Jadwal dipilih di form

Data Sertifikat (STRUKTUR LENGKAP):
- vinix_certificates: Array sertifikat dengan struktur:
  {
    id: timestamp unik,
    nama: nama peserta,
    email: email peserta (digunakan untuk filter di e-certificate),
    skill: jenis skill (UI/UX Design, Web Development, etc),
    catatan: catatan dari admin,
    noCertifikat: nomor unik (CERT-[timestamp]),
    tanggalTerbit: tanggal terbit sertifikat,
    fileName: nama file asli yang di-upload,
    fileData: base64 encoded image (untuk preview & download)
  }

Data Lainnya:
- vinix_reviews: Array testimoni pengguna
- vinix_skill: Skill user
- vinix_jadwal: Jadwal user

======================================================
CARA TESTING LENGKAP
======================================================

A. TESTING SEBAGAI USER:

1. Buka login.html
2. Isi form login:
   - Nama: Budi Santoso
   - Email: budi@email.com
3. Klik "Masuk Sebagai User"
4. Akan masuk ke dashboard.html
5. Klik "Daftar" atau akses pilihmentor.html
6. Isi form pendaftaran:
   - Nama: Budi Santoso
   - Email: budi@email.com (HARUS SAMA)
   - No. Hp: 081234567890
   - Paket: Premium
   - Skill: Web Development
   - Jadwal: Senin - Rabu, 09.00
   - Metode Pembayaran: Transfer Bank
7. Klik "Daftar"
8. Akan redirect ke upgradeskill.html

B. TESTING SERTIFIKAT SEBAGAI ADMIN:

1. Buka login.html
2. Klik "Login sebagai Admin"
3. Masukkan password: admin123
4. Akan masuk ke dashboardadmin.html
5. Di Dashboard, lihat statistik:
   - Total Pengguna: 1
   - Pendaftaran Aktif: 1
   - Sertifikat: 0
6. Klik tab "SERTIFIKAT"
7. Klik "Terbitkan Sertifikat Baru"
8. Modal terbuka, isi form:
   - Nama: Budi Santoso
   - Email: budi@email.com (HARUS SAMA dengan user login)
   - Skill: Web Development
   - Upload File: Pilih gambar sertifikat
   - Catatan: Sertifikat selesai program Web Dev (optional)
9. Klik "Simpan Sertifikat"
10. Alert success
11. Sertifikat muncul di tabel dengan icon file
12. Statistik berubah: Sertifikat: 1

C. TESTING LIHAT SERTIFIKAT SEBAGAI USER:

1. Dari halaman mana saja, akses e-certificate.html
2. Atau: Klik navigasi → E-Certificate
3. Halaman e-certificate.html load
4. Tampilkan sertifikat yang sesuai dengan email user login (budi@email.com)
5. Sertifikat ditampilkan dengan:
   - Judul: E-Certificate - Web Development
   - Preview gambar sertifikat
   - Detail: No. Sertifikat, Tanggal, Catatan
6. Hover ke sertifikat → Overlay Download muncul
7. Klik tombol Download → File terdownload

D. TESTING EDIT SERTIFIKAT:

1. Login admin
2. Tab Sertifikat
3. Di tabel, klik tombol "Edit" pada sertifikat
4. Modal terbuka dengan data lama
5. Ubah data (misalnya catatan)
6. Bisa upload file baru atau biarkan file lama
7. Klik "Simpan Sertifikat"
8. Data terupdate

E. TESTING HAPUS SERTIFIKAT:

1. Login admin
2. Tab Sertifikat
3. Di tabel, klik tombol "Hapus" pada sertifikat
4. Konfirmasi: "Apakah Anda yakin?"
5. Klik OK untuk confirm
6. Sertifikat dihapus
7. Statistik berkurang

======================================================
PASSWORD & AKUN TEST
======================================================

USER LOGIN:
Nama: Budi Santoso (atau bebas)
Email: budi@email.com (atau bebas)

ADMIN LOGIN:
Username: Administrator (otomatis)
Email: admin@vinix.com (otomatis)
Password: admin123

======================================================
FITUR YANG SUDAH BERFUNGSI
======================================================

✅ Login user dengan menyimpan data
✅ Admin login dengan role check
✅ Pendaftaran program dengan data lengkap
✅ Dashboard admin menampilkan statistik real-time
✅ Tab Kelola Pengguna menampilkan semua pengguna
✅ Tab Pendaftaran menampilkan data pendaftaran
✅ Tab Sertifikat dengan form upload file (BARU)
✅ Admin tambah sertifikat dengan upload (BARU)
✅ Admin edit sertifikat dan file (BARU)
✅ Admin hapus sertifikat (BARU)
✅ User lihat sertifikat di e-certificate (BARU)
✅ User download sertifikat (BARU)
✅ Filter sertifikat berdasarkan email user (BARU)
✅ Logout dengan clear localStorage
✅ Responsive design

======================================================
FITUR YANG BISA DIKEMBANGKAN
======================================================

- Validasi format email
- Multiple sertifikat per user
- Tanda tangan digital
- QR Code verifikasi
- Template sertifikat custom
- Notifikasi email ke user
- Export sertifikat ke PDF
- Archive sertifikat lama
- Batch upload sertifikat
- Backend database integration

======================================================

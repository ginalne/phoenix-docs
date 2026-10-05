---
name: phoenix-docs-silverbullet
pageDecoration: 
  icon: info
description: knowledge-base phoenix untuk AI Agent selama membuat dokumentasi phoenix.
---

## Workspace (Modul Developer)

- Workspace adalah komponen untuk mengatur ruang kerja pengembangan: komponen yang dapat dilihat, dikelola, dan diubah, serta **fungsi di dalamnya** (bukan "integrasi yang digunakan", sesuai versi akhir penulis).
- Akses Workspace ke setiap anggota dikelola melalui Group. Setelah Group memetakan pengguna ke Workspace, Workspace dapat digunakan. Saat membuka Phoenix, pengguna masuk ke satu Workspace yang sudah memiliki struktur folder.
- Setiap Pro memiliki satu rangkaian folder yang berawal dari **Origin**. Jika komponen Workspace ditempatkan di folder yang lebih dalam, folder itu menjadi root.
- **Membuat:** buka folder di Area Manajemen Folder, klik kanan > Add > Developer > Workspace, isi Name dan Description, klik Create.
- **Mengubah:** tombol Edit pada bilah navigasi mengubah **atribut Workspace** (Name, Description), lalu klik Update. Tombol Edit bukan untuk mengubah sel hak akses.
- **Menyegarkan:** tombol Refresh memuat ulang tampilan.
- **Menghapus:** klik kanan Workspace > Delete, lalu konfirmasi dengan Delete. Sebelum menghapus, pastikan setiap Group masih memiliki Workspace lain agar pengguna tetap bisa memakai Phoenix.
- Bilah navigasi Workspace hanya memiliki tombol Edit dan Refresh.
- **Halaman kerja:**
  - Kolom kiri: Folder/ Component. Kolom kanan: Comp. Access, Data Access, Function Access.
  - Baris Origin = workspace. Baris Group (contoh: Administrator) hanya mengatur akses dari Workspace ke komponen Group tersebut, **bukan** akses per anggota.
  - Sel kosong berarti akses itu tidak relevan untuk komponen tersebut.
  - Arti angka dan ikon di samping nama komponen dijelaskan di halaman Folder, bagian Informasi Data.
- **Hak akses** (nilai: allow / disallow):
  - Comp. Access (level komponen/header): Visible, Add (menambah folder atau komponen baru), Update (mengubah atribut komponen), Delete.
  - Data Access (level data): Add, Update, Delete. Jenis data bergantung komponen (Table View: Row dan TableData; Timeline: TimelineData). Penjelasan lengkap ada di subhalaman Data Access.
  - Function Access: Merge (penggabungan data), Modify Event, View Publish (hanya melihat konfigurasi publikasi, misalnya menyalin Publish Link), Publish (memperbarui konfigurasi publikasi).
- **Pewarisan:** jika folder induk Visible = disallow, seluruh isinya tidak dapat diakses meski allow. Disallow juga dapat diterapkan pada komponen selain folder, misalnya komponen Workspace dan Tree.
- Nama folder pada gambar contoh penulis adalah kasus pribadi dan tidak disebut di dokumentasi.
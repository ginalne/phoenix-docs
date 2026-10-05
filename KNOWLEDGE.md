---
name: phoenix-docs-silverbullet
pageDecoration: 
  icon: info
description: knowledge-base phoenix untuk AI Agent selama membuat dokumentasi phoenix.
---

## Workspace (Modul Developer)
 
- Workspace adalah komponen untuk mengatur ruang kerja pengembangan: komponen yang dapat dilihat, dikelola, dan diubah, serta integrasi yang digunakan.
- Akses Workspace ke setiap anggota dikelola melalui Group. Setelah Group memetakan pengguna ke Workspace, Workspace dapat digunakan.
- Saat pengguna membuka Phoenix, mereka masuk ke satu Workspace yang sudah memiliki struktur folder.
- Setiap Pro memiliki satu rangkaian folder yang berawal dari **Origin**. Jika komponen Workspace ditempatkan di folder yang lebih dalam, folder itu menjadi root.
- Hak akses (nilai: allow / disallow):
  - **Comp. Access** (level komponen/header): Visible, Add, Update, Delete. Visible = disallow menyembunyikan komponen, termasuk saat dipilih (misalnya saat membuat komponen Interface).
  - **Data Access** (level data di bawah header): Add, Update, Delete. Jenis data bergantung komponen (Table: Row, Timeline: Timeline Data).
  - **Function Access**: Merge, Modify Event, View Publish (hanya melihat konfigurasi publikasi, misalnya menyalin alamat share), Publish (memperbarui konfigurasi publikasi).
- Pewarisan: jika folder (induk) Visible = disallow, seluruh isi tidak dapat diakses meski allow.
- Disallow dapat diterapkan pada folder dan komponen lain, termasuk komponen Workspace (nested) dan Data Tree.
- Navbar Workspace hanya memiliki tombol Edit dan Refresh.
- Halaman kerja: Origin = workspace, Administrator = group (angka = jumlah anggota), folder dapat dibuka untuk melihat komponen di dalamnya.
- Nama folder pada gambar contoh penulis adalah kasus pribadi dan tidak disebut di dokumentasi.`
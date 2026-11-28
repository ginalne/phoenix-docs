---
status: release
title: "Apa yang berubah ketika perangkat lunak sekolah menjadi lebih fleksibel"
description: "Sebuah cerita pendek tentang format pendataan yang harus dibuat ulang setiap semester, dan apa yang berubah setelah struktur data bisa menyesuaikan diri dengan kebutuhan sekolah"
cta: Ingin melihat Phoenix bekerja untuk sekolah Anda?
readMinutes: 4
author:
  name: Phoenix Team
  role: Communication
  bio: Stories and updates from the people building Phoenix
updated: 2026-11-27
user: education
tags:
  Perencanaan
---
# Apa yang berubah ketika perangkat lunak sekolah menjadi lebih fleksibel
![[Blog/2026-11-27/how-to-use-phoenix-in-education.png|A school administrator and a teacher reviewing student and activity records together]]
*Evaluasi murid dan aktifitas pendataan bersamaan. Photo: ChatGPT AI generated*

>Bayangkan minggu pertama semester baru. Seorang staf tata usaha membuka berkas pendataan siswa dari semester lalu, lalu berhenti di tengah jalan. Kepala sekolah baru saja meminta data tambahan: siapa saja yang mengikuti kegiatan pengembangan diri, dan siapa pembinanya. “Kolomnya tidak ada, Bu,” katanya. “Saya buat berkas baru saja, ya?”
>
>Wali kelas menjawab, “Boleh, tapi data nilai ada di berkas lain, dan daftar kegiatan ada di catatan guru pembina.” Staf itu mengangguk, membuka lembar kosong, dan mulai menyalin. Tidak ada yang salah. Hanya saja, pekerjaan yang sama akan terulang lagi semester depan.

## Sekolah memang berubah setiap semester

Sekolah adalah tempat yang terus bergerak. Setiap semester datang kelas baru, jadwal baru, kegiatan baru, dan kadang permintaan data baru dari pimpinan atau pihak lain. Kebutuhan pendataan ikut berubah.

Sementara itu, alat yang dipakai biasanya disusun untuk satu bentuk saja: spreadsheet yang dirancang sekali, formulir untuk satu keperluan, atau aplikasi dengan kolom yang sudah tetap. Ketika bentuknya tidak lagi cocok, membuat berkas baru adalah jalan tercepat, dan itu pilihan yang masuk akal bagi staf yang waktunya terbatas. Begitu juga dengan data yang tersebar. Informasi akademik, kegiatan, dan administrasi tersimpan di tempat berbeda karena masing-masing dibuat pada waktu dan untuk keperluan yang berbeda.

## Ongkosnya baru terasa belakangan

Selama perubahannya kecil, cara ini masih bisa ditoleransi. Namun setiap kali proses sekolah bergeser, ada bayaran yang akrab bagi siapa pun yang bekerja di tata usaha:

- **Pekerjaan yang sama diulang setiap semester.** Struktur dibuat lagi, data lama disalin lagi, dan format dirapikan lagi.
- **Data disesuaikan secara manual.** Nama siswa yang ditulis berbeda di dua berkas harus dicocokkan satu per satu.
- **Informasi tidak bertemu.** Pertanyaan sederhana, seperti siswa mana yang aktif di kegiatan tertentu dan bagaimana perkembangan akademiknya, berarti membuka beberapa berkas sekaligus.
- **Pekerjaan bergantung pada satu orang.** Hanya staf tertentu yang tahu berkas mana yang paling baru dan rumus mana yang tidak boleh disentuh.

Ongkos yang paling mahal justru yang paling senyap. Pemahaman tentang cara kerja sistem lama tinggal di kepala satu orang. Ketika orang itu cuti, pindah tugas, atau pensiun, sekolah harus memulai lagi dari awal. Sepanjang waktu itu, tenaga staf terpakai untuk merawat alat, bukan untuk melayani siswa dan guru.

## Fleksibel bukan berarti setiap orang bebas mengubah apa saja

Mendengar “struktur data yang bisa diubah”, banyak kepala sekolah dan pengelola administrasi langsung khawatir, dan kekhawatiran itu wajar. Jika kolom bisa ditambah kapan saja oleh siapa saja, bisa jadi datanya justru makin tidak teratur. Fleksibilitas tanpa aturan memang bisa lebih berantakan daripada spreadsheet.

Karena itu, yang perlu dicari bukan sekadar sistem yang bisa diubah, melainkan sistem yang berubah di tempat yang sama. Kolom baru ditambahkan pada struktur yang sudah ada, sehingga data lama tetap di tempatnya dan tidak perlu disalin ke berkas baru. Pilihan seperti jenis kegiatan atau status ditetapkan sekali, sehingga penulisannya seragam. Dan hanya orang yang bertanggung jawab yang boleh mengubah struktur, sementara yang lain cukup mengisi dan membaca.

Di sinilah arah hubungannya berbalik. Perangkat lunak seharusnya mengikuti proses kerja sekolah. Ketika prosesnya berubah, strukturnya yang disesuaikan, bukan sekolah yang terus mempertahankan cara lama hanya karena formatnya sudah terlanjur kaku.

## Yang bisa dikelola sekolah dengan Phoenix

Phoenix bukan sistem sekolah siap pakai dengan kolom yang sudah ditentukan. Phoenix menyediakan bahan agar sekolah menyusun sendiri pendataannya sesuai proses yang sedang berjalan, lalu mengubahnya ketika prosesnya berubah. Beberapa hal yang bisa dilakukan:

- **Tabel yang mengikuti kebutuhan.** Siswa, kelas, guru, dan kegiatan masing-masing punya tabel (Table). Kolomnya bisa ditambah atau diubah ketika format pendataan berubah, dan Phoenix memberi peringatan bila perubahan berisiko menghilangkan data.
- **Hubungan antardata.** Kolom dapat mengacu ke baris di tabel lain, sehingga siswa terhubung dengan kelas dan kegiatannya tanpa menulis ulang (Table).
- **Pilihan yang seragam.** Status, jenis kegiatan, atau semester disusun sebagai daftar pilihan yang sama di mana pun dipakai (Enum).
- **Formulir pendataan.** Guru atau staf mengisi formulir, dan isiannya masuk ke tabel yang sudah ada tanpa perlu disalin ulang (Form).
- **Tampilan sesuai peran.** Wali kelas melihat siswa di kelasnya, pembina melihat peserta kegiatannya, semuanya dari data yang sama (Table View).
- **Papan tahapan.** Proses seperti pengajuan kegiatan atau kelengkapan berkas bisa dilihat per tahap dan digeser ke tahap berikutnya (Kanban).
- **Peran yang jelas.** Pengelola, staf, dan guru hanya melihat dan mengubah bagian yang menjadi tanggung jawabnya (Group dan Workspace).

Tidak perlu menyiapkan semuanya sekaligus. Mulailah dari satu tabel yang paling sering dibuat ulang setiap semester, misalnya pendataan kegiatan. Setelah berjalan, hubungkan dengan data siswa dan tambahkan tampilan sesuai kebutuhan. Lalu, ketika semester berikutnya kepala sekolah meminta data tambahan, jawaban staf tidak lagi “saya buat berkas baru saja”, melainkan cukup menambah satu kolom.
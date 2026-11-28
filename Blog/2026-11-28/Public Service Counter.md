---
status: release
title: "Mengapa layanan publik membutuhkan struktur yang dapat menyesuaikan diri"
description: "Sebuah cerita pendek tentang satu kolom baru yang harus menempuh empat tempat setiap kali ketentuan berubah, dan apa yang berubah setelah data layanan berada di satu struktur yang bisa disesuaikan"
cta: Ingin melihat bagaimana Phoenix bisa mengikuti perubahan di layanan Anda?
readMinutes: 4
author:
  name: Phoenix Team
  role: Communication
  bio: Stories and updates from the people building Phoenix
updated: 2026-11-28
user: government
tags:
  Public Service
---
# Mengapa layanan publik membutuhkan struktur yang dapat menyesuaikan diri
![[Blog/2026-11-28/public-service-counter.png|petugas dan warga di loket layanan publik]]
*Pengumpulan data publik. Photo: ChatGPT AI generated*

Bayangkan sebuah formulir permohonan layanan di loket kantor pelayanan. Ini hanya ilustrasi, tetapi kerepotannya mungkin Anda kenal. Suatu hari ketentuan administrasi berubah, dan formulir itu harus meminta satu keterangan tambahan dari pemohon.

Satu kolom saja. Di atas kertas, itu pekerjaan sebentar.

## Satu kolom, empat tempat yang ikut berubah

Kolom baru itu tidak berhenti di formulir. Ia harus ikut ke setiap tempat yang selama ini memegang data yang sama.

**Pertama, formulir itu sendiri.** Cetakan lama diganti, dan petugas diberi tahu isian mana yang kini wajib. Selama beberapa hari, dua versi formulir bisa beredar di meja yang berbeda.

**Kedua, spreadsheet di bagian verifikasi.** Menyisipkan satu kolom tampak sepele, sampai rumus di sebelahnya bergeser dan penyaring yang biasa dipakai menampilkan hasil yang aneh.

**Ketiga, aplikasi pendaftaran.** Ini biasanya tidak bisa diubah sendiri oleh petugas. Permintaannya masuk ke tim pengembangan layanan digital, mengantre bersama permintaan lain, dan baru selesai setelah beberapa waktu.

**Keempat, laporan.** Bentuk laporan mengikuti data yang dikumpulkan, jadi laporan pun perlu disusun ulang.

Sementara itu, loket tetap buka. Antrean tidak menunggu perubahan selesai.

## Kekakuan ini bukan kelalaian siapa pun

Hampir setiap alat di layanan publik lahir untuk menjawab satu kebutuhan pada satu waktu. Bagian verifikasi punya spreadsheet karena itulah yang paling cepat tersedia. Aplikasi pendaftaran dibangun untuk pendaftaran. Laporan disusun untuk pihak yang memintanya.

Setiap departemen memang mencatat hal yang berbeda, tetapi catatan itu saling berkaitan. Permohonan dari loket menjadi bahan kerja verifikasi, dan hasil verifikasi menjadi bahan laporan. Karena alatnya berdiri sendiri-sendiri, setiap perubahan harus dijalani satu per satu.

Pilihan itu masuk akal pada waktunya. Harganya baru terasa ketika ketentuan berubah.

## Tiga bulan kemudian, pertanyaan yang tidak ada jawabannya

Bila perubahan dikerjakan sepotong-sepotong, data dari dua aturan bisa bercampur dalam satu daftar, dan pertanyaan seperti ini mulai muncul. Permohonan bulan lalu diisi dengan aturan lama atau yang baru? Spreadsheet verifikasi sudah punya kolom itu, tetapi apakah aplikasinya sudah? Laporan triwulan ini memakai versi yang mana? Dan bila ketentuan berubah lagi, siapa yang masih ingat apa saja yang harus diubah kemarin?

Ongkos yang paling senyap bukan lamanya perubahan, melainkan kepercayaan. Petugas mulai ragu pada data sendiri, dan keraguan itu dibayar dengan pemeriksaan ulang di sela pelayanan.

## Bukankah fleksibel berarti siapa saja bisa mengubah apa saja?

Kekhawatiran itu wajar, apalagi di layanan yang datanya menyangkut warga. Struktur yang bisa berubah tanpa batas memang lebih berisiko daripada struktur yang kaku. Kekakuan setidaknya membuat perubahan tidak mudah dilakukan sembarang orang.

Karena itu yang dicari bukan struktur yang bebas diubah, melainkan struktur yang mudah diubah oleh orang yang berwenang, dan hanya oleh mereka. Petugas loket perlu bisa mengisi dan memperbarui data tanpa bisa mengubah bentuk tabelnya. Pengelola layanan perlu bisa menambah kolom tanpa menunggu antrean pengembangan. Dua kebutuhan itu tidak bertentangan, selama pembagian hak aksesnya jelas.

## Mengikuti kolom yang sama di Phoenix

Phoenix dirancang agar struktur data dan alur kerja bisa menyesuaikan diri. Coba ikuti kolom baru tadi.

Data permohonan tersimpan di satu tabel (Table). Ketika ketentuan berubah, pengelola menambah kolom di tabel itu. Bila perubahan berisiko menghilangkan data, Phoenix menampilkan peringatan terlebih dahulu, sehingga keputusan tidak diambil dalam gelap. Lalu formulir pendaftaran (Form) diberi satu isian yang terhubung ke kolom tersebut. Apa yang diisi pemohon langsung masuk ke tabel yang sama dengan yang dipakai bagian lain, jadi tidak ada salinan yang harus disamakan.

Bagian verifikasi dan bagian pelaporan tidak perlu menyimpan salinan sendiri. Masing-masing melihat tabel yang sama lewat tampilan tabel (Table View), dengan kolom dan penyaring yang disesuaikan untuk kebutuhannya. Data yang saling berkaitan, seperti permohonan dan pemohonnya, bisa dihubungkan antartabel, sehingga satu informasi tidak perlu ditulis di banyak tempat.

Daftar pilihan seperti jenis layanan atau status disimpan terpisah (Enum). Bila prosedur menambah satu tahap, cukup tambahkan satu pilihan, dan papan status (Kanban) yang memakai pilihan itu menampilkannya sebagai kolom baru. Pekerjaan rutin yang mengikutinya, misalnya memberi status awal pada setiap permohonan yang baru masuk, bisa dijalankan otomatis oleh alur kerja (Flow), dan setiap jalannya tercatat.

Soal siapa boleh apa, anggota dikelompokkan ke dalam Group, dan setiap Group diberi Workspace yang menentukan komponen mana yang terlihat serta apa yang boleh ditambah, diubah, atau dihapus. Staf loket bisa diberi izin mengelola data permohonan tanpa izin mengubah struktur tabelnya, sedangkan pengelola layanan diberi izin tambahan untuk menyesuaikan strukturnya. Perubahan hak akses berlaku langsung.

Ini tidak berarti setiap perubahan serba ringan. Perubahan besar pada cara kerja layanan tetap perlu dirancang dengan hati-hati, dan Phoenix tidak menggantikan penilaian keamanan serta kepatuhan yang harus dilakukan setiap instansi terhadap aturannya sendiri. Yang berubah adalah perubahan yang paling sering terjadi: menambah kolom, menambah pilihan, menambah tahap. Itu tidak lagi berarti mulai dari nol.

Kolom tadi kembali menjadi satu kolom, seperti yang tampak di atas kertas dulu. Ia ditambahkan di satu tempat, lalu terlihat di semua tempat yang memerlukannya.
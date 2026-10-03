---
    status: draft
    pageDecoration:
      icon: home
      tree:
        priority: -3
---
# Welcome to Phoenix Docs
Sebagai pembaca saya harap anda dapat mengabaikan halaman ini, berikut adalah tips dan aturan yang berlaku saat menulis dokumentasi ini:

>**warning** Wajib dibaca oleh penulis!
>Anda boleh mengedit halaman ini jika diperlukan.

ATURAN:
1. Penulis wajib menulis [[index#Frontmatter|Frontmatter]] disetiap awal dokumen.
2. Penulis wajib membuat urutan [[index#Heading|Heading]] yang tepat.
3. Penulis tidak boleh menulis [[index#Task|Task]] kecuali digunakan dalam [[index#Comment|Comment]]
4. Penulis wajib menyisipkan ruang dengan Enter 2x diakhir dokumen (agar ada space dengan kolom Linked Mentions)


---

## Frontmatter
frontmatter adalah section wajib dalam penulisan dokumentasi yang dibuka dengan `---` dan ditutup dengan `---`, isi dari frontmatter ditulis dengan format YAML. 

Lihat lebih lengkap [[frontmatter guidance| atribute penting frontmatter]].

---

## Heading
Sebagai penulis Anda wajib menambahkan judul pada baris pertama diawali dengan mengetik # dan spasi.

Harap pastikan urutan heading tidak salah. Heading 1 diawali #, Heading 2 diawali ##, Heading 3 diawali ###. Jangan gunakan Heading 1 lebih dari 1 kali.

---

## Comment
comment adalah section dalam penulisan dokumentasi yang dibuka dengan `<!--` dan ditutup dengan `-->`, isi dari comment ditulis dengan format berikut:

<!--
  `@your_username` <small style="opacity: 0.5">at your time</small>
  Tulis komen... `@free` untuk mention siapapun...

  tulis disini balasannya...
-->

>**note** Tips Command
>Anda bisa ketikan perintah ***`/asking`*** untuk memulai komen, dan ***`/answer`*** untuk menjawab (harap kursor perlu didalam comment).
>
>seperti contoh:

<!--
  `@ginalne` <small style="opacity: 0.5">at 2026-10-02 21:21</small>
  Hallo semua @everynyaw

  <small>*ketik ***`/answer`*** dibawah ini*</small>
  
-->

>**note** Kelebihan
>Comment tidak akan tampil di website, jadi gunakan section ini untuk berdiskusi

---

## Admonition
Admonition adalah section dalam penulisan dokumentasi yang dibuka dengan `>**note**`, `>**warning**`, atau `>**danger**`, isi dari info, warning, atau danger dapat ditulis dengan format berikut:

>**note** Judul Info
>Silahkan isi deskripsi info secara bebas

Anda dapat menggunakan ketik ***`/note-admonition`*** lalu Enter untuk membuat info.

>**warning** Judul Warning
>Silahkan isi deskripsi warning secara bebas

Anda dapat menggunakan ketik ***`/warning-admonition`*** lalu Enter untuk membuat peringatan.

>**danger** Judul Danger
>Silahkan isi deskripsi danger secara bebas

Anda dapat menggunakan ketik ***`/danger-admonition`*** lalu Enter untuk membuat larangan.

>**success** Judul Success
>Silahkan isi deskripsi success secara bebas

Anda dapat menggunakan ketik ***`/success-admonition`*** lalu Enter untuk membuat tip/sukses.

---

## Text Decoration
Sebagai Penulis baru tentu menggunakan Silverbullet tidaklah mudah, berikut adalah hint yang perlu diingat agar mudah mengetik:

1. Huruf Miring (_italic_), dengan cara ketik underscore (*) dipembuka dan penutup, seperti contoh *ini adalah teks miring*.
2. Huruf Tebal (**bold**), dengan cara ketik bintang 2x (**) dipembuka dan penutup, seperti contoh **ini adalah teks tebal**.
3. Huruf Miring + Tebal (***italic + bold***), dengan cara ketik bintang 3x (***) dipembuka dan penutup, seperti contoh **ini adalah teks tebal**.
4. Penerangan (==Highlighting==), dengan cara ketik simbol sama dengan 2x `==` dipembuka dan penutup, seperti contoh ==highlight saya==.

---

## List
Ada 2 jenis list yang digunakan:

### List tanpa nomor
  adalah dengan * atau - diawal lalu ditambah spasi:
  * ini list tanpa nomor
  * ini daftar selanjutnya
    
### List dengan nomor
  adalah dengan nomor diawal lalu ditambah spasi:
  1. Ini item pertama
  2. Ini item kedua

---

## Task
Task hanya boleh digunakan dalam [[index#Comment|Comment]], karena tidak bagus ditampilkan di website.

Ada beberapa jenis task yang bisa digunakan:

### Checkbox Task
Dengan syntax `* [ ]`. contohnya:

* [ ] Ini task hanya ceklist (dengan syntax `* [ ] Nama task` )
* [x] task menjadi kabur ketika diceklis

## State Task
Dengan mengetik syntax `* [STATE]`. Nilainya bisa diisi dengan PROGRESS, DONE atau TODO. contohnya:

* [TODO] Ini task dengan sifat dikerjakan [priority: high] [assignee: @ginalne]
* [TODO] Ini task dengan sifat belum dikerjakan
* [TODO] Ini task dengan sifat selesai
  
>**note** Tips Command
>Anda bisa ketikan perintah ***`/todo task`*** untuk menambahkan item TODO.
>bisa juga dengan mengetik task nya terlebih dahulu lalu menutup ***/todo task*** lalu Enter diakhir.
>
>Seperti contoh : Ini pekerjaan baru `/todo task`
>lalu Enter 

---

## Quotes
Tambahkan quotes jika ingin mengutip sesuatu dengan mengetik simbol `>` diawal, contohnya:

> “If you don’t know where you’re going, you may not get there.”
> — Yogi Berra

---

## Table
Tambahkan table jika ingin membuat informasi berbentuk tabel dengan cara ketik `/table` lalu Enter, contohnya:

| Header A | Header B |
|----------|----------|
| Cell A | Cell B |

---

## Tambahan
Harap isi enter 2x disetiap akhir dokumen.

---

## Penutup
Sekian tips dan aturan yang wajib diikuti oleh Penulis. Harap di ingat.
Terimakasih

Selamat Menulis ~


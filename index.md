---
    status: draft
    pageDecoration:
      tree:
        priority: -3
---
# Welcome to Phoenix Docs
Sebagai pembaca saya harap anda dapat mengabaikan pesan ini, berikut adalah aturan yang berlaku saat menulis dokumentasi ini:

>[!warning] Wajib dibaca oleh penulis!
>Anda boleh mengedit halaman ini jika diperlukan.

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
  `@your_username` 
  Some Comment... `@free` mention some here...

  some other comment or replied...
  
  
-->

>[!note] Kelebihan Comment
>Comment tidak akan tampil diwebsite, jadi gunakan section ini untuk berdiskusi

---

## Info dan Warning
info dan warning adalah section dalam penulisan dokumentasi yang dibuka dengan “>[!note]” untuk info, dan “>[!warning]“, isi dari info atau warning dapat ditulis dengan format berikut:

>[!note] Judul Info
>Silahkan isi deskripsi info secara bebas

>[!warning] Judul Warning
>Silahkan isi deskripsi warning secara bebas

---

## Text Decoration
Sebagai Penulis baru tentu menggunakan Silverbullet tidaklah mudah, berikut adalah hint yang perlu diingat agar mudah mengetik:

1. Huruf Miring (_italic_), dengan cara ketik underscore (_) dipembuka dan penutup, seperti contoh *ini adalah teks miring*.
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
Task dapat Anda gunakan sebagai catatan mark yang hanya boleh digunakan dalam [[index#Comment|Comment]], karena tidak bagus ditampilkan di website.

Ada beberapa jenis task yang bisa digunakan:

### Checbox Task
Dengan syntax `* [ ]`. contohnya:

* [ ] Ini task hanya ceklist (dengan syntax `* [ ] Isi task` )
* [ ] task menjadi kabur ketika selesai

## State Task
Dengan syntax `* [IN PROGRESS]`. status bisa PROGRESS , DONE atau TODO. contohnya:

* [TODO] Ini task dengan sifat dikerjakan [priority: high] [assignee: @ginalne]
* [PROGRESS] Ini task dengan sifat belum dikerjakan
* [DONE] Ini task dengan sifat selesai
  
---

## Quotes
Tambahkan quotes jika ingin mengutip sesuatu dengan diawali simbol `>`, contohnya:

> “If you don’t know where you’re going, you may not get there.”
> — Yogi Berra

---

## Penutup
Sekian aturan yang wajib diikuti oleh Penulis. Harap di ingat.
Terimakasih

Selamat Menulis~


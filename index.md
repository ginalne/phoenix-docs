---
    status: draft
    pageDecoration:
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
  Some Comment... `@free` mention some here...

  some other comment or replied...
-->

>**note** Tips command
>Anda bisa ketika perintah **`/asking`** untuk memulai komen, dan **`/answer`** untuk menjawab (harap kursor perlu didalam comment).
>
>seperti contoh:

<!--
  `@ginalne` <small style="opacity: 0.5">at 2026-10-02 21:21</small>
  Hallo semua @everynyaw

  *ketik `/answer` disini*
  
-->

>**note** Kelebihan
>Comment tidak akan tampil di website, jadi gunakan section ini untuk berdiskusi

---

## Admonition
Admonition adalah section dalam penulisan dokumentasi yang dibuka dengan `>**note**`, `>**warning**`, atau `>**danger**`, isi dari info atau warning dapat ditulis dengan format berikut:

>**note** Judul Info
>Silahkan isi deskripsi info secara bebas

Anda dapat menggunakan ketik `/note-admonition` lalu Enter untuk membuat info.

>**warning** Judul Warning
>Silahkan isi deskripsi warning secara bebas

Anda dapat menggunakan ketik `/warning-admonition` lalu Enter untuk membuat peringatan.

>**danger** Judul Danger
>Silahkan isi deskripsi danger secara bebas

Anda dapat menggunakan ketik `/danger-admonition` lalu Enter untuk membuat larangan.

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

### Checkbox Task
Dengan syntax `* [ ]`. contohnya:

* [ ] Ini task hanya ceklist (dengan syntax `* [ ] Isi task` )
* [ ] task menjadi kabur ketika selesai

## State Task
Dengan syntax `* [STATE]`. state bisa diisi PROGRESS , DONE atau TODO. contohnya:

* [TODO] Ini task dengan sifat dikerjakan [priority: high] [assignee: @ginalne]
* [PROGRESS] Ini task dengan sifat belum dikerjakan
* [DONE] Ini task dengan sifat selesai
  
---

## Quotes
Tambahkan quotes jika ingin mengutip sesuatu dengan diawali simbol `>`, contohnya:

> “If you don’t know where you’re going, you may not get there.”
> — Yogi Berra

---

## Table
Tambahkan table jika ingin membuat informasi dengan ketik `/table` lalu Enter, contohnya:

| Header A | Header B |
|----------|----------|
| Cell A | Cell B |

---

## Tambahan
Harap isi enter 2x diakhir dokumen.

---

## Penutup
Sekian tips dan aturan yang wajib diikuti oleh Penulis. Harap di ingat.
Terimakasih

Selamat Menulis ~


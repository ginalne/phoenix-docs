---
    status: draft
    title: Melihat Detail Node
    description: Cara membuka detail Node untuk melihat atributnya tanpa mengubah data.
    pageDecoration:
      icon: x
      tree:
        priority: 6
---

# Melihat Detail Node

Detail menampilkan atribut [[Docs/Tipe Data/Node|Node]] tanpa mengubahnya. Gunakan [[^field|Detail]] untuk memeriksa posisi Node, sedangkan perubahan dilakukan lewat [[^field/edit|Edit]].

## Membuka Detail

![[Docs/Modul Data/Tree/Node/detail-node.png|Detail Node]]

1. Buka halaman kerja [[Docs/Modul Data/Tree/Apa itu Tree|Tree]].
2. Klik kanan [[Docs/Tipe Data/Node|Node]] yang akan dilihat ➜ [[^field|Detail]].

### Informasi pada Detail

| Informasi | Penjelasan |
| --------- | ---------- |
| [[^field|Name]] | Nama Node. |
| [[^field|Order]] | Urutan Node di antara saudara kandung. |
| [[^field|Parent]] | Node induk. Origin tidak memiliki induk. |
| [[^field|Children]] | Daftar Node anak langsung. |

<!--
  * [TODO] Informasi pada Detail saya ambil dari atribut Node (Name, Order, Parent, Children). Mohon konfirmasi isi sebenarnya, termasuk apakah ada informasi lain (misalnya Tree pemilik atau asal Node hasil clone).
    Jawaban: Informasi Name, Children (semisal 1.Grandchildren A, 2. Granchildren B, 3. Grandchildren C), dan Ancestor (semisal Origin). Bagian ancestor ada label anchor yang dapat diganti dengan klik, akan mengubah urutan dari 1 (anchor) dan selanjutnya hingga ancestor terdekat, fungsinya agar memudahkan menghitung jarak kedalaman ancestor, interaksi ini tidak disimpan jadi akan hilang ketika diclose.
  * [DONE] Letakkan gambar detail-node.png dengan penanda angka pada setiap informasi di tabel.
-->

## Membuka Detail Langsung

Anda dapat membuat klik kanan langsung membuka Detail tanpa menampilkan menu konteks.

1. Klik [[^field|Context]] di bagian bawah area kerja untuk mengganti nilainya menjadi `Detail`.
2. Klik kanan [[Docs/Tipe Data/Node|Node]]. Detail terbuka langsung.

>**note** Perubahan Context bersifat sementara
> Penggantian [[^field|Context]] di halaman kerja hanya berlaku sementara. Untuk mengubah nilai awalnya, gunakan [[^field|Default Configuration]] pada [[Docs/Modul Data/Tree/Apa itu Tree#Mengubah Tree|Edit Tree]].

<!--
  * [TODO] Mohon konfirmasi apakah satu klik pada Context berpindah ke nilai berikutnya (Menu, Edit, Detail) atau membuka pilihan.
    Jawaban: berpindah ke nilai berikutnya.
-->

## Lihat Juga

- [[Docs/Modul Data/Tree/Node/Mengubah Nama|Mengubah Nama Node]]
- [[Docs/Modul Data/Tree/Node/Mengubah Urutan|Mengubah Urutan Node]]
- [[Docs/Modul Data/Tree/Node/Pengenalan|Tree Node]]
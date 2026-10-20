---
  pageDecoration:
    tree:
      priority: -8
  tags:
    meta
    prompt
---
2026-10-19 13:00

/phoenix-docs-knowledge  /phoenix-docs-silverbullet 

Tolong saya membuat halaman "Apa itu Gallery?".
base knowledge:

![[prompt/phoenix.ginalne.com_testing_kanban_13(Documentation) (2).png]]
![[prompt/phoenix.ginalne.com_testing_gallery_4(Documentation) (1).png]]
![[prompt/phoenix.ginalne.com_testing_gallery_4(Documentation).png]]
/phoenix-docs-knowledge  /phoenix-docs-silverbullet 

Tolong saya membuat halaman "Apa itu Gallery?".
base knowledge:

1. Gallery menyajikan data dalam bentuk kartu visual yang menonjolkan gambar atau konten dari setiap data. Komponen ini ideal untuk koleksi yang bersifat visual, seperti katalog, portofolio, atau daftar aset, sehingga data lebih mudah dikenali sekilas.
2. Saat membuat Gallery, wajib mengisi Table dan Filter jika dibutuhkan (belum ada digambar tapi akan diupdate nanti). Filter adalah list dengan field kondisi seperti Query (kolom, operator, operand).
4. Klik setting akan memunculkan modal Setup Gallery Template.
5. Setiap Row pada Table akan tampil sebagai kartu didalam Gallery.
6. Kartu memiliki template sebagai berikut:
   1. Column yang di isi akan tampil sesuai dengan posisi template nya. Class adalah nilai text yang sesuai dengan nama class styling.
   2. Header, yaitu memiliki display flex-row dan berada pada bagian paling atas dalam kartu. Urutan pertama hingga terakhir dalam daftar adalah dari kiri ke kanan.
   3. Body, yaitu memiliki display flex-col dan urutannya atas ke bawah.
   4. Footer, yaitu memiliki display flex-row dan berada pada bagian paling bawah dalam kartu. Urutan pertama hingga terakhir dalam daftar adalah dari kiri ke kanan.
7. Jika template kosong (seperti saat pertama kali Gallery dibuat), tampilan kartu gallery adalah Kolom Alias dalam tabel (yang biasanya adalah nama dengan format Short Text).
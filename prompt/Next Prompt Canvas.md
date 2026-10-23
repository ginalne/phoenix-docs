---
  pageDecoration:
    tree:
      priority: -12
  tags:
    meta
    prompt
---

2026-10-23 16:00
![[prompt/2026-10-23_16-17-18.png]]
![[prompt/2026-10-23_16-17-22.png]]
Semua sudah ok, selanjut bisakah kita buat beberapa halaman (struktur akan diikuti oleh Widget lain) yaitu Widget Table dan Widget Pie.

Widget Table:

Bagian header ada "123" adalah untuk menunjukan pagination, sedangkan kaca pembesar adalah memunculkan toolbar search.

Widget Pie:

Bagian header ada Data dengan input Query (kaidah Series Output), dan Limit dengan maximal jumlah data yang muncul. Layout toolbar memiliki design panel dengan penjelasan berikut:

*   hole : berapa lubang pada pie
*   gap : gap antar data
*   theme : tema warna
*   gradient : gradasi warna dari tengah ke pinggir (transparent to color).
*   offset : batas akhir gradasi, jika 75% artinya gradasi dari tengah sampai sekitar 75% ke ujung lingkaran.
*   label: label dalam pie (none, label, value, percent, all \[label - value\].
*   min : derajat minimum pie untuk menampilkan label.
*   legends : posisi legenda (right, bottom, hidden).
*   Total : toggle, menampilkan total ditengah
*   size: font size dari tampilan total ditengah.
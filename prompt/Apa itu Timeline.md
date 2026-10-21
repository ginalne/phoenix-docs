---
  pageDecoration:
    tree:
      priority: -8
  tags:
    meta
    prompt
---
2026-10-21 14:00

/phoenix-docs-knowledge  /phoenix-docs-silverbullet 

Tolong saya membuat halaman "Apa itu Timeline?".
base knowledge:

![[prompt/phoenix.ginalne.com_testing_enum_46(Documentation) (1).png]]
![[prompt/phoenix.ginalne.com_testing_timeline_15(Documentation).png]]

![[prompt/phoenix.ginalne.com_testing_timeline_15(Documentation) (3).png]]

![[prompt/phoenix.ginalne.com_testing_timeline_15(Documentation) (1).png]]
![[prompt/phoenix.ginalne.com_testing_timeline_15(Documentation) (2).png]]
/phoenix-docs-knowledge  /phoenix-docs-silverbullet 

Tolong saya membuat halaman "Apa itu Timeline?".
base knowledge:

1. Timeline menampilkan data dalam urutan waktu sehingga Anda dapat memantau seperti jadwal, riwayat aktivitas, dan perkembangan suatu proses dengan lebih mudah linimasa. Komponen ini cocok untuk perencanaan, pelacakan progres, serta melihat hubungan antar peristiwa dalam satu rentang waktu.
2. Timeline memiliki Timeline Event dan Timeline Data.
3. Timeline Event berfungsi untuk membuat trigger Event (ke Flow Block Pulser) dengan/tanpa pengulangan. Konteks menu pada block Timeline Event: Edit, Add Data, Add Event, Zoom, Delete Event.
4. Timeline Data berfungsi untuk membuka data sumber dengan bantuan Query. Konteks menu pada block Timeline Event: Rename Data, Add Data, Add Event, Zoom, Delete Data.
5. Klik kiri pada row akan membuka popup preview (judul, start, end, status, calendar, relative, progress dan lain-lain) form edit (akses tetap mengikuti Access Data pada sumber). Konteks menu pada Row dalam Timeline Data adalah Edit, View, Add Row, Add Data, Add Event, Zoom, Delete Row.
6. Konteks menu pada bagian yang kosong: Add Data, Add Event, Zoom
7. Konteks menu Zoom memiliki cabang: Zoom In, Zoom Out, Quarter - Month, Month - Week, Week - Date, Week - Dayweek, Date - Hour, Time - 30 Minute, Time - 10 Minute, Time - 1 Minute, Minute - Second.
8. Klik kiri
7. Klik setting akan memunculkan modal Setup Gallery Template.
8. Setiap Row pada Table akan tampil sebagai kartu didalam Gallery.
9. Kartu memiliki template sebagai berikut:
   1. Column yang di isi akan tampil sesuai dengan posisi template nya. Class adalah nilai text yang sesuai dengan nama class styling.
   2. Header, yaitu memiliki display flex-row dan berada pada bagian paling atas dalam kartu. Urutan pertama hingga terakhir dalam daftar adalah dari kiri ke kanan.
   3. Body, yaitu memiliki display flex-col dan urutannya atas ke bawah.
   4. Footer, yaitu memiliki display flex-row dan berada pada bagian paling bawah dalam kartu. Urutan pertama hingga terakhir dalam daftar adalah dari kiri ke kanan.
10. Jika template kosong (seperti saat pertama kali Gallery dibuat), tampilan kartu gallery adalah Kolom Alias dalam tabel (yang biasanya adalah nama dengan format Short Text).
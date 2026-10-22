---
  pageDecoration:
    tree:
      priority: -10
  tags:
    meta
    prompt
---
2026-10-22 14:30

![[prompt/phoenix.ginalne.com_testing_dashboard.png]]
![[prompt/phoenix.ginalne.com_testing_form_15(Documentation).png]]

![[prompt/2026-10-22_14-47-51.png]]
![[prompt/2026-10-22_14-49-38.png]]
![[prompt/2026-10-22_14-50-59.png]]
![[prompt/2026-10-22_14-53-17.png]]
![[prompt/2026-10-22_15-53-04.png]]


/phoenix-docs-knowledge  /phoenix-docs-silverbullet 

Tolong saya membuat halaman "Apa itu Form?".
base knowledge:

1. Form adalah komponen untuk menginput, melihat, dan mengubah data secara terstruktur. Setiap kolom ditampilkan sebagai field yang jelas dan terarah, sehingga proses pengisian data menjadi lebih rapi, konsisten, dan minim kesalahan. Anda juga dapat membagikan Form kepada publik agar proses pengumpulan data bisa lebih cepat dan efektif.
2. Form dapat memiliki beberapa halaman, dan disetiap halaman akan ada informasi Start Building dengan pemilihan layout (informasi ini hanya tampil di Edit Mode).
3. Bagian publish form adalah konfigurasi untuk mengubah form menjadi di publikasi.
4. Informasi submission (sukses, menunggu, gagal) dapat diklik agar menampilkan konten (disebelah kanan) Submission List, yaitu grafik dan daftarnya, dapat di filtrasi ataupun dicari.
5. Pada mode Edit informasi binding bisa dilihat, focus node dengan klik kiri.
6. Setiap aksi select (klik kiri) dalam Node akan menampilkan card konfigurasi (seperti binding, state, attribute, children atau parent), serta header (untuk shortcut action) yang selalu ada tombol Remove untuk menghapus Node.
7. Khusus penjelasan keunikan masing-masing Node akan dijelaskan di halaman [[Docs/Modul Interface/Form/<Tipe>/<Nama Node>/Penjelasan|<Nama Node>]].

techincal knowledge:
1. Node dalam form adalah satu objek yang bisa digunakan untuk memetakan konten dalam Form, dengan kategori Layout (Card, Full, Split, Accordion), Display (Text, Table, Tooltip, Qr, Chrono), Input (Basic, Quiz, Table, List).
2. Layout berfungsi untuk menjadi template, khusus tipe ini memiliki field “Type something here to add...” yaitu untuk menambahkan node didalamnya.
3. Display memiliki fungsi untuk menampilkan sesuatu informasi yang statis atau expression dari binding value (semisal nilai total dan sebagainya).
4. Input memiliki fungsi untuk input ataupun menampilkan sesuatu informasi yang berlaku di binding.
5. Form memiliki binding yaitu ikatan hirarki agar input dan hasil akhir (binding ke table row dan relasinya) dapat sesuai.
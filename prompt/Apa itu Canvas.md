---
  pageDecoration:
    tree:
      priority: -11
  tags:
    meta
    prompt
---

/phoenix-docs-knowledge  /phoenix-docs-silverbullet 

Tolong saya membuat halaman "Apa itu Canvas?".
base knowledge:

1. Canvas adalah komponen untuk menginput, melihat, dan mengubah data secara terstruktur. Setiap kolom ditampilkan sebagai field yang jelas dan terarah, sehingga proses pengisian data menjadi lebih rapi, konsisten, dan minim kesalahan. Anda juga dapat membagikan Form kepada publik agar proses pengumpulan data bisa lebih cepat dan efektif.
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

answer:
1. Tombol [[^button/edit|Edit]] mengubah atribut Form (Name dan Description, lalu Update) seperti komponen lain, sedangkan toggle mode yang berpindah antara View dan Edit Mode. tombol [[^button/save|Save]] aktif ketika ada perubahan, bisa ditekan manual atau menunggu sekitar 3 detik (auto save).
2. mode read only itu ketika bukan dalam edit mode. Toggle ke edit mode bisa dlakukan jika akses workspace edit data = allow.
3. language dalam publish adalah form publik, single submission yaitu per perangkat. kalau status jadi non-active maka form tidak bisa dikirim (hanya dilihat).
4. Bagian Template di Start Building belum ada, itu ada untuk mempermudah styling. (sama hal nya menggunakan node yang tersedia dan mengubah konfigurasi stylenya).
5. Hanya menghapus template dan history submission, data yang sudah tersimpan tidak langsung terhapus. (ada pengaruh juga ketika publik sedang mengisi, akan error ketika mencoba mengirim).
6. Form mengikuti Comp. Access, Data Access, dan Function Access (View Publish dan Publish) seperti komponen lain. Data Access yang dimaksud adalah setiap perubahan Node dan atributnya didalam Form.
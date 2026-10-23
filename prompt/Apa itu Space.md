---
  pageDecoration:
    tree:
      priority: -12
  tags:
    meta
    prompt
---
2026-10-23 08:30


![[prompt/phoenix.ginalne.com_testing_canvas_14(Documentation) (4).png]]
![[prompt/phoenix.ginalne.com_testing_space_4(Documentation).png]]


![[prompt/phoenix.ginalne.com_testing_canvas_14(Documentation) (2).png]]
![[prompt/2026-10-23_02-35-36.png]]

/phoenix-docs-knowledge  /phoenix-docs-silverbullet 

Tolong saya membuat halaman "Apa itu Space?".
base knowledge:

1. Space adalah komponen yang menaungi dan mengorganisasi data dalam bentuk 3D (tiga dimensi). Dengan Space, Anda dapat memvisualisasikan data beserta hubungan antar data dalam ruang tiga dimensi dan menjelajahinya dari berbagai sudut pandang, sehingga pola dan keterkaitan yang sulit terlihat pada tampilan tabel menjadi lebih mudah dipahami.
2. Space memiliki 3 jenis data yaitu Weather, Environment dan Object.
3. Weather adalah data yang tampil sebagai _world effect_ dengan atribut Name, Description, jenis dengan properti uniknya, hal yang bisa digunakan saat ini adalah earth sky (dengan properti waktu [datetime / datetimezone]), dan sea (dengan properti level [number] dan wave rate [number]). Jika ada banyak jenis
4. Environment adalah data yang tampil sebagai object dengan atribut posisi (3d vector), skala (volume unit), rotation (eul)
5. Bagian publish adalah konfigurasi untuk mengubah canvas menjadi di publikasi. Hanya ada kolom Status (Active atau Non-Active) dan Link (link - copy - open new tab).
6. Pada mode Edit, focus widget dengan klik kiri.
7. Setiap aksi select (klik kiri) dalam widget akan menampilkan header toolbar dan design toolbar.
8. Khusus penjelasan keunikan masing-masing widget akan dijelaskan di halaman [[Docs/Modul Interface/Form/Widget/<Nama Widget>/Penjelasan|<Nama Widget>]].
9. Layout dalam Canvas hanya satu, tipe horizontal dan vertical dapat di toggle, sedangkan styling menggunakan layout & styling yang tersedia
10. Canvas memiliki binding yang dikonfigurasikan melalui tombol [[^button/setting|Binding]] yang bisa digunakan dalam query di widget (dalam bentuk modal). Binding ini memiliki default value, dan canvas bisa dibuka secara dinamis dengan binding dijadikan sebagai parameter. Semisal dibuat Canvas untuk mempresentasikan row table pesanan A, dengan desain yang menarik dengan informasi pesanan A, setelah itu ketika binding diubah ke pesanan B, maka desain yang menarik tadi disesuaikan informasi dengan pesanan B. (bagian ini tidak ada dalam lampiran, karena ada di rilis selanjutnya)
11. Modal binding berisi table dengan kolom Name (harus unik), Format dan Header (hanya pada format tertentu, mirip dengan konfigurasi kolom di Tabel), Default Value (nilai bawaan ketika parameter tidak ditentukan).
12. Tombol [[^button/edit|Edit]] mengubah atribut Canvas (Name dan Description, lalu Update) seperti komponen lain, sedangkan toggle mode yang berpindah antara View dan Edit Mode. tombol [[^button/save|Save]] aktif ketika ada perubahan, bisa ditekan manual atau menunggu sekitar 3 detik (auto save).
13. mode read only itu ketika bukan dalam edit mode. Toggle ke edit mode bisa dlakukan jika akses workspace edit data = allow.
14. Efek menghapus canvas hanya menghapus template dan properti termasuk query yang sudah dibuat, data sumber tetap aman. pengaruhnya hanya tautan yang sudah dishare akan invalid.
15. Canvas mengikuti Comp. Access, Data Access, dan Function Access (View Publish dan Publish) seperti komponen lain. Data Access yang dimaksud adalah setiap perubahan Widget dan atributnya didalam Canvas.
16. Gambar widget pie dilampirkan sebagai contoh. Harap dicatat bahwa toolbar masing-masing widget adalah unik.
---
  pageDecoration:
    tree:
      priority: -11
  tags:
    meta
    prompt
---
2026-10-23 02:30

![[prompt/phoenix.ginalne.com_testing_canvas_14(Documentation).png]]
![[prompt/phoenix.ginalne.com_testing_canvas_14(Documentation) (2).png]]
![[prompt/2026-10-23_02-35-36.png]]

/phoenix-docs-knowledge  /phoenix-docs-silverbullet 

Tolong saya membuat halaman "Apa itu Canvas?".
base knowledge:

1. Canvas adalah komponen untuk untuk menyusun, menghubungkan, dan memetakan data atau presentasi secara visual. Komponen ini memberi fleksibilitas untuk membuat diagram, tabel, maupun proyeksi tanpa dibatasi struktur baris dan kolom.
2. Canvas memiliki widget yang tersedia yaitu: text, chart\_pie, chart\_line, chart\_bar, chart\_radial, chart\_linear, table, kanban, gantt, timeline, gallery, space, button. Beberapa widget bekerja seperti interface lain (versi lite) namun dengan Query dan isinya tidak dapat dimanipulasi. Button dapat berfungsi sebagai trigger flow atau membuka komponen lain. 
3. Bagian publish adalah konfigurasi untuk mengubah canvas menjadi di publikasi. Hanya ada kolom Status (Active atau Non-Active) dan Link (link - copy - open new tab).
4. Pada mode Edit, focus widget dengan klik kiri.
6. Setiap aksi select (klik kiri) dalam widget akan menampilkan header toolbar dan design toolbar.
7. Khusus penjelasan keunikan masing-masing widget akan dijelaskan di halaman [[Docs/Modul Interface/Form/Widget/<Nama Widget>/Penjelasan|<Nama Widget>]].
8. Layout dalam Canvas hanya satu, tipe horizontal dan vertical dapat di toggle, sedangkan styling menggunakan layout & styling yang tersedia
9. Canvas memiliki binding yang dikonfigurasikan melalui tombol [[^button/setting|Binding]] yang bisa digunakan dalam query di widget (dalam bentuk modal). Binding ini memiliki default value, dan canvas bisa dibuka secara dinamis dengan binding dijadikan sebagai parameter. Semisal dibuat Canvas untuk mempresentasikan row table pesanan A, dengan desain yang menarik dengan informasi pesanan A, setelah itu ketika binding diubah ke pesanan B, maka desain yang menarik tadi disesuaikan informasi dengan pesanan B. (bagian ini tidak ada dalam lampiran, karena ada di rilis selanjutnya)
10. Modal binding berisi table dengan kolom Name (harus unik), Format dan Header (hanya pada format tertentu, mirip dengan konfigurasi kolom di Tabel), Default Value (nilai bawaan ketika parameter tidak ditentukan).
11. Tombol [[^button/edit|Edit]] mengubah atribut Canvas (Name dan Description, lalu Update) seperti komponen lain, sedangkan toggle mode yang berpindah antara View dan Edit Mode. tombol [[^button/save|Save]] aktif ketika ada perubahan, bisa ditekan manual atau menunggu sekitar 3 detik (auto save).
12. mode read only itu ketika bukan dalam edit mode. Toggle ke edit mode bisa dlakukan jika akses workspace edit data = allow.
13. Efek menghapus canvas hanya menghapus template dan properti termasuk query yang sudah dibuat, data sumber tetap aman. pengaruhnya hanya tautan yang sudah dishare akan invalid.
14. Canvas mengikuti Comp. Access, Data Access, dan Function Access (View Publish dan Publish) seperti komponen lain. Data Access yang dimaksud adalah setiap perubahan Widget dan atributnya didalam Canvas.
15. Gambar widget pie dilampirkan sebagai contoh. Harap dicatat bahwa toolbar masing-masing widget adalah unik.
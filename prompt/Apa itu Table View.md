---
  pageDecoration:
    tree:
      priority: -6
  tags:
    meta
    prompt
---
2026-10-16 19:00

![[prompt/preview.webp]]
![[prompt/preview (1).webp]]
/phoenix-docs-knowledge  /phoenix-docs-silverbullet 

Tolong saya membuat halaman "Apa itu Table View?".
base knowledge:

1. TableView adalah komponen dalam module interface yang berfungsi untuk menampilkan data Table menggunakan Query.
2. Query yang diisi wajib menggunakan header Table (spesifik tentang header dapat dilihat di [[Docs/Tipe Data/Query]].
3. TableView memiliki data bisa lebih dari satu, yang setiap datanya dapat menampung satu Query, nama dan konfigurasi tampilan (full, half, quarter of screen).
4. Kegunaan komponen interface ini berguna untuk menampilkan data Table lebih dari satu dan dapat dikontrol (menampilkan kolom tertentu menggunakan Show/Hide dalam Query) atau difiltrasi (dengan menambahkan Where condition di Query-nya).
5. Harap maknai informasi ini: Setiap field dapat diisi dan ditambahkan seperti pada komponen Table, namun beberapa kolom yang difiltrasi akan otomatis terisi. semisal ada kondisi EnumData di kolom tertentu yang tidak tampil di table view karena Query-nya tidak menampilkan itu, namun ketika menambahkan row, kolom tersebut akan langsung terisi agar data tetap tampil di table view tersebut (karena jika tidak diisi, data akan menghilang ketike di Refresh).
6. Access Data di Workspace untuk TableView adalah mengubah datanya, seperti rename, edit query dan mengubah konfigurasi. namun untuk perubahan pada row atau mengubah isi cell diatur dalam konfigurasi data TableView (bukan melalui workspace). Namun tetap, perubahan data cell di Table yg dipanggil oleh Query tersebut tetap mengikuti access Table tersebut didalam Workspace (jika workspace tidak mengijinkan edit data di Table tersebut, maka tetap tidak bisa, meskipun akses dalam TableView diijinkan). *note untuk claude: aturan ini juga berlaku dengan interface lain yang dapat memanipulasi data apapun di komponen dalam Modul Data.
7. Tampilan menambahkan dalam halaman kerja TableView dilampirkan. Contoh pada halaman adalah 3 data dengan nama : All Name, Name Level 2, New Data (Query belum diisi). Query pada Name Level 2 ada where level = level 2.
8. setiap data dapat toggle collapse/expand dengan klik.
9. contextmenu pada data adalah : Rename, Add Row (menambahkan row pada table), Add Data (menambahkan data), Delete Data (menghapus data dengan konfirmasi).
10. Cara menggunakan Query dijelaskan di [[Docs/Tipe Data/Query]].
11. Search pada header adalah mencari kata kunci disemua kolom dalam data.
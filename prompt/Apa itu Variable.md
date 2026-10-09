---
  pageDecoration:
    tree:
      priority: -1
  tags:
    meta
    prompt
---
2026-10-06 06-00

![[prompt/2026-10-06_06-06-41.png]]

/phoenix-docs-silverbullet /phoenix-docs-knowledge

Tolong buatkan dokumentasi phoenix berjudul "Apa itu Variable". Directory: Docs/Modul Data/Variable/Apa itu Variable

new knowledge:

1.  Variabel merupakan komponen yang dikenali semua komponen sebagai satu sumber data universal (dalam ruang lingkup Pro). Komponen ini secara \_default\_ dibuat ketika memulai Pro (di folder root) dan tidak dapat dihapus namun dapat dipindahkan, di manajemen folder, tidak dapat menambahkan komponen variabel baru (header). Nama default headernya adalah "Variables" dan tidak bisa di ganti.
    
2.  Isi Data variable dimulai dengan kosong, untuk menambahkannya perlu membuka halaman kerja variable.
    
3.  Contoh pada gambar dilampirkan. Agar kamu (claude) memahami contoh: Admin Google adalah workspace saat ini. Inventory sampai New Flow adalah komponen yang sudah saya buat. Fokus nya ke bagian Variables yang hanya satu, dan halaman kerja berbentuk tabel.
    
4.  Kolom dalam tabel tersebut adalah: Name, Type, Value, Description, Created At, Updated At.
    
5.  Antar baris tidak boleh memiliki Name yang sama. Created At dan Updated At terisi otomatis. Type adalah isian tipe data, sedangkan Value adalah nilai yang disimpan berdasarkan Type nya.
    
6.  Ketika ada field (di komponen lain) dengan tipe data Variable, maka pilihannya adalah daftar di tabel ini.
    
7.  Komponen di modul logic seperti flow, bisa mengisi field Variable dengan namanya saja (dalam bentuk string). Jika memang tidak ditemukan, maka akan terlihat laporan errornya di Flow Activity.
    
8.  Salah satu fungsi variable juga adalah untuk mengaliaskan nilai value agar tidak dapat diketahui isinya oleh tim, namun bisa digunakan demi kebutuhan integrasi. Contoh penggunaannya semisal nilai IP Address server hub, API Key provider AI tertentu. Walaupun tujuan utama nya adalah agar environment Pro memiliki sebuah konstanta (agar nilai konfigurasi tidak redundant dan ada coupling), sekaligus sebagai source of truth.
    
9.  daftar variable bisa dihapus (gambar yang berikan ada bug).
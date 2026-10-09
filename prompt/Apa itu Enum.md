---
  pageDecoration:
    tree:
      priority: -2
  tags:
    meta
    prompt
---
2026-10-07 23-00

![[prompt/2026-10-07_23-56-04.png]]
![[prompt/2026-10-08_00-05-56.png]]
/phoenix-docs-silverbullet /phoenix-docs-knowledge

1. Enum adalah salah satu komponen dalam modul [[Docs/Modul Data/Pengenalan|Data]] di Phoenix. 
2. Enum dapat digunakan sebagai deret data atau yang sering dikenal dengan Master Data. Sifat data ini digunakan sebagai pilihan, menu, opsi ataupun kategori. Setiap Enum memiliki banyak [[Docs/Tipe Data/EnumData]] didalamnya. Salah satu atribut penting dalam Enum adalah [[Docs/Modul Data/Enum/Konfigurasi Tegas]] (penjelasan fungsi field Strict On Selected).
3. field dengan format EnumData akan menampilkan pilihan dari daftar dengan Selectable bernilai Yes.
4. Setiap baris memiliki kolom Value berdasarkan Format di konfigurasi Enum.
5. Field header adalah header untuk format dengan tipe data yang perlu header.
6. fungsi merge dan event akan dijelaskan dihalaman lain
7. Fungsi Add Row adalah menambahkan baris (EnumData).
8. atribut Name tidak boleh sama didalam Enum yang sama.
9. Hubungan Tipe Data dengan Header : tipe data format => tipe data header, EnumData => Enum Column, Table Row => Table, TableData => Column, Node => Tree
10.  Masih bisa, akan tetapi akan ada warning dahulu untuk dapat melakukan force update (loss or lossless \[converted\]).
11.  Betul, menghapus enum akan kehilangan enumdata. Namun relasi dari komponen lain perlu dihapus terlebih dahulu.
12.  Iya tetap bisa, toggle selectable hanya untuk field.
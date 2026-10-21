---
    status: release
    title: "FAQ : Enum"
    description: Pertanyaan yang sering diajukan pada komponen Enum
    pageDecoration:
      tree:
        priority: -10
    tags:
      draft
---
# FAQ : Enum

Berikut adalah pertanyaan yang sering diajukan pada komponen Enum:

> **faq**
> **Apa bedanya Enum dengan EnumData?**
> Enum adalah komponen yang menyimpan daftar, sedangkan [[Docs/Tipe Data/EnumData]] adalah setiap baris di dalamnya.
> **Mengapa pilihan saya tidak muncul di field?**
> Pastikan [[^field|Selectable]] pada [[Docs/Tipe Data/EnumData]] bernilai [[^value/boolean/true]]. Hanya [[Docs/Tipe Data/EnumData]] dengan [[^field|Selectable]] bernilai [[^value/boolean/true]] yang tampil sebagai pilihan.
> **Apakah EnumData dengan Selectable No masih bisa dipakai?**
> Bisa. [[^field|Selectable]] hanya memengaruhi daftar pilihan pada field, bukan pemakaian di tempat lain.
> **Bolehkah dua EnumData memiliki Name yang sama?**
> Tidak, selama keduanya berada di Enum yang sama.
> **Mengapa Enum saya tidak bisa dihapus?**
> Hapus terlebih dahulu relasi dari komponen lain yang masih memakai Enum tersebut, lalu ulangi penghapusan.


---
    status: release
    title: "FAQ : Space"
    description: Pertanyaan yang sering diajukan pada komponen Space
    pageDecoration:
      tree:
        priority: -10
    tags:
      draft
---
# FAQ : Space

Berikut adalah pertanyaan yang sering diajukan pada komponenSpace:

> **faq**
> **Apa perbedaan Environment dan Object?**
> [[#Mengelola Environment|Environment]] adalah benda statis tanpa logika yang dibuat dari file 3D. [[#Mengelola Object|Object]] memiliki logika yang disiapkan di [[Docs/Modul Developer/Model/Apa itu Model|Model]] dan mengambil data riil lewat [[Docs/Tipe Data/Query|Query]] Table Output.
> **Mengapa Weather yang saya tambahkan tidak berlaku?**
> Hanya satu Weather untuk setiap [[^field|Type]] yang berlaku. Pastikan [[^field|Status]] bernilai [[^value/boolean/true]] dan [[^field|Priority]]-nya paling kecil dibanding Weather lain dengan [[^field|Type]] yang sama.
> **Mengapa semua objek 3D pada Object tampil sama?**
> Periksa kolom [[^field|Static]] pada [[#Mengatur Model Attribute|Model Attribute]]. Atribut [[^value/radio|static]] bernilai sama untuk semua objek 3D, pilih [[^value/radio|bind]] agar nilainya mengikuti kolom [[Docs/Tipe Data/Query|Query]].
> **Apakah mengubah nilai di Panel Properti mengubah data sumber?**
> Hanya untuk [[#Mengelola Object|Object]]. Perubahan memengaruhi [[Docs/Tipe Data/Row]] sebenarnya selama [[Docs/Modul Developer/Workspace/Data Access|Data Access]] sumber mengizinkan. Untuk [[#Mengelola Weather|Weather]] dan [[#Mengelola Environment|Environment]], perubahan tidak memengaruhi Row sumber.
> **Mengapa saya tidak bisa menambah atau menghapus data di Outliner?**
> Penambahan dan penghapusan data mengikuti [[Docs/Modul Developer/Workspace/Data Access|Data Access]] Space di Workspace. Hubungi pengelola Workspace Anda untuk memeriksa pengaturannya.
> **Bagaimana cara mencari data di Space?**
> Gunakan [[^field|Search Space Data...]] pada bilah navigasi untuk mencari data di Outliner berdasarkan Name, termasuk data yang jumlahnya banyak pada [[#Mengelola Object|Object]].
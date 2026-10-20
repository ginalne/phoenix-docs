---
    status: release
    title: "FAQ : Table View"
    description: Pertanyaan yang sering diajukan pada komponen Table View
    pageDecoration:
      tree:
        priority: -10
    tags:
      draft
---
# FAQ : Table View

Berikut adalah pertanyaan yang sering diajukan pada komponen Table View:

> **faq**
> **Mengapa Row yang baru saya tambahkan tidak hilang walaupun kolom filternya tidak tampil?**
> Kolom yang menjadi syarat [[Docs/Tipe Data/Query#Filter|Filter]] terisi otomatis saat baris ditambahkan, sehingga baris tetap memenuhi kondisi [[Docs/Tipe Data/Query|Query]]. Selengkapnya lihat [[#Mengelola Row pada Data]].
> **Mengapa muncul pesan [[^field|Query column output is not valid!]]?**
> Query pada Data belum diisi atau outputnya tidak valid. Pastikan Query memakai [[Docs/Tipe Data/Query#Table Output]], lalu atur di [[#Mengatur Query]].
> **Apakah menghapus Data juga menghapus data sumber?**
> Tidak. Menghapus Data hanya menghapus [[Docs/Tipe Data/Query]] dan konfigurasinya. Namun menghapus Row lewat [[^button/delete|Delete]] pada kolom [[^field|Action]] menghapus baris dari sumber.
> **Mengapa saya tidak dapat mengubah cell padahal konfigurasi Data mengizinkan?**
> Perubahan data tetap mengikuti [[Docs/Modul Developer/Workspace/Data Access|Data Access]] Table di [[Docs/Modul Developer/Workspace/Apa itu Workspace| Workspace]]. Jika [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]] tidak mengizinkan, baris tidak dapat diubah dari Table View.
> **Apa bedanya Table View dengan komponen data lain seperti Table?**
> Table View menampilkan data sumber seperti [[Docs/Modul Data/Table/Apa itu Table|Table]] dalam beberapa tampilan sekaligus dengan [[Docs/Tipe Data/Query]] berbeda.

---
    status: release
    title: "FAQ : Kanban"
    description: Pertanyaan yang Sering Diajukan pada komponen Kanban
    pageDecoration:
      tree:
        priority: -10
---
# FAQ : Kanban

Berikut adalah pertanyaan yang Sering Diajukan pada komponen Kanban:

> **faq**
> **Mengapa Kanban saya memiliki jumlah kolom tertentu?**
> Kolom Kanban mengikuti jumlah [[Docs/Tipe Data/EnumData|EnumData]] pada [[Docs/Tipe Data/Enum]] yang dipilih di [[^field|Table - Column]]. Jika [[Docs/Tipe Data/Enum]] memiliki 4 [[Docs/Tipe Data/EnumData]], Kanban memiliki 4 kolom.
> **Mengapa kartu hanya menampilkan satu teks?**
> Template kartu masih kosong, sehingga kartu menampilkan [[Docs/Modul Data/Table/Apa itu Table#Membuat Table|Alias]] dari [[Docs/Modul Data/Table/Apa itu Table|Table]]. Tambahkan [[^field|Column]] pada template di [[#Mengatur Template Kartu]].
> **Apa bedanya [[^value/radio|Global]] dan [[^value/radio|Local]]?**
> [[^value/radio|Global]] membuat perubahan template memengaruhi [[Docs/Tipe Data/EnumData]] lain dalam Kanban yang sama, sedangkan [[^value/radio|Local]] hanya menerapkannya pada satu [[Docs/Tipe Data/EnumData]]. Selengkapnya lihat [[#Global dan Local]].
> **Mengapa template kartu saya hilang setelah mengubah Kanban?**
> Template otomatis terhapus saat Anda mengganti [[Docs/Modul Data/Table/Apa itu Table|Table]] pada [[^field|Table - Column]]. Template tidak terhapus jika Anda hanya mengganti [[Docs/Tipe Data/Column]] pada [[Docs/Modul Data/Table/Apa itu Table|Table]] yang sama.
> **Apakah Row hilang jika Kanban dihapus?**
> Tidak. Kanban hanya menampilkan data, jadi [[Docs/Tipe Data/Row]] pada [[Docs/Modul Data/Table/Apa itu Table|Table]] tetap ada. Yang terhapus adalah Kanban beserta template kartunya.
> **Apakah menghapus kartu juga menghapus Row?**
> Ya. [[^field/delete|Delete Row]] pada menu konteks kartu menghapus [[Docs/Tipe Data/Row]] dari [[Docs/Modul Data/Table/Apa itu Table|Table]] sumber, bukan hanya kartu pada Kanban.


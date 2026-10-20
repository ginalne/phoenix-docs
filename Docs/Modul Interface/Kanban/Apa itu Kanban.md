---
    status: release
    title: "Apa itu Kanban?"
    description: Penjelasan komponen Kanban untuk memvisualisasikan data Table dalam bentuk kolom status atau kategori dan kartu.
    pageDecoration:
      icon: '<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="#aaa" viewBox="0 0 16 16">
  <path d="M13.5 1a1 1 0 0 1 1 1v12a1 1 0 0 1-1 1h-11a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1zm-11-1a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h11a2 2 0 0 0 2-2V2a2 2 0 0 0-2-2z"/>
  <path d="M6.5 3a1 1 0 0 1 1-1h1a1 1 0 0 1 1 1v3a1 1 0 0 1-1 1h-1a1 1 0 0 1-1-1zm-4 0a1 1 0 0 1 1-1h1a1 1 0 0 1 1 1v7a1 1 0 0 1-1 1h-1a1 1 0 0 1-1-1zm8 0a1 1 0 0 1 1-1h1a1 1 0 0 1 1 1v10a1 1 0 0 1-1 1h-1a1 1 0 0 1-1-1z"/>
</svg>

</svg>'
      tree:
        priority: 4
    icon: assets/icons/type/-1.svg
---
# Apa itu Kanban?

>**note** Kanban merupakan salah satu komponen dalam modul [[Docs/Modul Interface/Pengenalan|Interface]] di Phoenix.

Kanban adalah komponen yang menampilkan data dalam bentuk kolom-kolom berdasarkan status atau kategori. Setiap data direpresentasikan sebagai kartu yang dapat dipindahkan antar kolom.

Dengan Kanban, Anda dapat memvisualisasikan data secara tersegmentasi, misalnya data yang memiliki tahapan atau kategori. Kolom diambil dari [[Docs/Tipe Data/EnumData|EnumData]], kartu berasal dari [[Docs/Tipe Data/Row]] pada [[Docs/Modul Data/Table/Apa itu Table|Table]], dan tampilan kartu dapat Anda atur sendiri melalui template.

## Mengapa Menggunakan Kanban?

- **Segmentasi terlihat sekilas.** Setiap tahapan atau kategori tampil sebagai kolom sehingga posisi setiap data langsung terbaca.
- **Progres terpantau.** Header kolom menampilkan jumlah item, sehingga Anda tahu tahap mana yang menumpuk.
- **Terhubung langsung dengan data.** Setiap [[Docs/Tipe Data/Row]] pada [[Docs/Modul Data/Table/Apa itu Table|Table]] otomatis menjadi kartu sesuai nilai [[Docs/Tipe Data/EnumData|EnumData]] miliknya.
- **Tampilan kartu dapat diatur.** Anda menentukan [[Docs/Tipe Data/Column]] apa yang tampil pada bagian [[^field|Header]], [[^field|Body]], dan [[^field|Footer]] kartu, lengkap dengan gaya tampilannya.

## Konsep Utama

| Istilah | Penjelasan |
| ------- | ---------- |
| [[Docs/Modul Data/Table/Apa itu Table|Table]] | Sumber data Kanban. Setiap [[Docs/Tipe Data/Row]] menjadi satu kartu. |
| [[Docs/Tipe Data/EnumData]] | Nilai dari [[Docs/Modul Data/Enum/Apa itu Enum|Enum]] yang dijadikan kolom Kanban. |
| [[#Membuat Kanban|Table - Column]] | [[Docs/Tipe Data/Column]] berformat [[Docs/Tipe Data/EnumData]] yang wajib dipilih saat Kanban dibuat. |
| [[#Header Kolom Kanban|Kolom]] | Satu [[Docs/Tipe Data/EnumData]] ditampilkan sebagai satu kolom Kanban. |
| [[#Mengatur Template Kartu|Kartu]] | Representasi satu [[Docs/Tipe Data/Row]]. Kartu berada pada kolom sesuai nilai [[Docs/Tipe Data/EnumData]]-nya. |
| [[#Mengatur Template Kartu|Template]] | Pengaturan isi dan tata letak kartu: [[^field|Header]], [[^field|Body]], dan [[^field|Footer]]. |
| [[#Global dan Local]] | Cakupan template: berlaku untuk [[Docs/Tipe Data/EnumData]] lain dalam Kanban yang sama atau hanya untuk satu [[Docs/Tipe Data/EnumData]]. |

## Mengelola Kanban

Berikut adalah halaman yang menjelaskan cara untuk mengelola Kanban:
1. [[Docs/Modul Interface/Kanban/Membuat Baru]] Kanban dalam halaman kerja.
2. [[Docs/Modul Interface/Kanban/Mengubah]] Atribut Kanban seperti [[^field|Name]], [[^field|Description]], atau [[^field|Table - Column]].
3. [[Docs/Modul Interface/Kanban/Menghapus]] Kanban.
4. [[Docs/Modul Interface/Kanban/Mengatur Templat]] Kartu dalam Kanban.

## Antarmuka

Penjelasan antarmuka Kanban lihat selengkap nya di [[Docs/Modul Interface/Kanban/Antarmuka|Antarmuka Kanban]].

## Praktik Terbaik

- Pilih [[^field|Table - Column]] yang benar-benar mewakili **tahapan atau kategori**, karena setiap [[Docs/Tipe Data/EnumData]] menjadi satu kolom.
- Gunakan cakupan [[^value/radio|Global]] agar **tampilan kartu seragam** di semua kolom, dan [[^value/radio|Local]] hanya untuk kolom yang butuh tampilan khusus.
- Tampilkan **informasi yang paling penting** saja pada [[^field|Header]], [[^field|Body]], dan [[^field|Footer]] agar kartu mudah dipindai.
- Isi [[^field|Class]] secara **sederhana dan konsisten** supaya tampilan kartu rapi.
- Periksa **dampak ke data sumber** sebelum memakai [[^field/delete|Delete Row]], karena [[Docs/Tipe Data/Row]] ikut terhapus dari [[Docs/Modul Data/Table/Apa itu Table|Table]].

## Batasan dan Catatan

- [[^field|Table - Column]] wajib diisi dan harus berformat [[Docs/Tipe Data/EnumData|EnumData]]. Jumlah kolom Kanban mengikuti jumlah [[Docs/Tipe Data/EnumData]].
- Mengganti [[Docs/Modul Data/Table/Apa itu Table|Table]] pada [[^field|Table - Column]] otomatis menghapus template kartu, sedangkan [[Docs/Tipe Data/Row]] pada [[Docs/Modul Data/Table/Apa itu Table|Table]] sumber tetap ada.
- Perubahan template dengan cakupan [[^value/radio|Global]] memengaruhi [[Docs/Tipe Data/EnumData]] lain dalam Kanban yang sama, tidak lintas Kanban. Cakupan [[^value/radio|Local]] hanya memengaruhi satu [[Docs/Tipe Data/EnumData]].
- Jika template kosong, kartu hanya menampilkan [[Docs/Modul Data/Table/Apa itu Table#Membuat Table|Alias]] dari [[Docs/Modul Data/Table/Apa itu Table|Table]].
- Menghapus Kanban menghapus template kartu, tetapi tidak menghapus [[Docs/Tipe Data/Row]] pada [[Docs/Modul Data/Table/Apa itu Table|Table]].
- [[^field/delete|Delete Row]] pada menu konteks kartu menghapus [[Docs/Tipe Data/Row]] dari [[Docs/Modul Data/Table/Apa itu Table|Table]] sumber.
- Memindahkan kartu, [[^field/add|Add Row]], dan [[^field/delete|Delete Row]] mengubah data pada [[Docs/Modul Data/Table/Apa itu Table|Table]] sumber, sehingga memerlukan izin pada [[Docs/Modul Developer/Workspace/Data Access]] untuk data sumber.

## TL:DR

- **Definisi:** Kanban menampilkan [[Docs/Tipe Data/Row]] pada [[Docs/Modul Data/Table/Apa itu Table|Table]] sebagai kartu pada kolom status atau kategori.
- **Membuat:** isi [[^field|Table - Column]] berformat [[Docs/Tipe Data/EnumData|EnumData]]; setiap [[Docs/Tipe Data/EnumData]] menjadi satu kolom ([[#Membuat Kanban]]).
- **Antarmuka:** header kolom berisi jumlah item, [[^field|Name]] - [[^field|Description]], dan [[^button/setting]]; kartu dapat dipindahkan, dibuka, dan dikelola lewat menu konteks ([[#Antarmuka Kanban]]).
- **Template:** atur [[^field|Header]], [[^field|Body]], dan [[^field|Footer]] kartu lewat [[^button/setting|Setting]] ([[#Mengatur Template Kartu]]).
- **Cakupan:** [[^value/radio|Global]] memengaruhi [[Docs/Tipe Data/EnumData]] lain dalam Kanban yang sama, [[^value/radio|Local]] hanya satu [[Docs/Tipe Data/EnumData]] ([[#Global dan Local]]).
- **Hati-hati:** mengganti [[Docs/Modul Data/Table/Apa itu Table|Table]] menghapus template, [[^field/delete|Delete Row]] menghapus data sumber, dan mengubah data lewat kartu memerlukan izin data sumber.


## FAQ : Pertanyaan yang Sering Diajukan

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


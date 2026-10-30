---
    status: release
    title: "Mengatur Template Kartu"
    description: Penjelasan cara mengatur templat kartu di Kanban
    pageDecoration:
      tree:
        priority: -2
---
# Mengatur Templat Kartu

>**note** Bagian dari Kanban
> Template Kartu adalah pengaturan tampilan kartu pada komponen [[Docs/Modul Interface/Gallery/Apa itu Gallery|Gallery]] di modul [[Docs/Modul Interface/Pengenalan|Interface]].

![[Docs/Modul Interface/Kanban/setup-kanban.png]]

Template menentukan [[Docs/Tipe Data/Column]] apa saja yang tampil pada kartu dan di mana letaknya. Template dibagi menjadi tiga bagian:

| Bagian | Tata letak | Urutan |
| ------ | ---------- | ------ |
| [[^field|Header]] | Berbentuk baris (*flex-row*), berada di bagian paling atas kartu. | Dari kiri ke kanan sesuai urutan dalam daftar. |
| [[^field|Body]] | Berbentuk kolom (*flex-col*), berada di antara [[^field|Header]] dan [[^field|Footer]]. | Dari atas ke bawah sesuai urutan dalam daftar. |
| [[^field|Footer]] | Berbentuk baris (*flex-row*), berada di bagian paling bawah kartu. | Dari kiri ke kanan sesuai urutan dalam daftar. |

Setiap baris template berisi [[^field|Column]] yang akan ditampilkan, [[^field|Styling]], dan [[^field|Action]] berupa tombol [[^button/delete|Delete]] untuk menghapus baris tersebut dari template. Isi [[^field|Styling]] dengan [[Docs/Styling/Pengenalan|Styling]] yang dapat digunakan untuk mengatur tampilan [[^field|Column]] pada kartu, misalnya ukuran atau ketebalan teks.

1. Klik [[^button/setting|Setting]] pada header kolom [[Docs/Tipe Data/EnumData]] yang ingin diatur
2. Pada modal [[^field|Setup Kanban Template]], pilih cakupan template di [[^field|Column Template]] (lihat [[#Global dan Local]])
3. Tambahkan [[^field|Column]] pada bagian [[^field|Header]], [[^field|Body]], atau [[^field|Footer]]. Langkah rincinya ada di [[Docs/Modul Interface/Kanban/Mengatur Templat|Template Kartu]]
4. Klik [[^button|Update]]

### Global dan Local

Setiap [[Docs/Tipe Data/EnumData]] dapat memiliki pengaturan template dengan cakupan [[^value/radio|Global]] atau [[^value/radio|Local]]. Cakupan dipilih lewat toggle [[^field|Column Template]]: mati berarti [[^value/radio|Global]], aktif berarti [[^value/radio|Local]].

| Cakupan | Penjelasan |
| ------- | ---------- |
| [[^value/radio|Global]] | Bawaan. Perubahan template memengaruhi [[Docs/Tipe Data/EnumData]] lain dalam Kanban yang sama yang juga memakai cakupan [[^value/radio|Global]]. Tidak berlaku lintas Kanban. |
| [[^value/radio|Local]] | Perubahan template hanya diterapkan pada [[Docs/Tipe Data/EnumData]] tersebut. |

### Template Kosong

Jika template masih kosong (seperti saat Kanban baru dibuat), kartu hanya menampilkan [[Docs/Modul Data/Table/Apa itu Table#Membuat Table|Alias]] dari [[Docs/Modul Data/Table/Apa itu Table|Table]], yang biasanya berupa [[Docs/Tipe Data/Column]] berformat [[Docs/Format Data/String/Short Text]].


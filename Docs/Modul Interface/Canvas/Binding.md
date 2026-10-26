---
    status: release
    title: "Binding dalam Canvas"
    description: Penjelasan binding dalam komponen Canvas
    pageDecoration:
      tree:
        priority: 0
---
# Binding dalam Canvas

Binding adalah parameter Canvas yang dapat dipakai dalam [[Docs/Tipe Data/Query]] pada widget. Binding dikonfigurasikan melalui tombol [[^button/setting|Binding]] yang membuka modal. Setiap Binding memiliki nilai bawaan (*default value*), dan Canvas dapat dibuka secara dinamis dengan Binding sebagai parameter.

Modal Binding berisi tabel dengan kolom berikut:

| Kolom                            | Fungsi                                                                                                                                                                  |
| -------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[^field|Name]]                 | Nama Binding. Harus unik.                                                                                                                                               |
| [[^field|Format]]               | Format data Binding.                                                                                                                                                    |
| [[^field|Header]]               | Hanya diisi pada format tertentu, mirip dengan konfigurasi [[Docs/Tipe Data/Column|Column]] pada [[Docs/Modul Data/Table/Apa itu Table|Table]]. Bernilai N/A bila Format tidak membutuhkannya. |
| [[^field|Default Value]]        | Nilai bawaan ketika parameter tidak ditentukan.                                                                                                                         |

**Memakai Binding di Query.** Pada bagian nilai di [[Docs/Tipe Data/Query]] (misalnya pada [[Docs/Tipe Data/Query#Filter|Filter]]), Anda dapat mengisinya dengan Name Binding. Ketika parameter Canvas diubah, nilai dalam Query ikut berubah.

**Membuka Canvas dengan parameter.** Canvas dapat dibuka dengan parameter melalui tautan [[#Mempublikasikan Canvas|Publish]], widget Button yang sudah disiapkan, atau komponen lain yang dapat memanggil Canvas dengan parameter.

Sebagai contoh, Anda membuat Canvas untuk mempresentasikan rincian satu [[Docs/Tipe Data/Row|Row]] pesanan dengan desain menarik. Binding diisi dengan nomor pesanan, lalu dipakai pada Filter Query setiap widget. Ketika nilai Binding diganti dengan nomor pesanan lain, desain yang sama menampilkan informasi pesanan tersebut.


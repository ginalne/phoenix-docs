---
    status: release
    title: "Mengelola Timeline Data"
    description: 
    pageDecoration:
      tree:
        priority: 6
---
# Timeline Data

Timeline Data berfungsi untuk membuka data sumber di sumbu waktu dengan bantuan [[Docs/Tipe Data/Query|Query]]. Setiap Row hasil Query tampil sebagai satu blok. Satu Timeline dapat memiliki beberapa Timeline Data.

## Query

Query pada Timeline Data mengikuti kaidah Timeline Output ([[Docs/Tipe Data/Query#Timeline Output]]). Cara menyusun sumber data dan [[Docs/Tipe Data/Query#Filter|Filter]] sama seperti Query lainnya. Pada bagian [[Docs/Tipe Data/Query#Show or Hide|Show]], label [[^field|Name]], [[^field|Start]], dan [[^field|End]] menunjukkan [[Docs/Tipe Data/Column|Column]] yang dipakai Timeline.

| Label | Fungsi | Format Column |
| ----- | ------ | ------------- |
| [[^field|Name]] | Nama Row yang tampil di [[^field|Item List]] dan di samping blok. | - |
| [[^field|Start]] | Waktu mulai Row. | [[Docs/Tipe Data/DateTime]], [[Docs/Tipe Data/Date]], atau [[Docs/Tipe Data/DateTimeZone]] |
| [[^field|End]] | Waktu selesai Row. | [[Docs/Tipe Data/DateTime]], [[Docs/Tipe Data/Date]], atau [[Docs/Tipe Data/DateTimeZone]] |

Label yang wajib hanya [[^field|Name]] dan [[^field|Start]].

>**warning** Query belum valid
> Selama Query tidak memenuhi kaidah Timeline Output, misalnya belum menampilkan paling sedikit dua Column, Timeline Data menampilkan baris [[^field|Error]] dengan pesan "Query must at least have 2 showed columns!" dan tidak ada Row yang tampil. Penjelasan kesalahan lain ada di [[Docs/Tipe Data/Query#Error]].

## Mengelola Timeline Data

Berikut adalah halaman yang menjelaskan cara untuk mengelolanya:
1. [[Docs/Modul Interface/Timeline/Timeline Data/Menambahkan]] Timeline Data.
2. [[Docs/Modul Interface/Timeline/Timeline Data/Mengganti Nama]] pada Timeline Data.
3. [[Docs/Modul Interface/Timeline/Timeline Data/Mengatur Query]] pada Timeline Data.
4. [[Docs/Modul Interface/Timeline/Timeline Data/Menghapus]] Timeline Data.
5. [[Docs/Modul Interface/Timeline/Timeline Data/Mengelola Row]] dalam Timeline Data.

## Hak Akses Timeline Data

Hak akses Timeline Data berlapis, sama seperti Table View.

- Menambah, mengubah (nama, Query, dan konfigurasi), serta menghapus Timeline Data mengikuti Data Access Timeline di [[Docs/Modul Developer/Workspace/Data Access]].
- Row dan isinya hanya dapat dikelola bila dua syarat terpenuhi, yaitu Timeline Data berada pada mode `editable` dan Data Access data sumber di Workspace mengizinkan.

| Mode Timeline Data | Data Access data sumber | Hasil pada Row |
| ------------------ | ----------------------- | -------------- |
| `editable` | [[^value/boolean/allow]] | Row dapat ditambah, diubah, dan dihapus, dan blok dapat digeser. |
| `editable` | [[^value/boolean/disallow]] | Row hanya dapat dilihat. |
| `readonly` | [[^value/boolean/allow]] | Row hanya dapat dilihat. |
| `readonly` | [[^value/boolean/disallow]] | Row hanya dapat dilihat. |

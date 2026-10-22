---
    status: draft
    pageDecoration:
      icon: x
      tree:
        priority: 4
---
# Mengelola Timeline Data

Timeline Data berfungsi untuk membuka data sumber di sumbu waktu dengan bantuan [[Docs/Tipe Data/Query|Query]]. Setiap Row hasil Query tampil sebagai satu blok. Satu Timeline dapat memiliki beberapa Timeline Data.

## Query Timeline Data

Query pada Timeline Data mengikuti kaidah Timeline Output ([[Docs/Tipe Data/Query#Timeline Output]]). Cara menyusun sumber data dan [[Docs/Tipe Data/Query#Filter|Filter]] sama seperti Query lainnya. Pada bagian [[Docs/Tipe Data/Query#Show or Hide|Show]], label [[^field|Name]], [[^field|Start]], dan [[^field|End]] menunjukkan [[Docs/Tipe Data/Column|Column]] yang dipakai Timeline.

| Label | Fungsi | Format Column |
| ----- | ------ | ------------- |
| [[^field|Name]] | Nama Row yang tampil di [[^field|Item List]] dan di samping blok. | - |
| [[^field|Start]] | Waktu mulai Row. | [[Docs/Tipe Data/DateTime]], [[Docs/Tipe Data/Date]], atau [[Docs/Tipe Data/DateTimeZone]] |
| [[^field|End]] | Waktu selesai Row. | [[Docs/Tipe Data/DateTime]], [[Docs/Tipe Data/Date]], atau [[Docs/Tipe Data/DateTimeZone]] |

Label yang wajib hanya [[^field|Name]] dan [[^field|Start]].

>**warning** Query belum valid
> Selama Query tidak memenuhi kaidah Timeline Output, misalnya belum menampilkan paling sedikit dua Column, Timeline Data menampilkan baris [[^field|Error]] dengan pesan "Query must at least have 2 showed columns!" dan tidak ada Row yang tampil. Penjelasan kesalahan lain ada di [[Docs/Tipe Data/Query#Error]].

## Menambahkan Timeline Data

1. Klik [[^button/add|Add Data]], atau klik kanan ➜ [[^field|Add Data]]
2. Timeline Data baru tampil dengan Query kosong ([[^field|Empty]]) dan nama awal `New Data (n)`
3. Klik [[^button/q]] pada Timeline Data untuk mengatur [[Docs/Tipe Data/Query|Query]]
4. Pada bagian [[Docs/Tipe Data/Query#Show or Hide|Show]], pastikan Column untuk label [[^field|Name]], [[^field|Start]], dan [[^field|End]] sudah sesuai
5. Tutup popup Query dengan klik di luar popup

>**success** Timeline Data berhasil diatur
> Query tersimpan otomatis ketika popup ditutup, dan Row hasil Query langsung tampil sebagai blok di sumbu waktu.

## Mengubah Query Timeline Data

1. Klik [[^button/q]] pada Timeline Data
2. Ubah Query
3. Tutup popup Query dengan klik di luar popup

Perubahan Query tersimpan otomatis dan Row menyesuaikan hasil Query yang baru. Tidak ada tombol simpan.

## Mengubah Nama Timeline Data

1. Klik kanan judul Timeline Data ➜ [[^field|Rename Data]]
2. Isi nama baru
3. Klik [[^button/ok|Ok]]

## Menghapus Timeline Data

1. Klik kanan judul Timeline Data ➜ [[^field|Delete Data]]
2. Konfirmasi dengan klik [[^button|Delete]]

>**warning** Hanya konfigurasi yang terhapus
> [[^field|Delete Data]] hanya menghapus konfigurasi dan Query Timeline Data. Row pada data sumber tidak terhapus.

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

---
    status: release
    title: "Antarmuka Table"
    description: Penjelasan antarmuka di halaman kerja komponen Table
    pageDecoration:
      tree:
        priority: 0
---
# Antarmuka Table

Halaman kerja Table terdiri dari bilah navigasi di bagian atas dan tabel data di bagian bawah.

![[Docs/Modul Data/Table/halaman-kerja-table.png]]
Tabel data memiliki dua kolom tambahan di luar Column yang Anda buat: [[^field|ID]] di bagian awal (terisi otomatis) dan [[^field|Action]] di bagian akhir. Ikon kecil pada header setiap Column menunjukkan format Column tersebut.

### Bilah navigasi Table terdiri dari:

| Tombol                                         | Fungsi                                                                                                   |
| ---------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| [[^button/edit|Edit]]                          | Mengubah atribut Table, termasuk Column. Lihat [[#Mengubah Table]].                                      |
| [[^button/merge|Merge]]                        | Menggabungkan data Table. Penjelasan lengkap di [[Docs/Modul Data/Table/Table Row/Menggabungkan]].                         |
| [[^button/publish|Publish]]                    | Mengatur publikasi Table. Penjelasan lengkap di [[Docs/Modul Data/Table/Mempublikasi]].                       |
| [[^button/event|Event]]                        | Menghubungkan Table dengan [[Docs/Event/Apa itu Event|Event]]. Penjelasan lengkap di [[Docs/Modul Data/Table/Mengotomasi]]. |
| [[^button/refresh|Refresh]]                    | Memuat ulang tampilan halaman kerja.                                                                     |
| [[^field|Search Table Data...]]                | Mencari data pada Table.                                                                                 |

### Tombol pada tabel data

| Tombol                                | Fungsi                                                         |
| ------------------------------------- | -------------------------------------------------------------- |
| [[^button/add|Add Row]]               | Menambahkan Row baru. Tersedia di bawah baris terakhir dan di bagian bawah halaman, keduanya berfungsi sama. |
| [[^button/save|Save]]                 | Menyimpan perubahan pada Row. Aktif hanya ketika ada perubahan. |
| [[^button/delete|Delete]]             | Menghapus Row.                                                 |

### Interaksi Antarmuka Table

| Fungsi                          | Aksi                                                                                       |
| ------------------------------- | ------------------------------------------------------------------------------------------ |
| Melihat Column di sisi kanan    | Scroll horizontal pada bagian bawah tabel data.                                            |
| Berpindah halaman data          | Klik [[^button/left|Prev]] atau [[^button/right|Next]], atau isi nomor halaman lalu klik [[^button/empty|Go]]. |
| Mencari data                    | Ketik pada [[^field|Search Table Data...]].                                                |
| Membaca informasi jumlah data   | Lihat [[^field|Show 50 of 2 items, on page]] di bagian bawah halaman. Pada contoh tampilan, angka 50 adalah batas data per halaman dan angka 2 adalah jumlah seluruh data. |

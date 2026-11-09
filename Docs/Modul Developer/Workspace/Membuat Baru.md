## Membuat Workspace

1. Buka folder tempat Workspace akan ditempatkan di [[Docs/Antarmuka/Pengenalan#Area Manajemen Folder]]
2. Klik kanan ➜ [[^field/add|Add]] ➜ [[^field|Developer]] ➜ [[^field/workspace|Workspace]]
3. Isi [[^field|Name]] dan [[^field|Description]]
4. Klik [[^button|Create]]

Folder tempat Workspace ditempatkan akan menjadi root dari Workspace tersebut.

>**success** Workspace berhasil dibuat
>Nilai awal hak akses Workspace baru mengikuti Workspace yang sedang aktif saat Workspace dibuat. Jika dibuat dari Origin, seluruh hak aksesnya [[^value/boolean/allow]]. Workspace baru belum dapat dipakai oleh anggota sampai dipetakan ke [[Docs/Modul Developer/Group/Apa itu Group|Group]], jadi periksa dan sesuaikan hak aksesnya di [[#Mengatur Hak Akses]] sebelum memetakannya.


## Menyegarkan

Klik [[^button/refresh|Refresh]] untuk memuat ulang tampilan.

## Menghapus Workspace

1. Buka folder yang berisi Workspace di [[Docs/Antarmuka/Pengenalan#Area Manajemen Folder]]
2. Klik kanan Workspace
3. Pilih [[^button/delete|Delete]]
4. Konfirmasi dengan [[^button|Delete]]

>**warning** Harap pastikan
>Sebelum menghapus pastikan setiap [[Docs/Modul Developer/Group/Apa itu Group|Group]] tetap memiliki Workspace selain daripada yang akan dihapus. Sehingga pengalaman pengguna tetap lancar menggunakan Phoenix.

>**warning** Pengaturan hak akses ikut hilang
>Seluruh pengaturan hak akses pada Workspace ini hilang dan pemetaannya pada [[Docs/Modul Developer/Group/Apa itu Group|Group]] terputus. Komponen dan data di dalam folder tidak ikut terhapus.

>**note** Workspace root terakhir tidak dapat dihapus
>Phoenix mencegah hilangnya akses ke root utama. Workspace di posisi root tidak dapat dihapus jika setelah dihapus tidak ada lagi Workspace di posisi root yang terhubung ke [[Docs/Modul Developer/Group/Apa itu Group|Group]]. Karena itu, Origin tidak dapat dihapus selama belum ada Workspace root lain yang terhubung ke Group.

---
    status: release
    title: "Menghapus Workspace"
    description: Penjelasan cara menghapus komponen Workspace
    pageDecoration:
      tree:
        priority: 6
---
# Menghapus Workspace

1. Buka folder yang berisi Workspace di [[Docs/Dasar/Antarmuka#Area Manajemen Folder]]
2. Klik kanan Workspace
3. Pilih [[^button/delete|Delete]]
4. Konfirmasi dengan [[^button|Delete]]

>**warning** Harap pastikan
>Sebelum menghapus pastikan setiap [[Docs/Modul Developer/Group/Apa itu Group|Group]] tetap memiliki Workspace selain daripada yang akan dihapus. Sehingga pengalaman pengguna tetap lancar menggunakan Phoenix.

>**warning** Pengaturan hak akses ikut hilang
>Seluruh pengaturan hak akses pada Workspace ini hilang dan pemetaannya pada [[Docs/Modul Developer/Group/Apa itu Group|Group]] terputus. Komponen dan data di dalam folder tidak ikut terhapus.

>**note** Workspace root terakhir tidak dapat dihapus
>Phoenix mencegah hilangnya akses ke root utama. Workspace di posisi root tidak dapat dihapus jika setelah dihapus tidak ada lagi Workspace di posisi root yang terhubung ke [[Docs/Modul Developer/Group/Apa itu Group|Group]]. Karena itu, Origin tidak dapat dihapus selama belum ada Workspace root lain yang terhubung ke Group.

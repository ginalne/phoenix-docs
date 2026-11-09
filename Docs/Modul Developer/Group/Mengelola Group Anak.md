---
    status: release
    title: "Mengelola Group Anak"
    description: Penjelasan cara mengelola group anak dalam komponen Group
    pageDecoration:
      tree:
        priority: 0
---
# Mengelola Group Anak

Group anak ditampilkan di bawah Group induknya. Setiap Group anak memiliki daftar Workspace dan User sendiri. Bila belum ada anggota, kolom [[^field|User]] menampilkan [[^field|(User Is Empty)]].

Menu pada Group anak terdiri dari:

| Menu | Fungsi |
| ---- | ------ |
| [[^field/edit|Edit]] | Mengubah atribut Group anak. |
| [[^field/add|Add Children]] | Menambahkan Group sebagai anak dari Group anak yang dipilih. |
| [[^field|Place to Directory]] | Menempatkan Group anak sebagai komponen di Area Manajemen Folder. |
| [[^field/delete|Delete]] | Menghapus Group anak. |

## Menambahkan Group Anak

1. Klik kanan Group anak ➜ [[^field/add|Add Children]]
2. Isi [[^field|Name]], [[^field|Description]], dan [[^field|Parent]]
3. Klik [[^button|Create]]

Anda juga dapat menambahkan Group melalui tombol [[^button/add|Add Group]] yang berada di bagian akhir setiap Group saat daftarnya terbuka (lihat [[#Dari Halaman Kerja Group]]).

## Mengubah Group Anak

1. Klik kanan Group anak ➜ [[^field/edit|Edit]]
2. Ubah atribut Group anak
3. Klik [[^button|Update]]

## Menempatkan Group ke Direktori

Group anak juga merupakan komponen. Gunakan [[^field|Place to Directory]] untuk menampilkannya di Area Manajemen Folder.

1. Klik kanan Group anak ➜ [[^field|Place to Directory]]
2. Untuk konfirmasi penempatan pada dialog yang muncul dengan Klik [[^button|Place]]

>**note** Posisi penempatan
> Group yang dipilih akan ditempatkan di posisi *root* folder dari [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]] yang sedang aktif. Selengkapnya tentang folder lihat [[Docs/Dasar/Apa itu Folder]].

## Menghapus Group Anak

1. Pindahkan seluruh User di Group anak tersebut dan di Group anaknya ke Group lain. Lihat [[#Memindahkan User]]
2. Klik kanan Group anak ➜ [[^field/delete|Delete]]
3. Konfirmasi dengan klik [[^button|Delete]]

>**warning** Dampak penghapusan Group anak
> Daftar Workspace pada Group anak tersebut hilang, dan Group anak di bawahnya ikut terhapus. Group anak yang dihapus tidak boleh masih memiliki User, jadi pindahkan semua User terlebih dahulu.

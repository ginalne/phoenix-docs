---
    status: release
    title: "Menghapus Data Variable"
    description: Penjelasan cara menghapus Data Variable
    pageDecoration:
      tree:
        priority: 1
---
# Menghapus Data Variable

1. [[#Membuka Halaman Kerja Variable|Buka]] Halaman Kerja Variable
2. Pada kolom [[^field|Action]], klik [[^button/delete|Delete]] pada baris yang ingin dihapus
3. Konfirmasi dengan [[^button|Delete]]

>**warning** Pastikan Variable tidak lagi dipakai
>Variable yang dihapus tidak lagi tersedia sebagai pilihan pada field bertipe Variable. Flow atau komponen lain yang masih memanggil Name tersebut tidak akan menemukan nilainya, dan laporan error tampil di [[Docs/Modul Logic/Flow/Flow Activity]]. Periksa dulu komponen yang memakai Variable sebelum menghapusnya.

>**danger** Pertimbangkan Resiko
>Variable Data yang sudah dihapus tidak dapat dikembalikan.

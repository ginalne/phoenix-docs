---
    status: release
    title: "Membuat Group"
    description: Penjelasan cara membuat komponen Group baru.
    pageDecoration:
      tree:
        priority: 2
---
# Membuat Group

Group dapat dibuat dari dua tempat, dan hasilnya sedikit berbeda.

## Dari Area Manajemen Folder

Cara ini menambahkan Group sebagai komponen di dalam folder.

![[Docs/Modul Developer/Group/add-group.png]]
1. Buka folder tempat Group akan ditempatkan di [[Docs/Antarmuka#Area Manajemen Folder]]
2. Klik kanan ➜ [[^field/add|Add]] ➜ [[^field|Developer]] ➜ [[^field/group|Group]]
3. Isi [[^field|Name]] dan [[^field|Description]]
4. Pilih Group induk pada [[^field|Parent]]
5. Klik [[^button|Create]]

>**note** Parent wajib diisi
> Pada form dari Area Manajemen Folder, [[^field|Parent]] wajib diisi dengan Group induk dari Group yang dibuat. Pro baru sudah memiliki Group [[^field/group|Administrator]] yang dapat dipilih sebagai Group induk.

>**success** Group berhasil dibuat
> Group yang baru dibuat belum memiliki Workspace dan User. Tambahkan Workspace di [[#Mengelola Workspace dalam Group]] dan pindahkan User di [[#Mengelola User dalam Group]].

## Dari Halaman Kerja Group

Cara ini menambahkan Group langsung di halaman kerja Group. Form-nya sama dengan form di Area Manajemen Folder, hanya tidak memiliki bagian direktori karena Group tidak langsung ditempatkan sebagai komponen di folder.

1. Buka halaman kerja Group
2. Klik panah di sebelah kiri judul Group yang akan diberi anak agar daftarnya terbuka
3. Klik [[^button/add|Add Group]] pada bagian akhir Group, setelah daftar Group anaknya
4. Isi [[^field|Name]] dan [[^field|Description]]
5. Klik [[^button|Create]]

[[^field|Parent]] terisi otomatis dengan Group tempat [[^button/add|Add Group]] diklik.

>**note** Group belum muncul di Area Manajemen Folder
> Group yang dibuat dari halaman kerja Group tidak otomatis menjadi komponen di folder. Gunakan [[#Menempatkan Group ke Direktori|Place to Directory]] bila Anda ingin menempatkannya.

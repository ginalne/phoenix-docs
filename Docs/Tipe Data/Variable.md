---
    status: release
    title: "Variable"
    description: 
    pageDecoration:
      tree:
        priority: 0
---
# Variable
Variable adalah tipe data yang hanya bisa dibuat, diperbarui atau dihapus melalui komponan [[Docs/Modul Data/Variable/Apa itu Variable|Variable]].

## Atribut

| Nama | Penjelasan |
| --- | --- |
| [[^field\|Name]] | Nama Variable. Tidak boleh sama dengan variable lain. | 
| [[^field\|Type]] | Tipe data dari nilai yang disimpan, misalnya [[Docs/Tipe Data/String\|String]]. | 
| [[^field\|Value]] | Nilai yang disimpan, menyesuaikan Type. | 
| [[^field\|Description]] | Keterangan tentang kegunaan Variable. | 
| [[^field\|Created At]] | Waktu baris dibuat. | 
| [[^field\|Updated At]] | Waktu baris terakhir diperbarui. | 

## Cara Kerja Variable

Karena keunikannya, komponen lain dapat memilih Variable lewat field bertipe Variable sebagai pilihan, sehingga dapat dianalogikan sebagai konstanta dalam ekosistem.

Selain sebagai konstanta, Variable dapat berfungsi sebagai *alias*: komponen dapat memanggil nilai lewat [[^field|Name]], sehingga isi [[^field|Value]] tidak harus diketahui oleh tim, tetapi tetap dapat dipakai untuk kebutuhan integrasi.

## Format
>**note** Tipe data ini tidak memiliki format khusus.


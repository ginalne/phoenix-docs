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
| [[^field\|Name]] | Nama Variable, nilainya tidak boleh sama dengan variable lain. | 
| [[^field\|Type]] | Menyimpan jenis tipe data, misalnya [[Docs/Tipe Data/String|String]]. | 
| [[^field\|Value]] | Nilai yang disimpan, menyesuaikan atribut [[^field|Type]]. | 
| [[^field\|Description]] | Keterangan tentang kegunaan Variable. | 
| [[^field\|Created At]] | Waktu baris dibuat. | 
| [[^field\|Updated At]] | Waktu baris terakhir diperbarui. | 

## Cara Kerja Variable

Karena keunikannya, komponen lain dapat memilih Variable lewat field bertipe Variable sebagai pilihan (tanpa menentukan [[^field|Header]], sehingga dapat dianalogikan sebagai konstanta dalam ekosistem.

Selain sebagai konstanta, Variable juga dapat berfungsi sebagai *alias*. Komponen dalam [[Docs/Modul Logic/Pengenalan|Modul Logic]] dapat mengakses isi [[^field|Value]] hanya lewat nilai [[^field|Name]], sehingga isi [[^field|Value]] tidak harus diketahui oleh tim, tetapi tetap dapat dipakai untuk kebutuhan otomasi.

Dengan Variable, nilai konfigurasi dan nilai sensitif di [[Inisialisasi/Apa itu Pro?|Pro]] tersimpan di satu sumber yang terhubung ke semua komponen, tanpa mengorbankan keamanan maupun konsistensi data.

## Format
>**note** Tipe data ini tidak memiliki format khusus.


---
    status: release
    title: ""
    description: 
    pageDecoration: 
      tree: 
        priority: 0 
---

## Space Weather

Weather adalah data yang tampil sebagai *world effect*, yaitu efek yang berlaku pada seluruh ruang 3D dan bukan pada satu benda tertentu.

| Atribut | Tipe Data | Penjelasan |
| --- | --- | --- |
| [[^field|Priority]] | [[Docs/Tipe Data/Number]] | Urutan prioritas Weather. Bila ada banyak Weather dengan [[^field|Type]] yang sama, yang dipakai adalah Priority terkecil. |
| [[^field|Name]] | [[Docs/Tipe Data/String]] | Nama Weather. |
| [[^field|Description]] | [[Docs/Tipe Data/String]] | Keterangan Weather. |
| [[^field|Type]] | - | Jenis efek yang menentukan properti uniknya. Pilihannya [[^value/radio|Earth Sky]] dan [[^value/radio|Sea]]. |
| [[^field|Status]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] berarti Weather ikut dipertimbangkan, [[^value/boolean/false]] berarti diabaikan. |

[[^field|Type]] Weather yang dapat digunakan saat ini:

| [[^field|Type]] | Properti | Tipe Data | Penjelasan |
| --- | --- | --- | --- |
| [[^value/radio|Earth Sky]] | [[^field|Time]] | [[Docs/Tipe Data/DateTime]] atau [[Docs/Tipe Data/DateTimeZone]] | Waktu yang digunakan untuk langit. |
| [[^value/radio|Sea]] | [[^field|Level]] | [[Docs/Tipe Data/Number]] | Level laut. |
| [[^value/radio|Sea]] | [[^field|Wave Rate]] | [[Docs/Tipe Data/Number]] | Laju gelombang laut. |

Setiap properti pada [[^field|Type]] memiliki *toggle* pada field nilainya untuk memilih pengisian dengan nilai langsung (statis) atau [[Docs/Tipe Data/Query|Query]] dengan kaidah [[Docs/Tipe Data/Query#Single Output|Single Output]]. Karena Query Single Output menghasilkan satu nilai hasil kalkulasi, nilai tersebut mengikuti data sumbernya.

>**note** Aturan Priority dan Status
> Hanya satu Weather untuk setiap [[^field|Type]] yang berlaku, yaitu Weather dengan [[^field|Status]] [[^value/boolean/true]] dan [[^field|Priority]] terkecil. Weather dengan [[^field|Status]] [[^value/boolean/false]] tidak ikut dihitung.

### Menambahkan Weather

1. Buka halaman kerja Space
2. Klik kanan pada [[#Antarmuka Space|Outliner]] ➜ [[^field/add|Add Weather]]
3. Isi [[^field|Name]], [[^field|Description]], [[^field|Priority]], [[^field|Type]], dan [[^field|Status]]
4. Isi properti sesuai [[^field|Type]] dengan nilai langsung atau [[Docs/Tipe Data/Query|Query]], dipilih lewat *toggle* pada field nilainya

### Mengubah Weather

1. Fokuskan Weather yang akan diubah
2. Ubah nilai pada [[#Panel Properti]]

Perubahan [[^field|Priority]] atau [[^field|Status]] dapat mengubah Weather mana yang berlaku untuk [[^field|Type]] yang sama.

### Menghapus Weather

1. Klik kanan Weather pada [[#Antarmuka Space|Outliner]]
2. Klik [[^button/delete|Delete]]

>**warning** Efek Weather hilang dari ruang
> Efek Weather tidak lagi tampil di ruang 3D. Jika masih ada Weather lain dengan [[^field|Type]] yang sama dan [[^field|Status]] [[^value/boolean/true]], Weather dengan [[^field|Priority]] terkecil berikutnya yang akan dipakai.

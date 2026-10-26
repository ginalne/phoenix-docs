---
    status: release
    title: "Space Weather"
    description: 
    pageDecoration:
      tree:
        priority: 4
---
# Space Weather

Weather adalah data yang tampil sebagai *world effect*, yaitu efek yang berlaku pada seluruh ruang 3D dan bukan pada satu benda tertentu.

## Atribut

| Atribut | Tipe Data | Penjelasan |
| --- | --- | --- |
| [[^field|Priority]] | [[Docs/Tipe Data/Number]] | Urutan prioritas Weather. Bila ada banyak Weather dengan [[^field|Type]] yang sama, yang dipakai adalah Priority terkecil. |
| [[^field|Name]] | [[Docs/Tipe Data/String]] | Nama Weather. |
| [[^field|Description]] | [[Docs/Tipe Data/String]] | Keterangan Weather. |
| [[^field|Type]] | - | Jenis efek yang menentukan properti uniknya. Pilihannya [[^value/radio|Earth Sky]] dan [[^value/radio|Sea]]. |
| [[^field|Status]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] berarti Weather ikut dipertimbangkan, [[^value/boolean/false]] berarti diabaikan. |

## Type Weather

Berikut adalah [[^field|Type]] Weather yang dapat digunakan saat ini:

### Earth Sky

Earth Sky adalah type dalam Weather yang berfungsi untuk mengatur tampilan langit dalam Space.

Properti yang dapat digunakan adalah sebagai berikut:

| Properti | Tipe Data | Penjelasan |
| --- | --- | --- |
| [[^field|Time]] | [[Docs/Tipe Data/DateTime]] atau [[Docs/Tipe Data/DateTimeZone]] | Waktu yang digunakan untuk langit. |

### Sea

Sea adalah type dalam Weather yang berfungsi untuk mengatur tampilan laut dalam Space.

| Properti | Tipe Data | Penjelasan |
| --- | --- | --- |
| [[^field|Level]] | [[Docs/Tipe Data/Number]] | Level laut. |
| [[^field|Wave Rate]] | [[Docs/Tipe Data/Number]] | Laju gelombang laut. |

Setiap properti pada [[^field|Type]] memiliki *toggle* pada field nilainya untuk memilih pengisian dengan nilai langsung (statis) atau [[Docs/Tipe Data/Query|Query]] dengan kaidah [[Docs/Tipe Data/Query#Single Output|Single Output]]. Karena Query Single Output menghasilkan satu nilai hasil kalkulasi, nilai tersebut mengikuti data sumbernya.

>**note** Aturan Priority dan Status
> Hanya satu Weather untuk setiap [[^field|Type]] yang berlaku, yaitu Weather dengan [[^field|Status]] [[^value/boolean/true]] dan [[^field|Priority]] terkecil. Weather dengan [[^field|Status]] [[^value/boolean/false]] tidak ikut dihitung.

## Mengelola Weather

Berikut adalah aksi yang bisa dilakukan untuk mengelola data Weather :

1. [[Docs/Modul Interface/Space/Environment/Menambahkan]] Data Weather
2. [[Docs/Modul Interface/Space/Environment/Mengubah]] Atribut atau Konfigurasi Weather
3. [[Docs/Modul Interface/Space/Environment/Menghapus]] Weather dari Space

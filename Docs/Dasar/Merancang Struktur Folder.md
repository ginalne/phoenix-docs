---
    status: release
    title: "Merancang Struktur Folder"
    description: Tips cara merancang struktur Folder
    pageDecoration:
      tree:
        priority: 0
---
# Merancang Struktur Folder

Tidak ada satu struktur yang paling benar, tetapi pola berikut membantu Anda memulai. Karena komponen yang dipindahkan tetap terhubung dengan komponen lain, Anda dapat menata ulang struktur kapan saja tanpa memutus relasi.

## Langkah Merancang

1. Petakan area kerja yang memakai [[Docs/Dasar/Apa itu Pro|Pro]], misalnya tim atau fungsi bisnis.
2. Pilih satu pola penataan utama dari tabel di bawah.
3. Tentukan batas akses: folder dan komponen mana yang harus tertutup bagi Workspace tertentu, lalu atur [[Docs/Modul Developer/Workspace/Component Access|Component Access]] sesuai struktur.
4. Tetapkan penamaan yang konsisten untuk folder dan komponen.
5. Tinjau struktur secara berkala dan tata ulang saat satu folder terasa terlalu ramai.

## Pola Penataan

| Pola | Cocok bila | Kerangka | Hal yang perlu diperhatikan |
| --- | --- | --- | --- |
| Per area bisnis | Beberapa fungsi, seperti penjualan dan keuangan, memakai Pro yang sama. | Satu folder per area berisi Table, Enum, Table View, Form, dan Flow area tersebut. | Komponen yang dipakai banyak area lebih mudah dikelola di folder bersama. |
| Per tim | Setiap tim memiliki Workspace sendiri. | Satu folder per tim. | [[^field|Visible]] mudah diatur per folder, tetapi komponen yang harus tertutup perlu Visible [[^value/boolean/disallow]] tersendiri. |
| Per sistem | Beberapa sistem terpisah dibangun dalam satu Pro. | Satu folder per sistem. | Nama komponen yang jelas membantu saat memilih komponen pada *field* dan [[Docs/Tipe Data/Query|Query]]. |
| Per jenis komponen | Pro kecil dengan sedikit area. | Folder terpisah untuk data, tampilan, dan otomasi. | Saat Pro bertumbuh, komponen satu area tersebar di beberapa folder, sehingga pertimbangkan pola per area. |
| Arsip | Ada komponen yang tidak dipakai lagi tetapi datanya masih disimpan. | Folder arsip. | Sembunyikan dari Workspace yang tidak membutuhkannya lewat Visible. |

## Kerangka yang Direkomendasikan

Nama dalam tanda `< >` hanya pengganti. Sesuaikan dengan area dan komponen di [[Docs/Dasar/Apa itu Pro|Pro]] Anda.

```
Pro
├── Bersama
│   ├── Variables (Variable)
│   └── <Kategori> (Enum)
├── <Area atau Tim A>
│   ├── <Data> (Table)
│   ├── <Tampilan> (Table View)
│   ├── <Formulir> (Form)
│   └── <Alur> (Flow)
└── <Area atau Tim B>
    └── ...
```

Folder bersama menampung komponen yang dipakai banyak area, seperti [[Docs/Modul Data/Variable/Apa itu Variable|Variable]] dan [[Docs/Modul Data/Enum/Apa itu Enum|Enum]] untuk kategori. Komponen Variable otomatis berada di *root* saat Pro dimulai dan boleh dipindahkan ke folder bersama.

>**note** Mulai dari yang sederhana
> Struktur dua tingkat, yaitu folder area bisnis lalu komponen di dalamnya, sudah cukup untuk sebagian besar [[Docs/Dasar/Apa itu Pro|Pro]]. Tambahkan tingkat berikutnya hanya ketika satu folder terasa terlalu ramai.

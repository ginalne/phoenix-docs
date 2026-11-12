---
    status: release
    title: "Format Import dan Export"
    description: 
status: draft
title: Format Import dan Export
description: Format file JSON untuk mengekspor dan mengimpor Node pada Tree.
pageDecoration:
  tree:
    priority: 2
---
# Format Import dan Export

[[Docs/Modul Data/Tree/Node/Mengekspor|Mengekspor]] menghasilkan file JSON dan [[Docs/Modul Data/Tree/Node/Mengimpor|Mengimpor]] membaca file dengan format yang sama. Strukturnya bersarang: setiap [[Docs/Tipe Data/Node|Node]] memuat daftar Node anaknya di dalam [[^field|children]].

## Atribut Node

Setiap Node dalam file memiliki tiga atribut. Kolom Tipe merujuk pada tipe JSON, bukan tipe data Phoenix.

| Atribut | Tipe | Keterangan |
| ------- | ---- | ---------- |
| [[^field|order]] | Number | Urutan Node di antara saudara kandung. Angka minimal [[^value/number|0]]. |
| [[^field|name]] | String | Nama Node. |
| [[^field|children]] | Array | Daftar Node anak langsung. Wajib ada, dan berisi array kosong bila Node tidak memiliki anak. Setiap anggota memiliki atribut yang sama dengan Node induknya. |

File tidak memiliki atribut induk. Hubungan induk dan anak ditentukan oleh posisi Node di dalam [[^field|children]].

## Contoh Isi File

Contoh berikut adalah hasil ekspor Node [[^value/node|Elektronik]] yang memiliki anak [[^value/node|Komputer]] dan [[^value/node|Ponsel]]. [[^value/node|Komputer]] memiliki anak [[^value/node|Laptop]].

```json
{
  "order": 0,
  "name": "Elektronik",
  "children": [
    {
      "order": 0,
      "name": "Komputer",
      "children": [
        {
          "order": 0,
          "name": "Laptop",
          "children": []
        }
      ]
    },
    {
      "order": 1,
      "name": "Ponsel",
      "children": []
    }
  ]
}
```

Node tanpa anak tetap memiliki [[^field|children]] berupa array kosong.

## Aturan Isi File

- [[^field|name]] harus unik di antara saudara kandung, yaitu Node dalam [[^field|children]] yang sama.
- [[^field|order]] berupa angka minimal [[^value/number|0]] dan harus unik di antara saudara kandung.
- [[^field|children]] wajib ada pada setiap Node, termasuk Node tanpa anak.
- Atribut selain [[^field|order]], [[^field|name]], dan [[^field|children]] diabaikan saat impor.
- Node terluar pada file berbentuk satu objek, yaitu Node yang Anda ekspor. Saat diimpor, Node ini menjadi anak dari Node yang Anda pilih, sehingga [[^field|name]] dan [[^field|order]]-nya juga harus unik terhadap saudara kandung di bawah Node tersebut.

>**warning** Name dan Order yang bentrok
> Bila satu saja Node dalam file bentrok dengan aturan di atas atau dengan Node yang sudah ada di bawah induk yang sama, impor ditolak seluruhnya dan tidak ada Node yang ditambahkan.

Anda dapat menyunting atau menyusun file secara manual sebelum diimpor selama formatnya mengikuti halaman ini.

## Lihat Juga

- [[Docs/Modul Data/Tree/Node/Mengekspor|Mengekspor Node]]
- [[Docs/Modul Data/Tree/Node/Mengimpor|Mengimpor Node]]
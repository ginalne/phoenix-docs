---
    status: release
    title: Mengimpor Node
    description: Cara mengimpor Node dari file ke Tree sebagai anak dari Node terpilih.
    pageDecoration:
      tree:
        priority: 3
---
# Mengimpor Node


Mengimpor menambahkan banyak [[Docs/Tipe Data/Node|Node]] sekaligus dari file, misalnya file hasil [[Docs/Modul Data/Tree/Node/Mengekspor|Mengekspor]]. Node dari file ditambahkan sebagai anak dari Node yang Anda pilih.

## Langkah Mengimpor

1. Buka halaman kerja [[Docs/Modul Data/Tree/Apa itu Tree|Tree]].
2. Klik kanan [[Docs/Tipe Data/Node|Node]] yang akan menjadi induk ➜ [[^field/import|Import]].
3. Pilih file yang akan diimpor.
4. Klik [[^button|Import]].

>**success** Node berhasil diimpor
> Node dari file tampil sebagai anak dari Node yang Anda pilih, lengkap dengan keturunannya.

Pastikan isi file sesuai [[Docs/Modul Data/Tree/Node/Format Import dan Export|Format Import dan Export]]. Node hasil impor selalu menjadi Node baru, bukan hasil *clone*.

>**warning** Name dan Order yang bentrok
> [[^field|Name]] dan [[^field|Order]] harus unik di antara saudara kandung. Bila Node dalam file bentrok dengan Node yang sudah ada di bawah induk yang sama, impor ditolak seluruhnya dan tidak ada Node yang ditambahkan.

>**note** Hak akses dan Event
> Mengimpor memerlukan [[Docs/Modul Developer/Workspace/Data Access#Data yang Diatur pada Setiap Komponen|Data Access]] Add pada Tree: Node bernilai [[^value/boolean/allow]]. Setiap Node yang diimpor memicu event [[^value/string|create]] pada [[Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event|Tree Node Event Block]].

## Lihat Juga

- [[Docs/Modul Data/Tree/Node/Mengekspor|Mengekspor Node]]
- [[Docs/Modul Data/Tree/Node/Menambahkan|Menambahkan Node]]
- [[Docs/Modul Data/Tree/Node/Format Import dan Export|Format Import dan Export]]
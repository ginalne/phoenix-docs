---
    status: draft
    title: Mengubah Nama Node
    description: Cara mengubah Name Node pada Tree tanpa memindahkan posisinya.
    pageDecoration:
      icon: x
      tree:
        priority: 8
---
# Mengubah Nama Node

Mengubah nama berarti mengganti [[^field|Name]] pada [[Docs/Tipe Data/Node|Node]] yang sudah ada tanpa memindahkan posisinya di [[Docs/Modul Data/Tree/Apa itu Tree|Tree]]. Node Origin juga dapat diganti namanya.

## Langkah Mengubah Nama

1. Buka halaman kerja [[Docs/Modul Data/Tree/Apa itu Tree|Tree]].
2. Klik kanan [[Docs/Tipe Data/Node|Node]] yang akan diganti namanya ➜ [[^field/edit|Edit]].
3. Ubah [[^field|Name]].
4. Klik [[^button|Update]].

Anda dapat klik [[^button/x|Cancel]] untuk membatalkan perubahan Node.

>**success** Nama Node berhasil diubah
> [[^field|Name]] baru langsung tampil pada Node di area kerja.

Contoh: mengganti [[^field|Name]] [[^value/node|Aksesori]] menjadi [[^value/string|Aksesori Komputer]].

<!--
  * [DONE] Langkah mengikuti asumsi di halaman Menambahkan (Edit pada Node ➜ ubah Name ➜ Update). Mohon konfirmasi label field dan tombol.
  * [DONE] Nama contoh (Aksesori) adalah nama generik. Sesuaikan dengan gambar Anda.
-->

## Aturan Name

[[^field|Name]] harus unik di antara saudara kandung, yaitu [[Docs/Tipe Data/Node|Node]] lain dengan parent yang sama. Node pada parent yang berbeda boleh memiliki Name yang sama. Menyimpan Node tanpa mengubah [[^field|Name]] bukan konflik.

Bila [[^field|Name]] bentrok dengan saudara kandung, perubahan tidak tersimpan dan sistem menampilkan pesan kesalahan.

>**warning** Node hasil clone di Tree merger
> Bila Node berada di Tree non-merger dan sudah di-*clone* oleh Tree merger, perubahan [[^field|Name]] ikut diterapkan pada Node hasil *clone* yang mengikuti perubahan Node asal. Perubahan tidak ikut diterapkan bila [[^field|Name]] pada [[Docs/Modul Data/Tree/Konfigurasi External Read Only|External Read Only]] di Tree merger bernilai [[^value/radio|Active]].

>**note** Hak akses dan Event
> Mengubah [[^field|Name]] memerlukan [[Docs/Modul Developer/Workspace/Data Access#Data yang Diatur pada Setiap Komponen|Data Access]] Update pada Tree: Node bernilai [[^value/boolean/allow]]. Perubahan memicu event [[^value/string|update]] pada [[Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event|Tree Node Event Block]], dan `Old` hanya berisi [[^field|Name]] sebelumnya.

<!--
  * [TODO] Pesan kesalahan saat Name bentrok belum diketahui. Mohon konfirmasi teks pesannya.
    Jawaban: Asumsikan pesan errornya agar sistem mengikuti.
-->

## Lihat Juga

- [[Docs/Modul Data/Tree/Node/Mengubah Urutan|Mengubah Urutan Node]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Setter|Node Setter Block]] untuk mengubah Name lewat Flow.
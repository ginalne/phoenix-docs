---
    status: release
    title: Mengatur Tampilan Node
    description: Cara melipat, memperluas, menyembunyikan Node, dan mengganti arah tampilan Tree.
    pageDecoration:
      tree:
        priority: 5
---
# Mengatur Tampilan Node

Tree dengan banyak [[Docs/Tipe Data/Node|Node]] mudah dibaca bila Anda hanya menampilkan bagian yang dibutuhkan. Pengaturan pada halaman ini hanya mengubah tampilan, bukan data Node.

![[Docs/Modul Data/Tree/Node/tree-context.png|Menu konteks Node]]

## Melipat dan Memperluas Node

Klik kanan [[Docs/Tipe Data/Node|Node]] ➜ [[^field|Expand/Collapse]] untuk membuka atau menutup anak langsung dari Node tersebut. Bila Node tidak memiliki anak, menu berubah menjadi [[^field|No children...]].

Untuk mengatur banyak Node sekaligus, klik kanan Node ➜ [[^field|View]], lalu pilih salah satu menu berikut.

| Menu | Fungsi |
| ---- | ------ |
| [[^field|Collapse Below Level]] | Melipat keturunan pada level Node ini, berlaku untuk semua Node. Level Node ini menjadi tingkat terakhir yang tampil karena semua Node di bawahnya masuk dalam lipatan. |
| [[^field|Expand Children Only]] | Memperluas hanya satu tingkat keturunan di bawah Node ini. |
| [[^field|Collapse Descendant]] | Melipat seluruh keturunan Node ini secara rekursif. |
| [[^field|Expand Descendant]] | Memperluas seluruh keturunan Node ini secara rekursif. |

## Menyembunyikan Node yang Dilipat

Node yang dilipat dapat tetap terlihat sebagai penanda atau disembunyikan sepenuhnya.

| Menu | Fungsi |
| ---- | ------ |
| [[^field|Hide Collapsed]] | Menyembunyikan anak yang sedang dilipat. |
| [[^field|Show Collapsed]] | Memunculkan kembali anak yang sedang dilipat. |
| [[^field|Collapse and Hide]] | Melipat sekaligus menyembunyikan anak. |

Semua menu di atas berada pada submenu [[^field|View]].

>**note** Status lipat tidak disimpan
> Status lipat dan sembunyi hanya berlaku selama halaman kerja terbuka. Klik [[^button/refresh|Refresh]] akan mengembalikan seluruh Node ke tampilan semula.

## Mengganti Arah Tampilan

Arah tampilan ditentukan oleh [[^field|Horizontal Mode]].

| Nilai | Tampilan |
| ----- | -------- |
| [[^value/radio|Active]] | Horizontal, Origin di kiri dan Node anak mengarah ke kanan. |
| [[^value/radio|Non-Active]] | Vertikal, Origin di atas dan Node anak mengarah ke bawah. |

Untuk mengganti arah saat itu juga, klik informasi mode di bagian bawah area kerja.

>**note** Perubahan arah bersifat sementara
> Penggantian mode di halaman kerja hanya berlaku sementara. Untuk mengubah nilai awalnya, gunakan [[^field|Default Configuration]] pada [[Docs/Modul Data/Tree/Apa itu Tree#Mengubah Tree|Edit Tree]].

## Mencari Node

Ketik [[^field|Name]] Node pada kolom [[^field|Search Tree Data...]] di bilah navigasi. Pencarian hanya mencocokkan [[^field|Name]] Node. Node yang cocok disorot dan tampilan berpindah ke Node tersebut.

Cara menggeser tampilan, *zoom*, dan memusatkan koordinat dijelaskan di [[Docs/Modul Data/Tree/Apa itu Tree#Interaksi Antarmuka Tree|Interaksi Antarmuka Tree]].

## Lihat Juga

- [[Docs/Modul Data/Tree/Node/Melihat Detail|Melihat Detail Node]]
- [[Docs/Modul Data/Tree/Apa itu Tree#Antarmuka Tree|Antarmuka Tree]]
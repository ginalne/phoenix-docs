---
    status: release
    title: "Konfigurasi Bawaan"
    description: Penjelasan Default Configuration di komponen Tree
    pageDecoration:
      tree:
        priority: 0.1
---
# Konfigurasi Bawaan

Tree memiliki halaman kerja seperti blueprint yang memiliki beberapa Mode dan konfigurasi menu konteks (ketika melakukan klik kanan pada Node).

## Mengatur Konfigurasi
Anda dapat mengaturnya ketika saat membuatnya pertama kali atau ketika klik [[^button/edit|Edit]].

![[Docs/Modul Data/Tree/create-new-tree.png|Modal Tambah Tree Baru]]
Kolom dapat diubah dengan implikasi seperti berikut:

| Kolom | Status/Nilai | Penjelasan |
| -------- | --------- | ---------------- |
| [[^field|Horizontal Mode]] | [[^value/boolean/Active]] | Tampilan struktur [[Docs/Tipe Data/Node]] akan menjalar dari kiri ke kanan (horizontal). |
| [[^field|Horizontal Mode]] | [[^value/boolean/Non-Active]] | Tampilan struktur [[Docs/Tipe Data/Node]] akan menjalar dari atas ke bawah (vertikal). |
| [[^field|Context]] | [[^field|Menu]] | Klik kanan pada [[Docs/Tipe Data/Node]] akan membuka konteks menu |
| [[^field|Context]] | [[^field|Detail]] | Klik kanan pada [[Docs/Tipe Data/Node]] akan membuka informasi detail |
| [[^field|Context]] | [[^field|Edit]] | Klik kanan pada [[Docs/Tipe Data/Node]] akan membuka penyuntingan |


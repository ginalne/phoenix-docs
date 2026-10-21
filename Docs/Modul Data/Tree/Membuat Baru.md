---
    status: release
    title: "Membuat Tree Baru"
    description: Penjelasan cara membuat komponen Tree baru.
    pageDecoration:
      tree:
        priority: 2
    tags:
      draft
---
# Membuat Tree Baru

![[Docs/Modul Data/Tree/add-tree.png]]
1. Buka folder tempat Tree akan ditempatkan di [[Docs/Antarmuka#Area Manajemen Folder]]
2. Klik kanan ➜ [[^field/add|Add]] ➜ [[^field|Data]] ➜ [[^field/tree|Tree]]
3. Isi [[^field|Name]], [[^field|Description]], dan atribut lainnya sesuai kebutuhan (lihat [[#Atribut Tree]])
4. Klik [[^button|Create]]

>**success** Tree berhasil dibuat
> Tree yang baru dibuat otomatis memiliki satu [[Docs/Tipe Data/Node]] bernama [[^field|Origin]]. Tambahkan Node lain di [[#Mengelola Node]].




## Atribut Tree

| Isian | Fungsi |
| --- | --- |
| [[^field|Directory]] | Folder tempat Tree berada. Terisi otomatis sesuai folder yang Anda klik kanan. Jika dikosongkan, Tree berada di root. |
| [[^field|Name]] | Nama Tree. |
| [[^field|Description]] | Keterangan singkat tentang Tree. |
| [[Docs/Modul Data/Tree/Konfigurasi Merger Mode]] | Jika aktif, Tree dapat menambahkan (*clone*) Node dari Tree lain. Tidak dapat diubah setelah Tree dibuat. |
| [[Docs/Modul Data/Tree/Konfigurasi External Read Only|External Read Only]] | Tiga pilihan, yaitu [[^field|Order]], [[^field|Name]], dan [[^field|Children]]. |
| [[Docs/Modul Data/Tree/Konfigurasi Bawaan]] | Pengaturan tampilan awal, yaitu [[^field|Horizontal Mode]] dan [[^field|Context]]. |

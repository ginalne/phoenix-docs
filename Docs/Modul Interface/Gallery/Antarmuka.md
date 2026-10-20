---
    status: release
    title: "Antarmuka Gallery"
    description: Penjelasan antarmuka di halaman kerja komponen Gallery
    pageDecoration:
      tree:
        priority: -1
    tags:
      draft
---
# Antarmuka Gallery

![[Docs/Modul Interface/Gallery/interface-gallery2.png]]
Halaman kerja Gallery terdiri dari bilah navigasi di bagian atas dan area kartu di bagian bawah. Setiap Row pada Table tampil sebagai satu kartu di area kartu.

### Bilah navigasi Gallery terdiri dari:

| Tombol | Fungsi |
| ------ | ------ |
| [[^button/edit|Edit]] | Mengubah [[^field|Name]], [[^field|Description]], dan [[^field|Filter]] Gallery. |
| [[^button/setting|Column]] | Membuka modal [[^field|Setup Gallery Template]] untuk mengatur template kartu. Selengkapnya lihat [[#Mengatur Template Kartu]]. |
| [[^button/refresh|Refresh]] | Memuat ulang tampilan. |
| [[^field|Search Gallery Data...]] | Mencari data pada Gallery. |

### Interaksi Antarmuka Gallery

| Fungsi | Aksi |
| ------ | ---- |
| Mengubah Row | Klik kiri kartu, Row tampil dalam bentuk Form Table untuk diperbarui. Berlaku jika Data Access Table di Workspace mengizinkan. |
| Melihat detail Row | Klik kanan kartu ➜ [[^field|Detail]] |
| Menambah Row | Klik kanan kartu ➜ [[^field|Add Row]] |
| Menghapus Row | Klik kanan kartu ➜ [[^field|Delete]] |

>**warning** Menghapus Row dari Gallery
> Row yang dihapus lewat Gallery terhapus dari Table sumber dan tidak dapat dikembalikan.

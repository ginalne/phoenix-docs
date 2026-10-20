---
    status: release
    title: "Antarmuka Kanban"
    description: Penjelasan antarmuka di halaman kerja komponen Kanban
    pageDecoration:
      tree:
        priority: 0
    tags:
      draft
---
# Antarmuka Kanban

![[Docs/Modul Interface/Kanban/interface-kanban.png]]

Halaman kerja Kanban terdiri dari bilah navigasi di bagian atas dan area kolom di bagian bawah. Setiap kolom mewakili satu [[Docs/Tipe Data/EnumData]], dan kartu berada di dalam kolom sesuai nilai [[Docs/Tipe Data/EnumData]] pada [[Docs/Tipe Data/Row]]-nya.

### Bilah navigasi Kanban terdiri dari:

| Elemen | Fungsi |
| ------ | ------ |
| Judul Kanban | Menampilkan ikon Kanban dan Header Name. |
| [[^button/edit|Edit]] | Mengubah atribut Kanban. Selengkapnya lihat [[Docs/Modul Interface/Kanban/Mengubah Kanban]]. |
| [[^button/refresh|Refresh]] | Memuat ulang tampilan Kanban. |
| [[^field|Search Kanban Data...]] | Mencari data pada Kanban. |

### Header Kolom Kanban

Header setiap kolom berisi tiga bagian dari kiri ke kanan:

| Bagian | Fungsi |
| ------ | ------ |
| Jumlah item | Angka yang menunjukkan banyaknya kartu pada kolom tersebut. |
| [[^field|Name]] - [[^field|Description]] | Nama [[Docs/Tipe Data/EnumData]] yang menjadi kolom. |
| Tombol [[^button/setting]] | Membuka modal pengaturan template untuk [[Docs/Tipe Data/EnumData]] tersebut. Lihat [[#Mengatur Template Kartu]]. |

### Interaksi Antarmuka Kanban

| Fungsi | Aksi |
| ------ | ---- |
| Memindahkan kartu antar kolom | Seret kartu ke kolom tujuan (*drag and drop*), atau klik kanan kartu ➜ [[^field|Move To]] lalu pilih kolom tujuan. |
| Melihat atau mengubah isi kartu | Klik kartu untuk membuka [[Docs/Modul Data/Table/Form Table|Form Table]], yaitu [[Docs/Tipe Data/Row]] dalam bentuk form, lalu ubah isinya secara langsung. |
| Membuka menu konteks kartu | Klik kanan pada kartu. Lihat [[#Menu Konteks Kartu]]. |
| Menggulir daftar kartu | Arahkan kursor pada satu kolom, lalu gulir ke bawah atau ke atas. Ini berlaku jika tinggi tampilan kartu lebih besar dari layar Anda. |
| Menggulir kolom | Arahkan kursor pada halaman kerja, lalu gulir ke kiri atau ke kanan. Ini berlaku jika jumlah kolom cukup banyak sehingga lebar tampilan lebih besar dari layar Anda. |

### Menu Konteks Kartu

| Menu | Fungsi |
| ---- | ------ |
| [[^field|Detail]] | Membuka [[Docs/Modul Data/Table/Form Table|Form Table]], sama seperti klik kiri pada kartu. |
| [[^field/add|Add Row]] | Menambahkan [[Docs/Tipe Data/Row]] baru. Nilai [[Docs/Tipe Data/EnumData]] langsung terisi sesuai kolom tempat kursor berada. |
| [[^field/delete|Delete Row]] | Menghapus [[Docs/Tipe Data/Row]] dari [[Docs/Modul Data/Table/Apa itu Table|Table]] sumber. |
| [[^field|Move To]] | Menampilkan daftar kolom yang tersedia, kecuali kolom yang sedang menampung kartu tersebut. Pilih kolom untuk memindahkan kartu. |

>**warning** Delete Row menghapus data sumber
>[[^field/delete|Delete Row]] menghapus [[Docs/Tipe Data/Row]] dari [[Docs/Modul Data/Table/Apa itu Table|Table]] sumber, bukan hanya kartu pada Kanban. [[Docs/Tipe Data/Row]] yang dihapus tidak dapat dikembalikan.

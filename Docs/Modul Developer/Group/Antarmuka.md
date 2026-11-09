---
    status: release
    title: "Antarmuka Group"
    description: Penjelasan antarmuka di halaman kerja komponen Group
    pageDecoration:
      tree:
        priority: 0
---
# Antarmuka Group

![[Docs/Modul Developer/Group/interface-group.png]]
Contoh gambar di atas merupakan halaman kerja Group dengan satu Group induk dan dua Group anak.

Halaman kerja Group terdiri dari bilah navigasi di bagian atas dan daftar Group di bagian bawah. Setiap Group menampilkan judul, deskripsi, kolom [[^field|Workspace]] di sebelah kiri, dan kolom [[^field|User]] di sebelah kanan. Group anak tersusun di bawah Group induknya.

### Bilah navigasi Group terdiri dari:

| Tombol | Fungsi |
| ------ | ------ |
| Judul Group | Menampilkan ikon Group dan nama Group. |
| [[^button/edit|Edit]] | Mengubah [[^field|Name]] dan [[^field|Description]] Group. Lihat [[#Mengubah Group]]. |
| [[^button/refresh|Refresh]] | Memuat ulang tampilan halaman kerja. |
| [[^field|Search Group Data...]] | Mencari Group berdasarkan nama dan deskripsi. |

### Interaksi Antarmuka Group

| Fungsi | Aksi |
| ------ | ---- |
| Membuka atau menutup daftar Group anak | Klik panah di sebelah kiri judul Group. |
| Menambahkan Group | Buka Group, lalu klik [[^button/add|Add Group]] pada bagian akhir Group, setelah daftar anaknya. |
| Menambahkan Workspace | Klik [[^field|Search workspace to add...]], cari Workspace, lalu pilih. |
| Menghapus Workspace dari Group | Klik Workspace pada daftar, lalu konfirmasi [[^button|Remove]]. |
| Memindahkan User | *Drag and drop* User dari Group lama ke Group tujuan. |
| Membuka menu Group anak | Klik kanan pada Group anak. |


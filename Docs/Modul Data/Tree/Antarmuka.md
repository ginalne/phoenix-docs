---
    status: release
    title: "Antarmuka Tree"
    description: Penjelasan antarmuka di halaman kerja komponen Tree
    pageDecoration:
      tree:
        priority: 0
---
# Antarmuka Tree

![[Docs/Modul Data/Tree/antarmuka-tree.png]]
Halaman kerja Tree terdiri dari bilah navigasi di bagian atas dan area kerja di bagian bawah yang menampilkan pohon beserta Node-nya. Di sudut bawah area kerja terdapat informasi [[^field|context _]], [[^field|mode _]], koordinat [[^field|x _ y _]], dan [[^field|scale _]].

## Bilah navigasi Tree terdiri dari:

| Elemen | Fungsi |
| --- | --- |
| Judul Tree | Menampilkan ikon Tree dan nama Tree. |
| [[^button/edit|Edit]] | Mengubah atribut Tree. Lihat [[#Mengubah Tree]]. |
| [[^button/publish|Publish]] | Mengatur publikasi Tree. Lihat [[Docs/Modul Data/Tree/Mempublikasi]]. |
| [[^button/event|Event]] | Menghubungkan Tree dengan Event. Lihat [[Docs/Modul Data/Tree/Event]]. |
| [[^button/refresh|Refresh]] | Memuat ulang tampilan. Lihat [[#Menyegarkan Tree]]. |
| [[^field|Search Tree Data...]] | Mencari Node berdasarkan [[^field|Name]]. Pencarian tidak mencakup atribut Node yang lain. |

## Informasi Area Kerja

| Informasi | Penjelasan |
| --- | --- |
| [[^field|context _]] | Nilai [[#Default Configuration|Context]] yang sedang berlaku. Klik untuk menggantinya. |
| [[^field|mode _]] | Arah tampilan pohon, yaitu Horizontal atau Vertical. Klik untuk menggantinya. Lihat [[#Default Configuration|Mode]]. |
| [[^field|x _ y _]] | Koordinat posisi tampilan pada area kerja. |
| [[^field|scale _]] | Skala tampilan pada area kerja. |

## Interaksi Antarmuka Tree

| Fungsi | Aksi |
| --- | --- |
| Menggeser tampilan (*pan*) | Tekan dan tahan pada bagian yang kosong dalam halaman kerja, lalu gerakkan kursor. Lepas untuk selesai. |
| Mengubah skala tampilan (*zoom*) | Gulir pada bagian halaman kerja. |
| Memusatkan tampilan | Klik informasi koordinat [[^field|x _ y _]]. Tampilan kembali ke tengah. |
| Mengembalikan skala | Klik informasi [[^field|scale _]]. Tampilan kembali berskala 1. |
| Mengganti mode | Klik informasi [[^field|mode _]]. Perubahan bersifat sementara. |
| Mengganti context | Klik informasi [[^field|context _]]. Perubahan bersifat sementara. |
| Membuka menu konteks Node | Klik kanan pada Node. Hasilnya mengikuti nilai [[^field|context _]]. |

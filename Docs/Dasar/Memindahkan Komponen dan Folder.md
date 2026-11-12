---
    status: release
    title: "Memindahkan Folder dan Komponen"
    description: Penjelasan cara memindahkan folder atau komponen ke folder lain, atau hanya mengubah urutannya di folder yang sama
    pageDecoration:
      tree:
        priority: 0
---
# Memindahkan Folder dan Komponen

Anda dapat memindahkan folder atau komponen ke folder lain, atau hanya mengubah urutannya di folder yang sama, dengan *drag and drop*. Pemindahan dapat dilakukan di Area Manajemen Folder atau di halaman kerja [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]].

### Memindahkan di Area Manajemen Folder

1. Nyalakan toggle [[^field/move]] di bagian atas [[Docs/Antarmuka#Area Manajemen Folder]]
2. Tekan dan tahan folder atau komponen yang ingin dipindahkan
3. Seret ke folder tujuan atau ke posisi baru, lalu lepaskan

Untuk memindahkan ke folder *root*, seret komponen atau folder ke barisan di level *root* (menyisipkan di antara komponen atau folder yang sudah ada), atau ke bagian kosong, biasanya di bagian bawah Area Manajemen Folder.

### Memindahkan di Halaman Kerja Workspace

1. Buka halaman kerja Workspace
2. Tekan dan tahan folder atau komponen yang ingin dipindahkan di kolom kiri
3. Seret ke folder tujuan atau ke posisi baru, lalu lepaskan

| Tujuan | Hak akses yang dibutuhkan |
| --- | --- |
| Memindahkan ke folder lain | [[^field|Delete]] pada folder atau komponen yang dipindahkan dan [[^field|Add]] pada folder tujuan. |
| Mengubah urutan di folder yang sama | Tidak memerlukan [[^field|Add]] maupun [[^field|Delete]]. |

>**note** Pemindahan mengubah struktur Pro
> Struktur folder Pro dan Workspace saling berkesinambungan. Memindahkan folder atau komponen mengubah struktur folder [[Docs/Dasar/Apa itu Pro|Pro]], bukan hanya tampilan halaman kerja Workspace.

>**success** Relasi komponen tetap terhubung
> Setelah dipindahkan, komponen tetap terhubung dengan komponen lain, misalnya lewat [[Docs/Tipe Data/Query|Query]] atau Flow Block. Anda dapat menata ulang struktur kapan saja tanpa memutus relasi.

>**warning** Izin memindahkan sama dengan izin menghapus
> Anggota yang boleh memindahkan komponen ke folder lain juga boleh menghapus komponen itu karena pemindahan memerlukan [[^field|Delete]]. Berikan hak akses ini dengan hati-hati. Selengkapnya lihat [[Docs/Modul Developer/Workspace/Component Access#Memindahkan Folder atau Komponen|Memindahkan Folder atau Komponen]].

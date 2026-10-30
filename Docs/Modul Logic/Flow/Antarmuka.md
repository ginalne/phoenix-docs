---
    status: release
    title: "Antarmuka Flow"
    description: Penjelasan antarmuka di halaman kerja komponen Flow
    pageDecoration:
      tree:
        priority: -1
---
## Antarmuka Flow

![[Docs/Modul Logic/Flow/blueprint-flow.png]]
Antarmuka Flow menampilkan seluruh struktur ruang kerja, yaitu bilah navigasi di bagian atas, dan kolom blueprint di bagian bawah.

Bilah navigasi Flow terdiri dari:

| Tombol | Fungsi |
| --- | --- |
| [[^field/flow|Judul Flow]] | Ikon Flow dalam Phoenix serta [[^field|Header Name]] Flow. |
| [[^button/edit|Edit]] | Mengubah atribut Flow seperti [[^field|Directory]], [[^field|Name]] dan [[^field|Description]]. |
| [[^button/refresh|Refresh]] | Memuat ulang halaman kerja. |
| [[^button/submission|Submission]] | Tombol yang berfungsi untuk membuka bilik submission. |
| [[^field|Search]] | Kolom pencarian untuk mencari Flow Block. |

>**note** Perbedaan Icon
>Dalam mode desktop, tombol [[^button/submission|Submission]] sedikit berbeda. Tombol terlihat dengan susunan informasi submission, yaitu total activity, done, waiting, dan failure.

### Informasi Area Kerja

| Informasi | Penjelasan |
| --- | --- |
| [[^field|x _ y _]] | Koordinat posisi tampilan pada area kerja. |
| [[^field|scale _]] | Skala tampilan pada area kerja. |

## Interaksi Antarmuka Flow

Anda bisa berinteraksi pada blueprint Flow untuk memudahkan proses pengembangan logika dan alur komposit dengan aksi seperti berikut:

| Fungsi | Aksi |
| --- | --- |
| Menggeser tampilan (_pan_) | Tekan dan tahan pada bagian yang kosong dalam blueprint lalu gerakkan kursor. Lepas untuk selesai. |
| Mengubah skala tampilan (_zoom_) | gulir pada bagian blueprint. |
| Mengembalikan tampilan ke tengah | Klik pada informasi koordinat [[^field|x _ y _]]. |
| Mengembalikan skala tampilan | Klik pada informasi skala [[^field|scale _]]. |
| Membuka menu konteks | Klik kanan pada bagian yang kosong dalam blueprint. |
---
    status: release
    title: "Antarmuka Gallery"
    description: Penjelasan antarmuka di halaman kerja komponen Gallery
    pageDecoration:
      tree:
        priority: 0
---
# Antarmuka Timeline
 ![[Docs/Modul Interface/Timeline/interface-timeline.png]]
Halaman kerja Timeline terdiri dari bilah navigasi di bagian atas dan area kerja di bagian bawah.

## Bilah navigasi Timeline terdiri dari:

| Tombol | Fungsi |
| ------ | ------ |
| Judul Timeline | Menampilkan ikon Timeline dan nama Timeline. |
| [[^button/edit|Edit]] | Mengubah atribut Timeline. Lihat [[#Mengubah Timeline]]. |
| [[^button/refresh|Refresh]] | Memuat ulang tampilan. |
| [[^field|Search Timeline Data...]] | Mencari kata kunci pada Timeline Data dan Timeline Event. |

## Area Kerja Timeline

| Area | Penjelasan |
| ---- | ---------- |
| [[^field|Item List]] | Kolom kiri berisi nama Timeline Event dan nama Row pada Timeline Data. |
| Header waktu | Baris di atas area kerja, misalnya [[^field|MonthYear]], [[^field|Week]], [[^field|Date]], [[^field|DateDayweek]], dan [[^field|Hour]]. Barisnya menyesuaikan tingkat [[#Menu Konteks Timeline|Zoom]]. |
| [[^field|now]] | Garis dan penanda yang menunjukkan waktu saat ini. |
| Grup Event | Judul `Event (n)` memuat Timeline Event, dengan n jumlah Timeline Event. Ikon jam di samping nama menandakan item tersebut Timeline Event. Jika kosong, tampil [[^field|Event is empty]] dan tombol [[^button/add|Add Event]]. |
| Grup Timeline Data | Judul berisi nama Timeline Data, jumlah Row hasil Query, dan tombol [[^button/q]] untuk mengatur Query. Jika belum ada, tampil [[^field|Data is empty]] dan tombol [[^button/add|Add Data]]. |
| Blok | Timeline Event dan Row tampil sebagai blok di sumbu waktu, dengan nama di sampingnya. |
| Panah pada judul grup | Klik panah di judul grup Event atau Timeline Data untuk melipat atau membuka grup tersebut. |

## Menu Konteks Timeline

Klik kanan pada area berikut untuk membuka menu konteks.

| Area | Menu |
| ---- | ---- |
| Blok Timeline Event | [[^field|Edit]], [[^field|Add Data]], [[^field|Add Event]], [[^field|Zoom]], [[^field|Delete Event]] |
| Judul Timeline Data | [[^field|Rename Data]], [[^field|Add Data]], [[^field|Add Event]], [[^field|Zoom]], [[^field|Delete Data]] |
| Row pada Timeline Data | [[^field|Edit]], [[^field|View]], [[^field|Add Row]], [[^field|Add Data]], [[^field|Add Event]], [[^field|Zoom]], [[^field|Delete Row]] |
| Bagian yang kosong | [[^field|Add Data]], [[^field|Add Event]], [[^field|Zoom]] |

[[^field|View]] membuka popup preview Row, sedangkan [[^field|Edit]] membuka form edit Row. Dampak penghapusan dijelaskan di [[#Menghapus Timeline Event]], [[#Menghapus Timeline Data]], dan [[#Menghapus Row]].

Menu [[^field|Zoom]] memiliki cabang berikut.

| Cabang | Fungsi |
| ------ | ------ |
| [[^field|Zoom In]], [[^field|Zoom Out]] | Memperbesar atau memperkecil skala rentang waktu. |
| [[^field|Quarter - Month]], [[^field|Month - Week]], [[^field|Week - Date]], [[^field|Week - Dayweek]], [[^field|Date - Hour]], [[^field|Time - 30 Minute]], [[^field|Time - 10 Minute]], [[^field|Time - 1 Minute]], [[^field|Minute - Second]] | Memilih tingkat satuan waktu pada header, dari kuartal sampai detik. |

## Preview dan Edit Row

![[Docs/Modul Interface/Timeline/preview-example.png]]
Klik kiri pada Row, atau pilih [[^field|View]] pada menu konteks Row, untuk membuka popup preview. Popup berisi bagian berikut.

| Bagian | Penjelasan |
| ------ | ---------- |
| Judul | Nama Row. |
| [[^field|Start]] dan [[^field|End]] | Waktu mulai dan waktu selesai Row. |
| [[^field|Duration]] | Lama waktu dari Start sampai End. |
| [[^field|Status]] | Kondisi Row terhadap waktu saat ini, yaitu [[^field|Upcoming]], [[^field|On Going]], atau [[^field|Finished]]. |
| [[^field|Calendar]] | Rentang tanggal dari Start sampai End. |
| [[^field|Relative]] | Keterangan waktu Row relatif terhadap waktu saat ini, misalnya sudah berakhir 180 hari lalu. |
| [[^field|Progress]] | Kemajuan Row. Hanya tampil ketika [[^field|Status]] bernilai [[^field|On Going]]. |
| [[^field|change time]] | Kontrol untuk menggeser waktu. Tombol panah di bawah label [[^field|start]] menggeser waktu Start, tombol panah di bawah label [[^field|end]] menggeser waktu End, dan pilihan satuan di tengah (misalnya 1 Day) menentukan besar pergeseran. Kontrol dibuka atau ditutup dengan ikon di kiri bawah popup, dan panahnya mengarah ke atas ketika kontrol terbuka. |
| [[^button/edit|Edit Row]] | Membuka modal form untuk mengubah Row. |

Hak akses untuk mengubah Row mengikuti [[#Hak Akses Timeline Data]].

## Interaksi Antarmuka Timeline

| Fungsi | Aksi |
| ------ | ---- |
| Berpindah posisi waktu | Gulir horizontal pada area kerja. Pada tampilan mobile, geser area kerja ke kiri atau kanan. |
| Menggulir Event dan Data | Geser area kerja ke atas atau bawah (vertikal). Ini berlaku jika jumlah Timeline Event dan Timeline Data melebihi tinggi layar. |
| Mengubah skala rentang waktu | Putar *wheel* mouse untuk mengubah *scale factor* rentang waktu Timeline. |
| Memindahkan waktu blok | Klik dan geser blok Timeline Data atau Timeline Event. Bagian kiri blok memindahkan waktu Start, bagian kanan memindahkan waktu selesai (End), dan bagian tengah memindahkan keduanya secara bersamaan. Hak aksesnya mengikuti [[#Hak Akses Timeline Event]] dan [[#Hak Akses Timeline Data]]. |
| Select dengan geser | Klik dan geser pada celah di antara header waktu dan blok data. |
| Select satu blok | Tekan Ctrl + Shift lalu klik blok untuk memilih rentang waktu blok tersebut secara otomatis. |
| Select pada area kerja | Tekan Shift lalu klik dan geser pada area kerja. |
| Memakai hasil Select | Menu konteks dan Zoom tetap sama. Saat [[^field|Add Row]], isian Start dan End terisi otomatis sesuai rentang Select. |
| Membuka preview Row | Klik kiri pada Row. Lihat [[#Preview dan Edit Row]]. |
| Membuka menu konteks | Klik kanan pada Timeline Event, Timeline Data, Row, atau bagian yang kosong. Lihat [[#Menu Konteks Timeline]]. |

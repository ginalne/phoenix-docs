---
    status: release
    title: Mengubah Urutan Node
    description: Cara mengubah Order Node untuk menentukan posisinya di antara saudara kandung.
    pageDecoration:
      tree:
        priority: 8
---
# Mengubah Urutan Node

[[^field|Order]] menentukan posisi [[Docs/Tipe Data/Node|Node]] di antara saudara kandungnya, yaitu Node lain dengan parent yang sama. Node dengan [[^field|Order]] lebih kecil tampil lebih dulu. Anda dapat mengubahnya lewat [[^field/edit|Edit]] atau dengan *drag and drop*.

## Langkah Mengubah Urutan

1. Buka halaman kerja [[Docs/Modul Data/Tree/Apa itu Tree|Tree]].
2. Klik kanan [[Docs/Tipe Data/Node|Node]] yang akan diubah urutannya ➜ [[^field/edit|Edit]].
3. Ubah [[^field|Order]].
4. Klik [[^button|Update]].

Anda dapat klik [[^button/x|Cancel]] untuk membatalkan perubahan Node.

>**success** Urutan Node berhasil diubah
> Node tampil pada posisi baru di antara saudara kandungnya.

## Mengubah Urutan dengan Drag and Drop

1. Buka halaman kerja [[Docs/Modul Data/Tree/Apa itu Tree|Tree]].
2. Tekan dan tahan ikon `::` di sebelah kiri [[Docs/Tipe Data/Node|Node]] yang akan dipindahkan.
3. Seret Node ke posisi yang diinginkan di antara saudara kandungnya.
4. Lepaskan Node.

*Drag and drop* lebih singkat untuk menukar posisi dua Node karena Anda tidak perlu menghitung [[^field|Order]] perantara seperti pada [[#Menukar Posisi Dua Node dengan Edit]].

## Aturan Order

- [[^field|Order]] berupa angka minimal [[^value/number|0]]. Nilai negatif tidak diterima.
- [[^field|Order]] harus unik di antara saudara kandung. Karena itu, lewat [[^field/edit|Edit]], dua Node tidak dapat langsung bertukar posisi.
- Mengubah [[^field|Order]] pada Origin tidak berpengaruh karena Origin selalu berada di titik pertama.
- Mengubah [[^field|Order]] lewat [[^field/edit|Edit]] tidak memindahkan Node ke parent lain.

## Menukar Posisi Dua Node dengan Edit

Gunakan [[^field|Order]] yang masih kosong sebagai perantara. Contoh: [[^value/node|Komputer]] ([[^field|Order]] [[^value/number|0]]) dan [[^value/node|Ponsel]] ([[^field|Order]] [[^value/number|1]]) berada di bawah [[^value/node|Elektronik]], dan Anda ingin [[^value/node|Ponsel]] berada di depan.

| Langkah | Node | Order Sebelum | Order Sesudah |
| ------- | ---- | ------------- | ------------- |
| 1 | [[^value/node|Komputer]] | [[^value/number|0]] | [[^value/number|2]] |
| 2 | [[^value/node|Ponsel]] | [[^value/number|1]] | [[^value/number|0]] |
| 3 | [[^value/node|Komputer]] | [[^value/number|2]] | [[^value/number|1]] |

Ulangi langkah [[#Langkah Mengubah Urutan|mengubah urutan]] untuk setiap baris tabel.

>**note** Hak akses dan Event
> Mengubah [[^field|Order]], lewat [[^field/edit|Edit]] maupun *drag and drop*, memerlukan [[Docs/Modul Developer/Workspace/Data Access#Data yang Diatur pada Setiap Komponen|Data Access]] Update pada Tree: Node bernilai [[^value/boolean/allow]]. Perubahan memicu event [[^value/string|update]] pada [[Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event|Tree Node Event Block]], dan `Old` hanya berisi [[^field|Order]] sebelumnya.

## Lihat Juga

- [[Docs/Modul Data/Tree/Node/Mengubah Nama|Mengubah Nama Node]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Setter|Node Setter Block]] untuk mengubah Order lewat Flow.
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Assign Node|Assign Node Block]] untuk memindahkan Node ke parent lain lewat Flow.
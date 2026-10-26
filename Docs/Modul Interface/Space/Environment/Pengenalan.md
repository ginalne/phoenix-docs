---
    status: release
    title: "Space Environment"
    description: 
    pageDecoration:
      tree:
        priority: 4
---
# Space Environment

Environment adalah data yang tampil sebagai objek 3D statis tanpa logika. Anda cukup meng-*upload* file 3D untuk menjadikannya benda di dalam ruang, misalnya bangunan, lantai, atau perabot.

## Atribut

| Atribut | Tipe Data | Penjelasan |
| --- | --- | --- |
| [[^field|Name]] | [[Docs/Tipe Data/String]] | Nama Environment. |
| [[^field|Description]] | [[Docs/Tipe Data/String]] | Keterangan Environment. |
| [[^field|Position]] | [[Docs/Format Data/Complex/3D Vector|3D Vector]] | Posisi Environment di ruang 3D. |
| [[^field|Scale]] | [[Docs/Format Data/Complex/Volume Unit|Volume Unit]] | Ukuran (skala) Environment pada sumbu x, y, dan z. |
| [[^field|Rotation]] | [[Docs/Format Data/Complex/Euler Angle|Euler Angle]] | Rotasi Environment. |
| [[^field|Model]] | File 3D | File 3D yang di-*upload* sebagai wujud Environment. |

## Mengelola Environment

Berikut adalah aksi yang bisa dilakukan untuk mengelola data Environment :

1. [[Docs/Modul Interface/Space/Environment/Menambahkan]] Data Environment
2. [[Docs/Modul Interface/Space/Environment/Mengubah]] Atribut atau Konfigurasi Environment
3. [[Docs/Modul Interface/Space/Environment/Menghapus]] Environment dari Space
   

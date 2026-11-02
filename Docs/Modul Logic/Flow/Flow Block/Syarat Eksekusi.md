---
    status: release
    title: "Syarat Flow Block Dieksekusi"
    description: 
    pageDecoration:
      tree:
        priority: 5
---
# Syarat Flow Block Dieksekusi

Sebuah block diproses bila kedua syarat berikut terpenuhi:

1. Setiap [[#Input]] yang terhubung ke [[#Output]] block lain sudah memiliki data, artinya block sebelumnya sudah tereksekusi.
2. [[#Trigger]] memiliki data setidaknya satu, artinya block sebelumnya sudah tereksekusi. Jika Trigger tidak terhubung, syarat ini selalu terpenuhi.

> **note** Block tanpa Trigger dan Input terhubung
> Flow Block non-Event yang tidak memiliki koneksi pada [[#Trigger]] maupun [[#Input]] tidak menerima apa pun dari block lain, sehingga tidak akan aktif dalam [[Docs/Modul Logic/Flow/Flow Activity|Activity]].

## Data pada Input selama Activity

Setelah block tereksekusi, data pada [[#Input]] dipertahankan selama [[Docs/Modul Logic/Flow/Flow Activity|Activity]] tersebut berjalan. Bila aliran Flow kembali ke block yang sama (rekursif), data terakhir yang akan digunakan.
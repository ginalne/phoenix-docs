---
    status: release
    title: "Menghapus Table View"
    description: Penjelasan cara menghapus komponen Table View
    pageDecoration:
      tree:
        priority: 1
    tags:
      draft
---
# Menghapus Tree

1. Buka folder yang berisi Tree
2. Klik kanan Tree, pilih [[^button/delete|Delete]]
3. Konfirmasi dengan [[^button|Delete]]

>**warning** Dampak penghapusan Tree
> Seluruh [[Docs/Tipe Data/Node]] di dalam Tree ikut terhapus. Relasi dari komponen lain yang memakai Tree ini akan terputus, misalnya [[Docs/Tipe Data/Column]] pada Table yang memakai [[Docs/Tipe Data/Node]] dari Tree ini dan [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] seperti [[Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event|Tree Node Event]]. Jika Tree ini menjadi sumber *clone* bagi Tree dengan [[Docs/Modul Data/Tree/Konfigurasi Merger Mode|Merger Mode]], Node hasil *clone* di Tree tersebut dapat terdampak.

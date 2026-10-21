---
    status: release
    title: "FAQ : Tree"
    description: Pertanyaan yang sering diajukan pada komponen Tree
    pageDecoration:
      tree:
        priority: -10
    tags:
      draft
---
# FAQ : Tree

Berikut adalah pertanyaan yang sering diajukan pada komponen Tree:

> **faq**
> **Apa bedanya Tree biasa dengan Tree yang memakai [[Docs/Modul Data/Tree/Konfigurasi Merger Mode|Merger Mode]]?**
> Tree biasa hanya menyimpan Node miliknya sendiri. Tree dengan [[Docs/Modul Data/Tree/Konfigurasi Merger Mode|Merger Mode]] dapat menambahkan (*clone*) Node dari Tree lain, sedangkan Tree biasa tidak dapat melakukannya.
> **Apakah [[Docs/Modul Data/Tree/Konfigurasi Merger Mode|Merger Mode]] dapat diubah setelah Tree dibuat?**
> Tidak. Pilihan ini ditentukan saat Tree dibuat. Lihat [[#Mengubah Tree]].
> **Apakah perubahan pada Node asal otomatis muncul di Node *clone*?**
> Hal ini bergantung pada [[#External Read Only]]. Jika [[^field|Order]], [[^field|Name]], atau [[^field|Children]] berstatus [[^value/boolean/Non-Active]], atribut tersebut ikut berubah ketika Node di Tree lain diperbarui.
> **Apa yang dicari oleh [[^field|Search Tree Data...]]?**
> Kolom ini hanya mencari berdasarkan [[^field|Name]] Node.
> **Apakah perubahan [[^field|mode _]] dan [[^field|context _]] di halaman kerja bersifat permanen?**
> Tidak. Perubahan di halaman kerja hanya sementara. Untuk mengubah nilai awalnya, gunakan [[^button/edit|Edit]] (lihat [[#Default Configuration]]).
> **Mengapa menu [[^field|Collapse]] berubah menjadi [[^field|No children...]]?**
> Node tersebut tidak memiliki anak, sehingga tidak ada yang dapat dilipat atau diperluas. Lihat [[#Menu Konteks Node]].
> **Apa yang ada di Tree yang baru dibuat?**
> Tree baru otomatis memiliki satu Node bernama [[^field|Origin]]. Anda dapat menambahkan Node lain di [[#Mengelola Node]].

---
  pageDecoration:
    tree:
      priority: -5
  tags:
    meta
    prompt
---
2026-10-09 08-00

![[prompt/2026-10-09_08-20-50.png]]![[prompt/2026-10-09_08-27-54.png]]
![[prompt/2026-10-09_08-21-13.png]]
/phoenix-docs-knowledge /phoenix-docs-silverbullet 

Tolong saya membuat halaman "Apa itu Tree?".

base knowledge:
1. Tree merupakan salah satu komponen dalam modul [[Docs/Modul Data/Pengenalan|Data]] di Phoenix. 
2. Komponen yang dapat menyimpan data secara hierarki atau berbentuk pohon. Sifat data ini dapat digunakan untuk menyimpan data relasional yang bercabang. Tree dapat memiliki banyak [[Docs/Tipe Data/Node]]. Salah satu atribut penting dalam Tree adalah [[Docs/Modul Data/Tree/Konfigurasi Merger Mode]].
3. Gambar membuat tree dilampirkan.
4. Narasi ini harus dimaknai, bukan fakta pasti: Tree memiliki [[Docs/Tipe Data/Node]] dengan atribut Order dan Name yang muncul ketika pengguna memilih atau menambahkannya, namun dalam proses pengelolaan data, sifat Tree ini cukup sulit untuk difiltrasi ataupun digabungkan. Sehingga diperlukan satu Tree bersifat merger yang bisa memanggil Node dari beberapa tree yang sudah ada (non merger), dan menambahkannya (clone) ke dalam dengan/tanpa mengikuti perubahan mendatang. Tree yang bukan bersifat merger tidak bisa menambahkan Node dari Tree lain.
5. External Read Only : Order, Name, Children. Jika non-active,  Attribute Node dalam tree ini akan berubah jika clone/origin node dari Tree lain di update.
6. Atribut context adalah status ketika pengguna membuka contextmenu dari Node. Pilihannya: Menu, Edit, Detail. Mengelola node perlu dijelaskan di halaman lain.
7. Context menu dari node dapat dilihat digambar. Jika Node tidak mempunya anak, maka pilihan "Expand"/"Collapse" dan "Expand Children Only" akan menjadi “No children...”. Penjelasan menu:
    * Expand atau Collapse : memperluas atau melipat keturunan selanjutnya.
    * Collapse Below Level : melipat keturunan di level ini (semua node).
    * Expand Children Only : memperluas hanya satu keturunan dibawahnya.
    * Collapse Descendant : membuat semua keturunan melipat (recursive collapse).
    * Expand Descendant: membuat semua keturunan terbuka (recursive expand).
    * Hide Collapsed: menyembunyikan anak yang dilipat.
    *  Show Collapsed: memunculkan anak yang dilipat.
    * Collapse and hide: melipat dan menyembunyikan anak yang dilipat.
8. Search Tree Data hanya mencari Name dalam node.
9. Mode ada horizontal dan vertical, menentukan apakah pohon akan berakar dari kiri kekanan, atau dari atas ke bawah.
10. Koordinat ketika di klik akan mengubah tampilan ke tengah.
11. Scale ketika di klik akan mengubah tampilan menjadi berskala 1.
12. Publish, Event perlu dijelaskan dihalaman lain.
13. Ketika Tree pertama kali dibuat akan ada 1 Node yang otomatis ada bernama Origin.
---
    status: release
    title: "Mengatur Tampilan Node"
    description: Penjelasan cara mengatur tampilan node di komponen Tree
    pageDecoration: 
      tree: 
        priority: 0 
---
# Mengatur Tampilan Node

![[Docs/Modul Data/Tree/node-menu.png]]
Submenu [[^field|View]]:

| Menu | Fungsi |
| --- | --- |
| [[^field/collapse|Collapse Below Level]] | Melipat keturunan pada level Node ini (semua Node). |
| [[^field/expand|Expand Children Only]] | Memperluas hanya satu keturunan di bawahnya. |
| [[^field/collapse|Collapse Descendant]] | Melipat semua keturunan secara *recursive*. |
| [[^field/expand|Expand Descendant]] | Membuka semua keturunan secara *recursive*. |
| [[^field|Hide Collapsed]] | Menyembunyikan anak yang dilipat. |
| [[^field|Show Collapsed]] | Memunculkan anak yang dilipat. |
| [[^field/collapse|Collapse and Hide]] | Melipat sekaligus menyembunyikan anak yang dilipat. |

>**note** Node tanpa anak
> Jika Node tidak memiliki anak, pilihan [[^field|Expand]] atau [[^field|Collapse]] dan [[^field|Expand Children Only]] berubah menjadi [[^field|No children...]].

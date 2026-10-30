---
    status: release
    title: "Menghapus Timeline"
    description: Penjelasan cara menghapus komponen Timeline
    pageDecoration:
      tree:
        priority: 1
---
# Menghapus Timeline

1. Buka folder yang berisi Timeline di [[Docs/Antarmuka#Area Manajemen Folder]]
2. Klik kanan Timeline ➜ [[^button/delete|Delete]]
3. Konfirmasi dengan klik [[^button|Delete]]

>**warning** Timeline Event dan Timeline Data ikut terhapus
> Seluruh Timeline Event dan Timeline Data beserta konfigurasi [[Docs/Tipe Data/Query]] di dalam Timeline hilang. [[Docs/Modul Logic/Flow/Flow Block/Event/Pulser]] yang sebelumnya dipicu Timeline Event tidak lagi menerima pemicu dari Timeline ini. [[Docs/Modul Data/Table/Apa itu Table|Table]] yang menjadi sumber [[Docs/Tipe Data/Query]] dan [[Docs/Tipe Data/Row]] di dalamnya tidak ikut terhapus.
---
    status: draft
    date: "2026-10-02"
    pageDecoration:
      icon: x
      tree:
        priority: 4
---
# Konfigurasi Merger Mode
Tree memiliki [[Docs/Tipe Data/Node]] dengan atribut Order dan Name yang muncul ketika pengguna memilih atau menambahkannya, namun dalam proses pengelolaan data, sifat Tree ini cukup sulit untuk difiltrasi ataupun digabungkan.

## Mengatur Konfigurasi
Anda dapat mengaturnya hanya ketika saat membuatnya pertama kali.

![[Docs/Modul Data/Tree/create-new-tree.png]]
Kolom _Merger Mode_ dapat diubah dengan implikasi seperti berikut:
* Active : Tree tidak akan memiliki Node sendiri, namun akan menambahkan Node sesuai dengan Tree lain yang tersedia.
* _Non Active_ : Tree akan memiliki Node-nya sendiri, namun tidak bisa menambahkan Node dari Tree lain.

>**danger** Harap pastikan
>Anda tidak dapat mengubah kolom *merger mode* ketika Tree sudah dibuat.


---
    status: release
    title: "Konfigurasi External Read Only"
    description: Penjelasan konfigurasi External Read Only di komponen Tree
    pageDecoration:
      tree:
        priority: 0
    tags:
      draft
---
# Konfigurasi External Read Only

Node yang dikloning oleh [[Docs/Tipe Data/Tree]] lain dapat tetap terhubung ketika salah satu atribut kloningan berubah. Supaya ikatan ini lepas, maka Tree dapat dikonfigurasi agar tidak mengikuti perubahan dari kloningan lain. Hal ini berlaku berbeda tergantung dari [[Docs/Modul Data/Tree/Konfigurasi Merger Mode]]-nya, dengan penjelasan sebagai berikut:

| Merger Mode | Read Only | Atribut yang dapat berubah | Penjelasan Efek Read Only = Yes|
| ------------------ | ---- | ---- | ------------------------ |
| Tidak             | [[^value/boolean/Active]] | [[^field|Order]], [[^field|Name]] | Ketika Tree eksternal yang mengkloning Node melakukan perubahan, maka Node lokal akan berubah. |
| Tidak             | [[^value/boolean/Non-Active]] | - | Ketika Tree eksternal yang mengkloning Node melakukan perubahan pada Node, maka Node asal tidak berubah. |
| Ya             | [[^value/boolean/Active]] | [[^field|Order]], [[^field|Name]], [[^field|Children]] | Ketika Node asal melakukan perubahan, maka Node lokal akan berubah. |
| Ya             | [[^value/boolean/Non-Active]] | - | Ketika Node asal melakukan perubahan, maka Node lokal tidak berubah. |

Pengaturan ini berlaku pada Tree dengan/tanpa Merger Mode, karena perubahan Node di Tree merger juga dapat mengubah Node di Tree non-merger. Setiap atribut memiliki pilihan sendiri:

| Atribut | Jika [[^value/boolean/Non-Active]] | Jika [[^value/boolean/Active]] |
| --- | --- | --- |
| [[^field|Order]] | [[^field|Order]] Node di Tree ini ikut berubah ketika Node di Tree lain diperbarui. | [[^field|Order]] Node tidak ikut berubah. |
| [[^field|Name]] | [[^field|Name]] Node di Tree ini ikut berubah ketika Node di Tree lain diperbarui. | [[^field|Name]] Node tidak ikut berubah. |
| [[^field|Children]] | [[^field|Children]] Node di Tree ini ikut berubah ketika Node di Tree lain diperbarui. | [[^field|Children]] Node tidak ikut berubah. |

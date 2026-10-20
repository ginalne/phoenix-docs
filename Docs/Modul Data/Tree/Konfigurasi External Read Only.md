---
    status: draft
    pageDecoration:
      icon: x
      tree:
        priority: 0
    tags:
      draft
---
# Konfigurasi External Read Only

Node yang dikloning oleh [[Docs/Tipe Data/Tree]] lain dapat tetap terhubung ketika salah satu atribut kloningan berubah. Supaya ikatan ini lepas, maka Tree dapat dikonfigurasi agar tidak mengikuti perubahan dari kloningan lain. Hal ini berlaku berbeda tergantung dari [[Docs/Modul Data/Tree/Konfigurasi Merger Mode]]-nya, dengan penjelasan sebagai berikut:

| Merger Mode | Penjelasan Efek |
| ------------------ | ------------------------ |
| Tidak             | Ketika Tree lain yang mengkloning Node melakukan perubahan, maka Node asal akan berubah. |

, yaitu Node *clone* dan Node asalnya (*origin*). Pengaturan ini berlaku pada Tree dengan maupun tanpa Merger Mode, karena perubahan Node di Tree merger juga dapat mengubah Node di Tree non-merger. Setiap atribut memiliki pilihan sendiri:

| Atribut | Jika [[^value/boolean/Non-Active]] | Jika [[^value/boolean/Active]] |
| --- | --- | --- |
| [[^field|Order]] | [[^field|Order]] Node di Tree ini ikut berubah ketika Node di Tree lain diperbarui. | [[^field|Order]] Node tidak ikut berubah. |
| [[^field|Name]] | [[^field|Name]] Node di Tree ini ikut berubah ketika Node di Tree lain diperbarui. | [[^field|Name]] Node tidak ikut berubah. |
| [[^field|Children]] | [[^field|Children]] Node di Tree ini ikut berubah ketika Node di Tree lain diperbarui. | [[^field|Children]] Node tidak ikut berubah. |

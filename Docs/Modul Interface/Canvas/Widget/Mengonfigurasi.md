---
    status: release
    title: "Mengonfigurasi Widget"
    description:  Penjelasan cara mengonfigurasi Widget dalam komponen Canvas
    pageDecoration:
      tree:
        priority: 5
    tags:
      draft
---
# Mengonfigurasi Elemen

![[Docs/Modul Interface/Form/Elemen Form/configuration-form.png]]
Klik kiri pada Elemen di [[#Mode View dan Edit Mode|Edit Mode]] untuk memfokuskannya. Setelah itu muncul [[#Properties Panel]] dan [[#Header Toolbar]]. Selain itu, [[#Layout Panel]] dapat dibuka lewat ikon kecil di bawah Elemen yang difokuskan.

## Properties Panel

![[Docs/Modul Interface/Form/Elemen Form/properties-panel-form.png]]
Panel untuk mengatur properti Elemen secara rinci, seperti [[^field|Binding]], [[^field|State]], [[^field|Validators]], [[^field|Attributes]], [[^field|Children]], dan [[^field|Parent]]. Isinya berbeda-beda pada setiap Elemen.

| Bagian | Fungsi |
| --- | --- |
| [[^field|Binding]] | Mengikat Elemen ke data. Lihat [[#Binding Form]]. |
| [[^field|State]] | Mengatur kondisi Elemen, misalnya [[^field|Visible]] untuk menampilkan atau menyembunyikan Elemen. |
| [[^field|Validators]] | Aturan yang harus dipenuhi pengisi agar dapat mengirim Form, misalnya [[^field|Required]]. |
| [[^field|Attributes]] | Mengatur pengaturan khusus Elemen, termasuk gayanya. Isinya berbeda-beda pada setiap Elemen. |
| [[^field|Children]] atau [[^field|Parent]] | Menampilkan Elemen yang berada di dalam Elemen ini (*children*), atau Elemen tempat Elemen ini berada (*parent*). |

#### Header Toolbar

Bilah pintasan aksi yang selalu memiliki tombol [[^button/delete|Remove]] untuk menghapus Elemen.

#### Layout Panel

Panel untuk mengatur ukuran, *padding*, *margin*, dan beberapa *styling* Elemen. Setiap Elemen memiliki pengaturan ini, dan panel dibuka lewat ikon kecil di bawah Elemen yang difokuskan.

| Bagian | Fungsi |
| --- | --- |
| [[^field|min.]] layout | Ukuran persentase minimum Elemen terhadap layar. |
| [[^field/resize]] | Kontrol tambahan terkait ukuran atau tampilan pengaturan dimensi. |
| [[^field|padding]] | Mengatur jarak di bagian dalam Elemen, yaitu antara batas Elemen dan kontennya. |
| [[^field|margin]] | Mengatur jarak di luar Elemen, yaitu ruang antara Elemen tersebut dan Elemen lain di sekitarnya. |

---
    status: draft
    pageDecoration:
      icon: x
---
# EnumData Merge
EnumData memiliki atribut Name yang tidak dapat sama, namun dalam proses Data Gatehring, terkadang nilai tersebut bisa bervariatif karena kesalahan input walaupun maksudnya sama. Sehingga diperlukan adanya proses Merge yang aman agar komponen yang telah terleasi dengan variasi tersebut ini dapat mengikuti nilai yang sama yang telah dijadikan patokannya.

## Melakukan Merge
Anda dapat mengaturnya melalui tombol Merge dalam halaman kerja [[Docs/Modul Data/Enum/Apa itu Enum|Komponen Enum]].
![[Docs/Modul Data/Enum/enum-test.png]]
Setelah Mode Merge aktif, maka Anda dapat memilih EnumData yang ingin digabungkan.
![[Docs/Modul Data/Enum/merge-select.png]

## Arti dari “Externally”
Externally artinya sesuatu yang diluar Enum. Saat menentukan sebuah inputan dengan tipe data [[Docs/Tipe Data/EnumData|EnumData]], anda harus memilih header Enum. Input ini dapat muncul dalam [[Docs/Komponen/Table/Pengenalan|Tabel]], komponen dalam [[Docs/Modul Interface]] seperti [[Docs/Modul Interface/Form/Pengenalan|Form]] yang dapat diinput oleh publik.

>[!note]Tips
>Meskipun Enum Data bisa bertambah secara liar, namun atribut Name dalam EnumData tetap tidak dapat terduplikat. Meskipun akan banyak variasi Name yang mirip, Anda dapat menggunakan fitur [[Docs/Modul Data/Enum/EnumData Merge]] agar setiap data yang terelasi dengan EnumData tersebut dapat menjadi satu EnumData.
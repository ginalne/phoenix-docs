---
    status: draft
    title: Validators dalam Elemen Form
    description: Penjelasan Validators pada Elemen input Form (saat ini Required) dan cara mengisinya dengan nilai statis atau expression.
    pageDecoration:
      tree:
        priority: 4
---
# Validator dalam Elemen Form

>**note** Validator merupakan bagian dari [[Docs/Modul Interface/Form/Apa itu Form#Properties Panel|Properties Panel]] pada Elemen input di komponen [[Docs/Modul Interface/Form/Apa itu Form|Form]], salah satu komponen dalam modul [[Docs/Modul Interface/Pengenalan|Interface]] di Phoenix.

Validator adalah aturan pemeriksaan yang harus dipenuhi isian pengisi sebelum Form dapat dikirim. Saat ini Validators hanya memiliki satu aturan, yaitu [[^field|Required]], dan hanya tersedia pada Elemen input.

Seperti [[Docs/Modul Interface/Form/Elemen Form/State]], [[^field|Required]] dapat diisi dengan nilai statis atau [[Docs/Tipe Data/Expression]], sehingga sebuah isian dapat menjadi wajib hanya pada kondisi tertentu.

## Required

[[^field|Required]] mewajibkan pengisi mengisi Elemen input. Selama Elemen yang wajib belum terisi, Form belum dapat dikirim.

| Kondisi | Hasil |
| ------- | ----- |
| [[^field\|Required]] bernilai [[^value/boolean/true]] | Pengisi wajib mengisi Elemen agar dapat mengirim Form. |
| [[^field\|Required]] bernilai [[^value/boolean/false]] | Elemen boleh dikosongkan. |
| [[^field\|Visible]] atau [[^field\|Enable]] bernilai [[^value/boolean/false]] | [[^field\|Required]] tidak berlaku, apa pun nilainya. |

Nilai awal [[^field|Required]] pada Elemen input yang baru ditambahkan adalah [[^value/boolean/false]].

>**note** Required mengikuti State
> Elemen yang tidak terlihat atau tidak aktif tidak dapat diisi oleh pengisi, sehingga [[^field|Required]] tidak berlaku pada Elemen tersebut. Selengkapnya lihat [[Docs/Modul Interface/Form/State|State]].

## Antarmuka Validator

![[Docs/Modul Interface/Form/Elemen Form/validator-form.png]]
Validator berada di Properties Panel, di bawah bagian [[^field|State]]. Baris [[^field|Required]] terdiri dari label, ikon saklar, dan nilai.

| Bagian | Fungsi |
| ------ | ------ |
| Label Validator | Nama aturan, saat ini [[^field\|Required]]. |
| Ikon saklar | Ikon kecil di sebelah kanan label. Klik untuk beralih antara nilai statis dan expression. |
| Saklar nilai | Tampil saat memakai nilai statis. Hijau berarti [[^value/boolean/true]], abu-abu berarti [[^value/boolean/false]]. |
| Kolom isian expression | Tampil menggantikan saklar nilai saat memakai expression. Memiliki *autocomplete* dan *checker*. |

## Mengisi Required dengan Nilai Statis

Nilai statis tidak berubah selama pengisi mengisi Form.

1. Beralih ke [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit|Edit Mode]]
2. Klik kiri Elemen input yang ingin diatur
3. Pada bagian [[^field|Validators]] di Properties Panel, klik saklar pada [[^field|Required]]
4. Klik [[^button/save|Save]], atau tunggu *auto save* sekitar 3 detik

## Mengisi Required dengan Expression

Expression membuat Elemen menjadi wajib hanya saat kondisinya terpenuhi. Hasil [[^value/boolean/true]] berarti Elemen wajib diisi.

1. Beralih ke [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit|Edit Mode]]
2. Klik kiri Elemen input yang ingin diatur
3. Pada baris [[^field|Required]], klik ikon saklar di sebelah kanan label. Saklar nilai berganti menjadi kolom isian expression
4. Ketik expression. *Autocomplete* membantu melengkapi penulisan
5. Periksa hasil *checker* sampai tidak ada kesalahan
6. Klik [[^button/save|Save]], atau tunggu *auto save* sekitar 3 detik

Aturan penulisan expression pada Validator:

- Hasil expression harus [[Docs/Tipe Data/Boolean|Boolean]]. *Checker* akan memeriksanya.
- Parameter pada expression merujuk ke nama [[^field|Alias]] Input Elemen yang ada di Form.
- Expression dihitung ulang saat pengisi mengisi Form, sehingga Elemen dapat berubah dari tidak wajib menjadi wajib selama pengisian.

| Contoh expression | Arti |
| ----------------- | ---- |
| `Email not empty` | Elemen menjadi wajib bila isian dengan [[^field\|Label]] "Email" sudah terisi. |

## Praktik Terbaik

* Gunakan Required seperlunya
- Wajibkan hanya **isian yang benar-benar dibutuhkan** agar pengisi tidak terbebani.
- Gunakan **expression** untuk isian yang hanya wajib pada kondisi tertentu.
- Beri **[[^field|Alias]] yang jelas dan berbeda** pada Elemen yang dirujuk expression.
- Pastikan Elemen yang wajib **tidak tersembunyi atau nonaktif** bila Anda ingin [[^field|Required]] berlaku.

## TL:DR

- Validator adalah aturan yang harus dipenuhi isian sebelum Form dapat dikirim.
- Saat ini hanya ada [[^field|Required]], dan hanya pada Elemen input.
- [[^field|Required]] diisi dengan nilai statis atau [[Docs/Tipe Data/Expression]], dipilih lewat ikon saklar di sebelah kanan label.
- Expression harus menghasilkan [[Docs/Tipe Data/Boolean|Boolean]] dan merujuk ke nama [[^field|Label]] Elemen di Form.
- [[^field|Required]] tidak berlaku bila [[^field|Visible]] atau [[^field|Enable]] bernilai [[^value/boolean/false]].

## FAQ : Pertanyaan yang Sering Diajukan

>**faq**
>**Apakah Elemen Text bisa diberi Required?**
>Tidak. Validator hanya tersedia pada Elemen input karena hanya Elemen input yang menerima isian pengisi.
>**Mengapa Required tidak berlaku pada Elemen yang tersembunyi?**
>Pengisi tidak dapat melihat atau mengisi Elemen yang [[^field|Visible]] atau [[^field|Enable]]-nya [[^value/boolean/false]], sehingga tidak ada isian yang dapat diwajibkan.
>**Apakah akan ada Validator selain Required?**
>Saat ini hanya [[^field|Required]] yang tersedia.
>**Bagaimana membuat isian wajib hanya pada kondisi tertentu?**
>Beralih ke expression lewat ikon saklar di sebelah kanan label [[^field|Required]], lalu tulis kondisinya, misalnya `Email not empty`.


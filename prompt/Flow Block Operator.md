---
  pageDecoration:
    tree:
      priority: -16
  tags:
    meta
    prompt
---
2026-11-09 02:00

![[Docs/Modul Logic/Flow/Flow Block/Operator/operator-block-flow.png|Flow Block Operator pada Blueprint: Increment, Concatenate, Implode, Pad Left, Pad Right, TableRow Parse, Assign, Merge, Parse, Stringify, If, dan Node Parse]]
/phoenix-docs-silverbullet /phoenix-docs-knowledge 

Tolong buatkan **12 halaman Flow Block** untuk dokumentasi Phoenix, yaitu halaman per block yang menjadi tujuan tautan pada halaman Pengenalan kategori Flow Block Operator.

## Daftar halaman

Seluruh path berada di bawah `Docs/Modul Logic/Flow/Flow Block/`. Alias tautan mengikuti tabel pada halaman kategori.

| No  | Kategori | Path | Alias tautan |
| --- | --- | --- | --- |
| 1   | Operator (Number) | `Operator/Number/Increment` | Increment Operator Block |
| 2   | Operator (String) | `Operator/String/Concatenate` | Concatenate Operator Block |
| 3   | Operator (String) | `Operator/String/Implode` | Implode Operator Block |
| 4   | Operator (String) | `Operator/String/Pad Left` | Pad Left Operator Block |
| 5   | Operator (String) | `Operator/String/Pad Right` | Pad Right Operator Block |
| 6  | Operator (Table) | `Operator/Table/TableRow Parse` | TableRow Parse Operator Block |
| 7  | Operator (Object) | `Operator/Object/Assign` | Assign Operator Block |
| 8  | Operator (Object) | `Operator/Object/Merge` | Merge Operator Block |
| 9  | Operator (Object) | `Operator/Object/Parse` | Parse Operator Block |
| 10  | Operator (Object) | `Operator/Object/Stringify` | Stringify Operator Block |
| 11  | Operator (Boolean) | `Operator/Boolean/If` | If Operator Block |
| 12  | Operator (Tree) | `Operator/Tree/Node Parse` | Node Parse Operator Block |

Catatan: kelompok tipe data pada Operator tidak memiliki halaman Pengenalan sendiri, jadi halaman block langsung berada di bawah folder tipe data.

## Increment


## Concatenate
Menghubungkan dua string input menjadi satu string. Tidak dapat error karena jika salah satu dibiarkan empty maka hasilnya adalah salah satu yang diinput.

## Implode
Menggabungkan input bertipe data string atau array dengan isi string, dengan separator.

## Pad Left
Menambahkan data String dengan Pad String disebelah kiri sampai dengan panjang string sesuai dengan Length. Fatal Error jika String atau Pad String dibiarkan kosong.

## Pad Right
Menambahkan data String dengan Pad String disebelah kanan sampai dengan panjang string sesuai dengan Length.Fatal Error jika String atau Pad String dibiarkan kosong.

## TableRow Parse
Mengubah input Row menjadi data object dan text (jika output nya terelasi), dengan Input Rel. Depth untuk relasi keadalamannya. Relasi kedalaman yang dimaksud adalah jika kolom pada Row memiliki relasi ke data lain, maka hasil dari kolom tersebut akan ditelusuri sehingga data menjadi semakin rinci. Fatal Error jika Row dibiarkan error. Rel. Depth yang kosong dianggap bernilai 0.

## Assign
Menambahkan atribut pada object dengan input Key sebagai key, dan Value adalah bertipe data object atau string (dapat di change type, namun bawaannya adalah object). Key ditulis dengan simbol “.” untuk mengisi object di kedalaman, semisal ditulis “job.status.level” artinya akan mengisi di atribut job -> status -> level. Fatal Erro jika Key atau Value dibiarkan kosong. Assign bersifat override, jadi jika ada data sebelumnya pada key, maka akan ditimpa. Output Object adalah hasilnya.

## Merge
Menggabungkan Objects yaitu input bertipe array dengan tipe object. Merge akan menimpa data pertama dengan data selanjutnya pada atribut yang spesifik sama. Jadi jika data saling mengisi pada kedalaman tertentu maka tidak ada yang ditimpa. Fatal Error jika Objects dibiarkan kosong. Result adalah output bertipe data object.

## Parse
## Stringify
## If
## Node Parse
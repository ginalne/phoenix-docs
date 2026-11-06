---
  pageDecoration:
    tree:
      priority: -15
  tags:
    meta
    prompt
---
2026-11-07 02:00

![[Docs/Modul Logic/Flow/Flow Block/Data Table/data-table-block-flow.png|Tujuh Flow Block Data Table pada Blueprint: Add Row, Delete Row, Table, Table Column, Table Row, TableData Getter, dan TableData Setter]]
/phoenix-docs-silverbullet /phoenix-docs-knowledge 

Tolong saya membuat 7 halaman flow block untuk data enum:

1. Add Row
   Table adalah input (pilihan) yang bakal diisi Row. New Row adalah output yang dihasilkan. Row ini tidak memiliki TableData yang artinya seperti Row baru yang kosong.
2. Delete Row
   Row adalah input bertipedata row untuk target row yang akan dihapus. Force adalah input bertipedata boolean (true jika ingin dihapus secara paksa - berakibat dengan relasi dan histori yang sudah ada). Succeed = boolean true dan Error “-” jika berhasil, begitu sebaliknya. Fatal Error ketika Row atau Force bernilai empty.
3. Table
   Table adalah input bertipedata table. Output adalah atribut dari table yang diinput.
4. Table Column
   Table Column adalah input bertipedata column. Output adalah atribut dari column yang input.
5. Table Row
   Table Row adalah input bertipe row. Output adalah atribut dari Row yang diinput.
6. TableData Getter
   Column adalah input bertipedata column, dan Row adalah input bertipedata Row atau dapat diganti dengan tipedata number atau string (harus berisi nilai dari index si Row). Output TableData adalah Value dari TableData itu sendiri. Output Is Empty keluar boolean true jika TableData tidak ada isinya atau tidak ditemukan. Fatal Error jika Column atau Row berisi empty.
7. TableData Setter
   Column adalah input bertipedata column, dan Row adalah input bertipedata Row atau dapat diganti dengan tipedata number atau string (harus berisi nilai dari index si Row). Output Pass adalah Value yang diinput. Output Value Conflict adalah bernilai boolean true jika value yang dimasukan tidak sesuai dengan tipedata kolomnya. Fatal Error jika Column atau Row dibiarkan empty, atau Value dibiarkan N/A karena column pasti memiliki tipedata yang terdefinisi.

Catatan untuk Calude:
Infomasi mengenai N/A Type, adalah input dengan tipe yang belum didefinisi. cara pendefinisiannya adalah dengan klik kanan -> Change Type -> lalu pilih tipe data.
---
  pageDecoration:
    tree:
      priority: -15
  tags:
    meta
    prompt
---
2026-11-07 02:00


![[Docs/Modul Logic/Flow/Flow Block/Data Tree/data-tree-block-flow.png|Sepuluh Flow Block Data Tree pada Blueprint: Add Node, Assign Node, Delete Node, Node, Node Get Ancestor, Node Get Children, Node Get Parent, Node Setter, Tree, dan Tree Get Origin]]

/phoenix-docs-silverbullet /phoenix-docs-knowledge 

Tolong saya membuat 10 halaman flow block untuk data tree:
1. Tree
   Tree adalah input bertipe data Tree. Output adalah atribut dari tree yang diinput.
2. Node
    Node adalah input bertipe data Node. Output adalah atribut dari node yang diinput.
3. Node Setter
    Node adalah input bertipe data Node, Order bertipe data number, Name bertipe data string. Pass adalah output dari Node yang sudah diinput. Jika node, order atau name empty maka Fatal Error.
3. Add Node
   Parent adalah input yang diisi Node (akan tampil semua node dalam semua tree di pilihan). Order adalah input bertipe number untuk Node baru. Name adalah input bertipe string. Parent, Order atau Name akan menghasilkan Fatal Error jika dibiarkan kosong
4. Assign Node
   Parent adalah input bertipe data Node sebagai bakal parent. Order adalah input bertipe data number bakal menjadi value order dari Node children yang diinput. Node children adalah input bertipedata Node yang ditempatkan pada parent yang diinput. Output pass children adalah Node children yang diinput. Error dapat terjadi jika Node parent dan children bukan dalam tree yang sama. Fata Error jika Parent, Order atau Node dibiarkan empty.
5. Delete Node
   Node adalah input bertipedata Node sebagai target Node yang akan dihapus. Force adalah input bernilai boolean, bernilai true jika ingin menghapus Node yang sudah digunakan. Dapat menghasilkan Output succeed atau error bernilai boolean, akan Fatal Error jika Node atau Force dibiarkan empty.
6. Tree Get Origin
   Tree adalah input bertipedata Tree. Output The Origin (Node) adalah bertipedata Node yaitu Node Origin dalam tree. Fatal Error jika Tree dibiarkan kosong.
7. Node Get Parent
   Node adalah 
   ![[Docs/Modul Logic/Flow/Flow Block/Data Tree/data-tree-block-flow.png|Sepuluh Flow Block Data Tree pada Blueprint: Add Node, Assign Node, Delete Node, Node, Node Get Ancestor, Node Get Children, Node Get Parent, Node Setter, Tree, dan Tree Get Origin]]

2. Delete Node
   Row adalah input bertipe data row untuk target row yang akan dihapus. Force adalah input bertipedata boolean (true jika ingin dihapus secara paksa - berakibat dengan relasi dan histori yang sudah ada). Succeed = boolean true dan Error “-” jika berhasil, begitu sebaliknya. Fatal Error ketika Row atau Force bernilai empty.
3. Table
   Table adalah input bertipe data table. Output adalah atribut dari table yang diinput.
4. Table Column
   Table Column adalah input bertipe data column. Output adalah atribut dari column yang input.
5. Table Row
   Table Row adalah input bertipe row. Output adalah atribut dari Row yang diinput.
6. TableData Getter
   Column adalah input bertipe data column, dan Row adalah input bertipe data Row atau dapat diganti dengan tipe data number atau string (harus berisi nilai dari index si Row). Output Table Data adalah Value dari Table Data itu sendiri. Output Is Empty keluar boolean true jika Table Data tidak ada isinya atau tidak ditemukan. Fatal Error jika Column atau Row berisi empty.
7. TableData Setter
   Column adalah input bertipe data column, dan Row adalah input bertipe data Row atau dapat diganti dengan tipe data number atau string (harus berisi nilai dari index si Row). Output Pass adalah Value yang diinput. Output Value Conflict adalah bernilai boolean true jika value yang dimasukan tidak sesuai dengan tipedata kolomnya. Fatal Error jika Column atau Row dibiarkan empty, atau Value dibiarkan N/A karena column pasti memiliki tipedata yang terdefinisi.

Catatan untuk Calude:
Infomasi mengenai N/A Type, adalah input dengan tipe yang belum didefinisi. cara pendefinisiannya adalah dengan klik kanan -> Change Type -> lalu pilih tipe data.
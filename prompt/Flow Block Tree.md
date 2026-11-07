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
4. Add Node
   Parent adalah input yang diisi Node (akan tampil semua node dalam semua tree di pilihan). Order adalah input bertipe number untuk Node baru. Name adalah input bertipe string. Parent, Order atau Name akan menghasilkan Fatal Error jika dibiarkan kosong
5. Assign Node
   Parent adalah input bertipe data Node sebagai bakal parent. Order adalah input bertipe data number bakal menjadi value order dari Node children yang diinput. Node children adalah input bertipedata Node yang ditempatkan pada parent yang diinput. Output pass children adalah Node children yang diinput. Error dapat terjadi jika Node parent dan children bukan dalam tree yang sama. Fata Error jika Parent, Order atau Node dibiarkan empty.
6. Delete Node
   Node adalah input bertipedata Node sebagai target Node yang akan dihapus. Force adalah input bernilai boolean, bernilai true jika ingin menghapus Node yang sudah digunakan. Dapat menghasilkan Output succeed atau error bernilai boolean, akan Fatal Error jika Node atau Force dibiarkan empty.
7. Tree Get Origin
   Tree adalah input bertipedata Tree. Output The Origin (Node) adalah bertipedata Node yaitu Node Origin dalam tree. Fatal Error jika Tree dibiarkan kosong.
8. Node Get Parent
   Node adalah input bertipedata Node. Depth adalah input bertipedata number. Output the parent (node) bertipedata Node adalah hasil dari tracing parent dari node yang diinput berdasarkan depth (jika node adalah saya, depth 1 adalah ayah saya, jika 2 adalah kakek saya), Not Found bertipedata boolean.
9. Node Get Children
   Node adalah input bertipedata Node. Child Order adalah input bertipedata number. Output The Children (Node) bertipedata Node adalah anak dari node yang diinput berdasarkan order yang diinput. Not Found adalah output bertipedata boolean, jika anak dengan nomor order yang diinput tidak ada.
10. Node Get Ancestor
    Node adalah input bertipedata Node. Anc. Level adalah input bertipedata number. Output The Ancestor (Node) adalah tracing dari origin ke node yang diinput sesuai “Anc. Level”, jika anc.level bernilai 1 maka akan keluar node leluhur pertama dan setelahnya. Not Found adalah output ketika leluhur tidak ditemukan (Anc.Level < 1 atau Anc.Level > jumlah silsilah dari origin ke node yang dipilih). 
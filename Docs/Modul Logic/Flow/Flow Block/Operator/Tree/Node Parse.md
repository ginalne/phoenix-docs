---
    status: release
    title: Node Parse Operator Block
    description: Mengubah Node menjadi Object dan Text dengan atribut parent dan children sesuai kedalaman pada Flow Block Operator Node Parse.
    pageDecoration:
      tree:
        priority: 0
---

# Node Parse Operator Block

>**note** Node Parse Block merupakan salah satu Flow Block kelompok Tree pada kategori [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Node Parse Block adalah Flow Block Operator yang mengubah [[^input|Node]] ([[Docs/Tipe Data/Node]]) menjadi [[Docs/Tipe Data/Object]] dan [[Docs/Tipe Data/Text]] berformat JSON. Atribut Node menjadi dasar hasilnya, lalu atribut `parent` dan `children` ditambahkan sesuai [[^input|Anc. Depth]] dan [[^input|Child Depth]] yang Anda isi.

![[Docs/Modul Logic/Flow/Flow Block/Operator/Tree/node-parse-block-flow.png|Node Parse Block pada Blueprint Flow]]
## Input dan Output

Node Parse Block memiliki 3 input di sisi kiri, 2 output di sisi kanan dan tidak memiliki Control. Output hanya keluar bila terhubung ke block lain. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| ----- | --------- | ---------- |
| [[^input|Node]] | [[Docs/Tipe Data/Node]] | Node yang akan diubah. Tidak boleh kosong. |
| [[^input|Anc. Depth]] | [[Docs/Tipe Data/Number]] | Kedalaman leluhur (ancestor) yang disertakan sebagai atribut `parent`. Bila dibiarkan kosong, dianggap bernilai [[^value/number|0]]. |
| [[^input|Child Depth]] | [[Docs/Tipe Data/Number]] | Kedalaman anak (child) yang disertakan sebagai atribut `children`. Bila dibiarkan kosong, dianggap bernilai [[^value/number|0]]. |

### Output

| Output | Tipe Data | Keterangan |
| ------ | --------- | ---------- |
| [[^output|Object]] | [[Docs/Tipe Data/Object]] | Hasil dalam bentuk Object. Aliran diteruskan bila output terhubung. |
| [[^output|Text]] | [[Docs/Tipe Data/Text]] | Hasil dalam bentuk Text. Aliran diteruskan bila output terhubung. |

Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

## Cara Kerja

1. Node Parse Block menerima [[^input|Node]], [[^input|Anc. Depth]], dan [[^input|Child Depth]].
2. Block membuat JSON dengan atribut Node sebagai dasar.
3. Bila Anc. Depth lebih dari [[^value/number|0]], atribut `parent` ditambahkan sesuai kedalamannya. Bila Child Depth lebih dari [[^value/number|0]], atribut `children` ditambahkan sesuai kedalamannya.
4. Hasilnya dikeluarkan lewat [[^output|Object]] atau [[^output|Text]] sesuai output yang terhubung.

## Contoh Penggunaan

Contoh berikut memakai Tree kategori produk. Angka di dalam kurung adalah `order` Node, dan Node yang dipilih adalah **Laptop**.

```
Elektronik (1)
└─ Komputer (1)
   └─ Laptop (1)            <- Node yang dipilih
      ├─ Laptop Gaming (1)
      └─ Laptop Kantor (2)
```

Tanpa kedalaman, hasilnya hanya atribut Node itu sendiri. Anc. Depth menambahkan `parent` (naik ke leluhur) dan Child Depth menambahkan `children` (turun ke anak).

| Node | Anc. Depth | Child Depth | Hasil (Object) | Status |
| ---- | ---------- | ----------- | -------------- | ------ |
| [[^value/node|Laptop]] | [[^value/empty]] | [[^value/empty]] | [[^value/object|{ "order": 1, "name": "Laptop" }]] | [[^flowstate/Succeed]] |
| [[^value/node|Laptop]] | [[^value/number|1]] | [[^value/empty]] | [[^value/object|{ "order": 1, "name": "Laptop", "parent": { "order": 1, "name": "Komputer" } }]] | [[^flowstate/Succeed]] |
| [[^value/node|Laptop]] | [[^value/number|2]] | [[^value/empty]] | [[^value/object|{ "order": 1, "name": "Laptop", "parent": { "order": 1, "name": "Komputer", "parent": { "order": 1, "name": "Elektronik" } } }]] | [[^flowstate/Succeed]] |
| [[^value/node|Laptop]] | [[^value/empty]] | [[^value/number|1]] | [[^value/object|{ "order": 1, "name": "Laptop", "children": [{ "order": 1, "name": "Laptop Gaming" }, { "order": 2, "name": "Laptop Kantor" }] }]] | [[^flowstate/Succeed]] |
| [[^value/node|Laptop]] | [[^value/number|1]] | [[^value/number|1]] | [[^value/object|{ "order": 1, "name": "Laptop", "parent": { "order": 1, "name": "Komputer" }, "children": [{ "order": 1, "name": "Laptop Gaming" }, { "order": 2, "name": "Laptop Kantor" }] }]] | [[^flowstate/Succeed]] |
| [[^value/empty]] | [[^value/number|1]] | [[^value/number|1]] | - | [[^flowstate/Fatal Error]] |

Perhatikan perbedaannya: Anc. Depth bergerak **ke atas** dan menghasilkan `parent` bersarang (Komputer, lalu Elektronik), sedangkan Child Depth bergerak **ke bawah** dan menghasilkan `children` berupa daftar Node (Laptop Gaming dan Laptop Kantor).

Status [[^flowstate/Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- Isi **Anc. Depth** dan **Child Depth** seperlunya agar hasil tidak lebih besar dari kebutuhan, terutama pada Tree dengan banyak Node.
- Ambil Node dari output [[Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event|Tree Node Event Block]] atau [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node|Node Block]] untuk mengolah Node yang berubah.

## Batasan dan Catatan

- Node Parse Block adalah Flow Block non-Event sehingga hanya diproses bila memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].
- [[^input|Node]] yang dibiarkan kosong menghasilkan status [[^flowstate/Fatal Error]].
- [[^input|Anc. Depth]] dan [[^input|Child Depth]] yang dibiarkan kosong dianggap bernilai [[^value/number|0]], sehingga atribut `parent` dan `children` tidak muncul pada hasil.

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]]
- [[Docs/Modul Logic/Flow/Flow Block/Operator/Table/TableRow Parse|TableRow Parse Operator Block]]
- [[Docs/Tipe Data/Node]]
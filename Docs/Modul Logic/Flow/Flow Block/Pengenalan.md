---
    status: release
    title: "Apa itu Flow Block"
    description: 
    pageDecoration:
      tree:
        priority: 10
    tags:
      draft
---
# Apa itu Flow Block

Flow Block adalah unit terkecil penyusun Flow, dan setiap block memiliki fungsi (masukan, proses dan keluaran yang berbeda-beda) dan dapat dihubungkan dengan block lain.

Pengkategorian Flow Block berfungsi agar memudahkan pencarian block. Selengkapnya bisa klik tautan per masing-masing kategori atau isinya.

| Kategori | Jenis Flow Block |
| --- | --- |
| [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Event]] | [[Docs/Modul Logic/Flow/Flow Block/Event/Pulser]], [[Docs/Modul Logic/Flow/Flow Block/Event/Variable Event]], [[Docs/Modul Logic/Flow/Flow Block/Event/Enum Data Event]], [[Docs/Modul Logic/Flow/Flow Block/Event/Table Row Event]], [[Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event]] |
| [[Docs/Modul Logic/Flow/Flow Block/Data/Pengenalan|Data]] | [[Docs/Modul Logic/Flow/Flow Block/Data/Variable/Pengenalan|Variable]] ([[Docs/Modul Logic/Flow/Flow Block/Data/Variable/Add Variable]], [[Docs/Modul Logic/Flow/Flow Block/Data/Variable/Delete Variable]], [[Docs/Modul Logic/Flow/Flow Block/Data/Variable/Variable]], [[Docs/Modul Logic/Flow/Flow Block/Data/Variable/Variable Getter]], [[Docs/Modul Logic/Flow/Flow Block/Data/Variable/Variable Setter]], [[Docs/Modul Logic/Flow/Flow Block/Data/Variable/Variable Value]]); [[Docs/Modul Logic/Flow/Flow Block/Data/Enum/Pengenalan|Enum]] ([[Docs/Modul Logic/Flow/Flow Block/Data/Enum/Add EnumData]], [[Docs/Modul Logic/Flow/Flow Block/Data/Enum/Delete EnumData]], [[Docs/Modul Logic/Flow/Flow Block/Data/Enum/Enum]], [[Docs/Modul Logic/Flow/Flow Block/Data/Enum/EnumData]], [[Docs/Modul Logic/Flow/Flow Block/Data/Enum/EnumData Getter]], [[Docs/Modul Logic/Flow/Flow Block/Data/Enum/EnumData Setter]], [[Docs/Modul Logic/Flow/Flow Block/Data/Enum/EnumData Value]]); [[Docs/Modul Logic/Flow/Flow Block/Data/Table/Pengenalan|Table]] ([[Docs/Modul Logic/Flow/Flow Block/Data/Table/Add Row]], [[Docs/Modul Logic/Flow/Flow Block/Data/Table/Delete Row]], [[Docs/Modul Logic/Flow/Flow Block/Data/Table/Table]], [[Docs/Modul Logic/Flow/Flow Block/Data/Table/Table Column]], [[Docs/Modul Logic/Flow/Flow Block/Data/Table/Table Row]], [[Docs/Modul Logic/Flow/Flow Block/Data/Table/TableData Getter]], [[Docs/Modul Logic/Flow/Flow Block/Data/Table/TableData Setter]]); [[Docs/Modul Logic/Flow/Flow Block/Data/Tree/Pengenalan|Tree]] ([[Docs/Modul Logic/Flow/Flow Block/Data/Tree/Add Node]], [[Docs/Modul Logic/Flow/Flow Block/Data/Tree/Assign Node]], [[Docs/Modul Logic/Flow/Flow Block/Data/Tree/Delete Node]], [[Docs/Modul Logic/Flow/Flow Block/Data/Tree/Node]], [[Docs/Modul Logic/Flow/Flow Block/Data/Tree/Node Get Ancestor]], [[Docs/Modul Logic/Flow/Flow Block/Data/Tree/Node Get Children]], [[Docs/Modul Logic/Flow/Flow Block/Data/Tree/Node Get Parent]], [[Docs/Modul Logic/Flow/Flow Block/Data/Tree/Node Setter]], [[Docs/Modul Logic/Flow/Flow Block/Data/Tree/Tree]], [[Docs/Modul Logic/Flow/Flow Block/Data/Tree/Tree Get Origin]]) |
| [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Pengenalan|I/O]] | [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Branch]], [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Passer]] |
| [[Docs/Modul Logic/Flow/Flow Block/Query/Pengenalan|Query]] | [[Docs/Modul Logic/Flow/Flow Block/Query/Condition]], [[Docs/Modul Logic/Flow/Flow Block/Query/Execute]] |
| [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Operator]] | [[Docs/Modul Logic/Flow/Flow Block/Operator/Number/Pengenalan|Number]] ([[Docs/Modul Logic/Flow/Flow Block/Operator/Number/Increment]]); [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Pengenalan|String]] ([[Docs/Modul Logic/Flow/Flow Block/Operator/String/Concatenate]], [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Implode]], [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Pad Left]], [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Pad Right]]); [[Docs/Modul Logic/Flow/Flow Block/Operator/Table/Pengenalan|Table]] ([[Docs/Modul Logic/Flow/Flow Block/Operator/Table/TableRow Parse]]); [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Pengenalan|Object]] ([[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Assign]], [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Merge]], [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Parse]], [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Stringify]]); [[Docs/Modul Logic/Flow/Flow Block/Operator/Boolean/Pengenalan|Boolean]] ([[Docs/Modul Logic/Flow/Flow Block/Operator/Boolean/If]]); [[Docs/Modul Logic/Flow/Flow Block/Operator/Tree/Pengenalan|Tree]] ([[Docs/Modul Logic/Flow/Flow Block/Operator/Tree/Node Parse]]) |
| [[Docs/Modul Logic/Flow/Flow Block/Modular/Pengenalan|Modular]] | [[Docs/Modul Logic/Flow/Flow Block/Modular/API/Pengenalan|API]] ([[Docs/Modul Logic/Flow/Flow Block/Modular/API/HTTP Request]]); [[Docs/Modul Logic/Flow/Flow Block/Modular/AI/Pengenalan|AI]] ([[Docs/Modul Logic/Flow/Flow Block/Modular/AI/OpenAI 4]]) |
| Misc | [[Docs/Modul Logic/Flow/Flow Block/Chrono/Pengenalan|Chrono]] ([[Docs/Modul Logic/Flow/Flow Block/Chrono/Delay]]); [[Docs/Modul Logic/Flow/Flow Block/Error/Pengenalan|Error]] ([[Docs/Modul Logic/Flow/Flow Block/Error/Error Message]]) |

Berikut adalah cara mengelola Flow Block didalam Flow:
1. [[Docs/Modul Logic/Flow/Flow Block/Menambahkan]]
2. [[Docs/Modul Logic/Flow/Flow Block/Menghapus]]
3. [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi]]
4. [[Docs/Modul Logic/Flow/Flow Block/Menghapus Koneksi]]

## TL:DR
- Tambahkan block lewat klik kanan pada blueprint ➜ [[^field/add|Add]].
- Hubungkan block dengan menahan klik pada output, lalu lepaskan di input. Hapus hubungan dengan melepas pada bagian kosong.
- Jalankan manual dengan tombol pada Block Event, lalu pantau lewat [[^button/activity|Activity]].

## FAQ : Pertanyaan yang Sering Diajukan

>**faq**
>**Bagaimana menambahkan Flow Block?**
>Klik kanan pada blueprint, pilih [[^field/add|Add]], lalu pilih kategori dan Flow Block yang diinginkan.
>**Bagaimana menghubungkan dua Flow Block?**
>Klik dan tahan titik output pada block asal, seret ke titik input block tujuan, lalu lepaskan.


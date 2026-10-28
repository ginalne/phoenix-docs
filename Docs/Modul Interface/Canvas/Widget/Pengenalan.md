---
    status: release
    title: "Widget Canvas"
    description: 
    pageDecoration:
      tree:
        priority: 6
---
# Widget Canvas

Widget adalah elemen penyusun tampilan Canvas. Widget yang tersedia:


| Widget                                                                                      | Kelompok                |
| ------------------------------------------------------------------------------------------- | ----------------------- |
| [[Docs/Modul Interface/Canvas/Widget/Text/Pengenalan|Text]]                                  | Teks                    |
| [[Docs/Modul Interface/Canvas/Widget/Chart Pie/Pengenalan|Chart Pie]]                        | Grafik                  |
| [[Docs/Modul Interface/Canvas/Widget/Chart Line/Pengenalan|Chart Line]]                      | Grafik                  |
| [[Docs/Modul Interface/Canvas/Widget/Chart Bar/Pengenalan|Chart Bar]]                        | Grafik                  |
| [[Docs/Modul Interface/Canvas/Widget/Chart Radial/Pengenalan|Chart Radial]]                  | Grafik                  |
| [[Docs/Modul Interface/Canvas/Widget/Chart Linear/Pengenalan|Chart Linear]]                  | Grafik                  |
| [[Docs/Modul Interface/Canvas/Widget/Table/Pengenalan|Table]]                                | Tampilan data           |
| [[Docs/Modul Interface/Canvas/Widget/Kanban/Pengenalan|Kanban]]                              | Tampilan data           |
| [[Docs/Modul Interface/Canvas/Widget/Gantt/Pengenalan|Gantt]]                                | Tampilan data           |
| [[Docs/Modul Interface/Canvas/Widget/Timeline/Pengenalan|Timeline]]                          | Tampilan data           |
| [[Docs/Modul Interface/Canvas/Widget/Gallery/Pengenalan|Gallery]]                            | Tampilan data           |
| [[Docs/Modul Interface/Canvas/Widget/Space/Pengenalan|Space]]                                | Tampilan data           |
| [[Docs/Modul Interface/Canvas/Widget/Button/Pengenalan|Button]]                              | Aksi                    |


Beberapa widget bekerja seperti komponen Interface lain dalam versi lite. Sebagai contoh, komponen [[Docs/Modul Interface/Timeline/Apa itu Timeline|Timeline]] memiliki Event dan banyak data, sedangkan widget Timeline pada Canvas hanya menyajikan satu data.

[[Docs/Tipe Data/Query]] setiap widget diatur melalui tombol [[^button/q]] pada header toolbar. Isi widget, yaitu data hasil Query, tidak dapat dimanipulasi dari Canvas.

Widget Button dapat berfungsi sebagai pemicu [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] melalui Flow Block [[Docs/Modul Logic/Flow/Flow Block/Event/Pulser|Pulser]], atau membuka komponen apa pun.

Penjelasan keunikan masing-masing widget ada di halaman widget yang bersangkutan.
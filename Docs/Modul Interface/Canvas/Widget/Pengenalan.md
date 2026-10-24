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
| [[Docs/Modul Interface/Form/Widget/Text/Penjelasan|Text]]                                  | Teks                    |
| [[Docs/Modul Interface/Form/Widget/Chart Pie/Penjelasan|Chart Pie]]                        | Grafik                  |
| [[Docs/Modul Interface/Form/Widget/Chart Line/Penjelasan|Chart Line]]                      | Grafik                  |
| [[Docs/Modul Interface/Form/Widget/Chart Bar/Penjelasan|Chart Bar]]                        | Grafik                  |
| [[Docs/Modul Interface/Form/Widget/Chart Radial/Penjelasan|Chart Radial]]                  | Grafik                  |
| [[Docs/Modul Interface/Form/Widget/Chart Linear/Penjelasan|Chart Linear]]                  | Grafik                  |
| [[Docs/Modul Interface/Form/Widget/Table/Penjelasan|Table]]                                | Tampilan data           |
| [[Docs/Modul Interface/Form/Widget/Kanban/Penjelasan|Kanban]]                              | Tampilan data           |
| [[Docs/Modul Interface/Form/Widget/Gantt/Penjelasan|Gantt]]                                | Tampilan data           |
| [[Docs/Modul Interface/Form/Widget/Timeline/Penjelasan|Timeline]]                          | Tampilan data           |
| [[Docs/Modul Interface/Form/Widget/Gallery/Penjelasan|Gallery]]                            | Tampilan data           |
| [[Docs/Modul Interface/Form/Widget/Space/Penjelasan|Space]]                                | Tampilan data           |
| [[Docs/Modul Interface/Form/Widget/Button/Penjelasan|Button]]                              | Aksi                    |

Beberapa widget bekerja seperti komponen Interface lain dalam versi lite. Sebagai contoh, komponen [[Docs/Modul Interface/Timeline/Apa itu Timeline|Timeline]] memiliki Event dan banyak data, sedangkan widget Timeline pada Canvas hanya menyajikan satu data.

[[Docs/Tipe Data/Query]] setiap widget diatur melalui tombol [[^button/q]] pada header toolbar. Isi widget, yaitu data hasil Query, tidak dapat dimanipulasi dari Canvas.

Widget Button dapat berfungsi sebagai pemicu [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] melalui Flow Block [[Docs/Modul Logic/Flow/Flow Block/Event/Pulser|Pulser]], atau membuka komponen apa pun.

Penjelasan keunikan masing-masing widget ada di halaman widget yang bersangkutan.
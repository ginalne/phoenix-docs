---
    status: release
    title: "Mempublikasi Canvas"
    description: Penjelasan cara mempublikasikan komponen Canvas
    pageDecoration:
      tree:
        priority: -1
    tags:
      draft
---

Publish adalah konfigurasi untuk mengubah Canvas menjadi dipublikasikan. Klik [[^button/publish|Publish]] untuk membuka modal konfigurasinya, yang hanya berisi dua kolom:

| Kolom                    | Fungsi                                                                                                                         |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------ |
| [[^field|Status]]       | Menentukan Canvas dipublikasikan atau tidak: [[^value/radio|Active]] atau [[^value/radio|Non-Active]].                       |
| [[^field|Link]]         | Tautan Canvas yang dibuat otomatis. Anda dapat menyalin tautan (*copy*) atau membukanya di tab baru (*open new tab*).          |

Tautan yang Active dapat dibuka oleh publik dalam View Mode saja. Jika Status [[^value/radio|Non-Active]], tautan tidak dapat dibuka karena Canvas tidak dalam status dipublikasikan.

>**warning** Canvas yang dipublikasikan dapat dipakai publik
> Widget Button pada Canvas yang dipublikasikan dapat ditekan oleh siapa pun yang memiliki tautan. Pastikan Flow atau komponen yang dipicu aman dijalankan oleh publik.

Akses Publish mengikuti Function Access di [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]]. Lihat [[#Hak Akses Canvas]].

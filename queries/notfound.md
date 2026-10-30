---
    status: draft
    pageDecoration:
      icon: check
      tree:
        priority: 0
---
# List of Queries

>**danger** Berikut adalah daftar link yang sudah dimention tapi belum ada halamannya
>${query[[
  from p = index.aspiringPages()
  select "- <i style=\"color:#c22\">" .. p.name .. "</i> [[".. p.name .. "|create]] — <small style=\"color:#ffa\">".. templates.paragraphItem(p) .. "</small>"
where not string.startsWith(p.name, "button")
and not string.startsWith(p.name, "value")
and not string.startsWith(p.page, "STYLING")
and not string.startsWith(p.page, "Library")
]]}

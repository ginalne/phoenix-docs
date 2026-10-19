---
    status: draft
    pageDecoration:
      icon: check
      tree:
        priority: 0
---
# List of Queries

>**warning** Berikut adalah daftar TODO
>${query[[
  from p = index.tasks(_)
  where p.page != "index"
  and p.page != "SKILL"
  and p.page != "request"
  select templates.taskItem(p) .. " — <small style=\"opacity:.7;color:#ffa\">" .. p.page .. "</small>"
]]}

>**danger** Berikut adalah daftar link yang sudah dimention tapi belum ada halamannya
>${query[[
  from p = index.aspiringPages()
  select "- <i style=\"color:#c22\">" .. p.name .. "</i> [[".. p.name .. "|create]] — <small style=\"color:#ffa\">".. templates.paragraphItem(p) .. "</small>"
where not string.startsWith(p.name, "button")
and not string.startsWith(p.name, "value")
and not string.startsWith(p.page, "STYLING")
and not string.startsWith(p.page, "Library")
]]}

>**warning** Berikut adalah daftar link yang sudah dimention tapi masih draft
>${query[[
  from p = index.tag "draft"
  select "- " .. p.name .. "         [[" .. p.name .. "]]" 
]]}
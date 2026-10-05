---
    status: draft
    pageDecoration:
      icon: check
      tree:
        priority: 0
---
# List of Queries

## Berikut adalah daftar TODO

${query[[
  from p = index.tasks(_)
  where p.page != "index"
  select templates.taskItem(p) .. " — <small style=\"opacity:.7;color:#ffa\">" .. p.page .. "</small>"
]]}

---

## Berikut adalah daftar link yang sudah dimention tapi belum ada halamannya

>**danger** Cepet bikin!
>${query[[
  from p = index.aspiringPages()
  select "- <i style=\"color:#c22\">" .. p.name .. "</i> — <small style=\"color:#ffa\">[[" .. p.page .. "|" .. p.page .. "]]</small>"
where not string.startsWith(p.name, "button")
where not string.startsWith(p.name, "value")
]]}

---

## Berikut adalah daftar link yang sudah dimention tapi masih draft

${query[[
  from p = index.tag "draft"
  select "- " .. p.name .. "         [[" .. p.name .. "]]" 
]]}
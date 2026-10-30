---
    status: draft
    pageDecoration:
      icon: check
      tree:
        priority: 0
---
# List of Queries

>**warning** Berikut adalah daftar link yang sudah dimention tapi masih draft
>${query[[
  from p = index.tag "draft"
  select "- " .. p.name .. "         [[" .. p.name .. "]]" 
]]}
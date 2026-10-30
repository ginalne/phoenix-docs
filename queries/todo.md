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

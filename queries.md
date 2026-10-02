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

## Berikut adalah daftar link tapi halamannya masih kosong

>**danger** bahaya
>${query[[
  from p = index.aspiringPages()
  select "- <i style=\"color:#a00\">" .. p.name .. "</i> — <small style=\"color:#ffa\">[[" .. p.page .. "|" .. p.page .. "]]</small>"
]]}

---

${query[[
  from tags.page select _.text
]]}

## Attachment Yatim
${orphanAttachmentsLinks()}

---

## Halaman Yatim

${orphanPages()}

---

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
  select templates.taskItem(p) .. " — " .. p.page
]]}

---

## Berikut adalah daftar link tapi halamannya masih kosong

${query[[
  from p = index.aspiringPages()
  select "- [[" .. p.name .. "]] " .. p.page
]]}

## Halaman Yatim

${orphanPages()}

## Aspiring Page
${query[[
  from tags.aspiring-page
  select { Halaman = "[[" .. _.name .. "]]" }
  render "table"
]]}

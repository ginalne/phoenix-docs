# List of Queries

## Berikut adalah daftar TODO
${query[[from index.tasks(_) where _.page != "index" select templates.taskItem(_)]]}

## Berikut adalah daftar link tapi halaman kosong
${query[[
  from p = index.aspiringPages()
  select "- [[" .. p.name .. "]]"
]]}

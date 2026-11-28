---
    status: draft
    pageDecoration:
      icon: check
      tree:
        priority: 0
---
# List of Queries

## Sudah dikerjakan
>${query[[
  from p = index.contentPages()
  where string.startsWith(p.name, "Blog") and not table.includes(p.tags, "draft")
  select "- [[" .. p.name .. "|" .. p.name .. "]]"
]]}

## Akan dikerjakan
>${query[[
  from p = index.tag "draft"
  where string.startsWith(p.name, "Blog")
  select "-    [[" .. p.name .. "]]" 
]]}
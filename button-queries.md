---
  tags: meta/Library
---


## mentioned button

${query[[
  from p = index.tag "button"
  select "- " .. p.name .. " <div style=\"padding:0rem 10rem\">[[" .. p.name .. "]]</div>" 
]]}

## mentioned but not exists button

${query[[
  from p = index.aspiringPages()
  select "- <i style=\"color:#faa\">" .. p.name .. "</i> — <small style=\"color:#ffa\">[[" .. p.page .. "|" .. p.page .. "]]</small>"
  where string.startsWith(p.name, "button")
]]}
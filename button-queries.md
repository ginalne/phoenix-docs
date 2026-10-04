---
  tags: meta/Library
---


${query[[from index.tag "button" select name, title]]}

${query[[
from index.tag "button" 
  select "- <i style=\"color:#c22\">" .. p.name .. "</i> — <small style=\"color:#ffa\">[[" .. p.page .. "|" .. p.page .. "]]</small>"]]
}

${query[[
  from p = index.aspiringPages()
  select "- <i style=\"color:#c22\">" .. p.name .. "</i> — <small style=\"color:#ffa\">[[" .. p.page .. "|" .. p.page .. "]]</small>"
  where string.startsWith(p.name, "button")
]]}
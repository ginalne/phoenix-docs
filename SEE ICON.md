---
  tags: meta/Library
  
---


>**success**mentioned button
>${query[[
  from p = index.tag "button"
  select "- " .. p.name .. "         [[" .. p.name .. "]]" 
]]}

>**danger** mentioned button but not exists
>${query[[
  from p = index.aspiringPages()
  select "- <i style=\"color:#faa\">[[" .. p.name .. "]]</i> — <small style=\"color:#ffa\">[[" .. p.page .. "|" .. p.page .. "]]</small>"
  where string.startsWith(p.name, "button")
]]}

>**success**mentioned mode
>${query[[
  from p = index.tag "mode"
  select "- " .. p.name .. "         [[" .. p.name .. "]]" 
]]}

>**danger** mentioned mode but not exists
>${query[[
  from p = index.aspiringPages()
  select "- <i style=\"color:#faa\">" .. p.name .. "</i> — <small style=\"color:#ffa\">[[" .. p.page .. "|" .. p.page .. "]]</small>"
  where string.startsWith(p.name, "mode")
]]}


>**success**mentioned field
>${query[[
  from p = index.tag "field"
  select "- " .. p.name .. "         [[" .. p.name .. "]]" 
]]}

>**danger** mentioned field but not exists
>${query[[
  from p = index.aspiringPages()
  select "- <i style=\"color:#faa\">[[" .. p.name .. "@" ..  ""]]</i> — <small style=\"color:#ffa\">[[" .. p.page .. "|" .. p.page .. "]]</small>"
  where string.startsWith(p.name, "field")
]]}



$${template.each(query\[\[ from index.tag "task" where page == "Tasks" and deadline > date.today('%Y-%m-%d') and deadline != nil and done == false order by deadline limit 6\]\], template.new\[==\[ \* \[${state}\] \*\*${custom.dayOfDate(deadline)}\*\* \_${name}\_ ${custom.concatenateTags(\_.tags)} | \[\[${ref}\]\] \]==\] )}

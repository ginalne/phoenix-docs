# Berikut adalah daftar minta tolong...

${query[[from index.tasks("help") select templates.taskItem(_)]]}

# Berikut adalah daftar halaman kosong
${query[[from index.tasks(_) where _.page != "index" select templates.taskItem(_)]]}

Berikut adalah daftar halaman kosong
${query[[from index.tag "empty" select templates.taskItem(_)]]}

${query[[from index.pages where _.text =~ "#empty" select _.name]]}

${query[[from index.tag "empty" select _.name]]}
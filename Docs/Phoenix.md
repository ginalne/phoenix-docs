---
    name: Library/myuser/My Library
    tags: meta/library
---

```space-lua
config.set("frontmatterFolding", {
  foldByDefault = "never",
})
```

This implements my super awesome hello world library!

```space-lua
config.set("frontmatterFolding", {
  foldByDefault = "always",
})

command.define {
  name = "Hello world",
  run = function()
    editor.flashNotification "Hello world!"
  end
}
```

  
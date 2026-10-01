---
  tags: meta/library
---
#meta

This page holds configuration for your SilverBullet space. See [[^Library/Std/Config]] for all options and defaults.

Run ${widgets.commandButton "System: Reload"} to reload.

## User configuration
Anything you add to the block below is yours, edit freely.

```space-lua
-- Add custom configuration here, e.g.:
-- config.set("shortWikiLinks", false)
```

## Managed by the Configuration Manager
The block below is maintained by the ${widgets.commandButton("Configuration Manager", "Configuration: Open")}. Prefer editing it through the UI, although simple hand edits should survive.

```space-lua
-- managed-by: configuration-manager
config.set("markdownPrettify.emphasisMarker", "_")
```

```space-style
a.christmas-decoration {
  background-color: #b4e46e;
}

body.christmas-decoration #sb-top {
  background-color: #b4e46e;
}

.cm-tooltip-autocomplete li.christmas-decoration {
  background-color: #b4e46e;
}

.sb-result-list .sb-option.christmas-decoration {
  background-color: #b4e46e;
}
```
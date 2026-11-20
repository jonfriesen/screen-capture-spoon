# ScreenCapture

A [Hammerspoon](https://www.hammerspoon.org/) Spoon that binds hotkeys to macOS’s native `/usr/sbin/screencapture` tool.

## Install and configure

Copy the `ScreenCapture.spoon` folder into `Spoons/` inside your Hammerspoon configuration directory (usually `~/.hammerspoon/Spoons/`). Add this to your Hammerspoon `init.lua`, then reload the configuration:

```lua
local modifiers = { "ctrl", "alt", "cmd" }
hs.loadSpoon("ScreenCapture"):bindHotkeys({
    captureSelection = { modifiers, "4" },
    captureSelectionToClipboard = { modifiers, "5" },
    captureOptions = { modifiers, "6" },
})
```

| Hotkey | Action |
| --- | --- |
| Control–Option–Command–4 | Select an area and save it as a PNG on the Desktop. |
| Control–Option–Command–5 | Select an area and copy the screenshot to the clipboard instead of saving a file. |
| Control–Option–Command–6 | Open the macOS Screenshot toolbar for screenshot and screen recording options. |

The selection-to-file mode names the PNG `Screen Capture at YYYY-MM-DD-HH:MM:SS.png` using UTC.

## macOS permissions

- If capture is blocked or macOS prompts for permission, allow Hammerspoon under **System Settings → Privacy & Security → Screen & System Audio Recording** (called **Screen Recording** on older macOS versions). If prompted, quit and reopen Hammerspoon.
- If the hotkeys do not respond, check that Hammerspoon is enabled under **System Settings → Privacy & Security → Accessibility** and that the key combinations are not already in use.

## Build the install ZIP

From the repository root, run:

```sh
git archive --format=zip --prefix=ScreenCapture.spoon/ \
  -o ../ScreenCapture.spoon.zip HEAD init.lua README.md LICENSE
```

## License

Copyright 2024 Jon Friesen. Licensed under the [Apache License 2.0](LICENSE).

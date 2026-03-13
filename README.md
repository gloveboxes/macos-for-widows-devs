# macOS Tips and Tricks for Windows Users

A practical guide for developers making the switch from Windows to macOS.

## Key Differences to Know First

Before diving into settings, here are the fundamental mental model shifts:

| Windows | macOS |
|---------|-------|
| <kbd>Ctrl</kbd> | <kbd>Cmd</kbd> (for most shortcuts) |
| <kbd>Alt</kbd> | <kbd>Option</kbd> |
| <kbd>Backspace</kbd> | <kbd>Delete</kbd> — use <kbd>Fn+Delete</kbd> for forward delete |
| Task Manager | Activity Monitor |
| File Explorer | Finder |
| Start Menu / search | Spotlight (<kbd>Cmd+Space</kbd>) |

> **Important:** Closing a window (clicking the red ×) does **not** quit the app on macOS — the app keeps running in the Dock. Use <kbd>Cmd+Q</kbd> to fully quit.

## System Settings

### Desktop & Dock

- Enable **Minimize windows to application icon** — keeps the Dock uncluttered
- Reduce Dock size and enable **Auto-hide/show**

### Menu Bar

- Clock → show date and time only
- Deselect Spotlight (redundant once you learn <kbd>Cmd+Space</kbd>)
- Add Weather widget

### Keyboard

Enable function keys by default — recommended for VS Code and other dev tools:

**System Settings → Keyboard → Keyboard Shortcuts → Function Keys → Use F1, F2, etc. as standard function keys**

#### Essential Keyboard Shortcuts

| Action | Shortcut |
|--------|----------|
| Spotlight (app launcher + search) | <kbd>Cmd+Space</kbd> |
| Switch between apps | <kbd>Cmd+Tab</kbd> |
| Switch windows within same app | <kbd>Cmd+`</kbd> |
| Quit app (fully) | <kbd>Cmd+Q</kbd> |
| Hide app | <kbd>Cmd+H</kbd> |
| Force quit | <kbd>Cmd+Option+Esc</kbd> |
| Close window | <kbd>Cmd+W</kbd> |
| Full-screen screenshot | <kbd>Cmd+Shift+3</kbd> |
| Area screenshot | <kbd>Cmd+Shift+4</kbd> |
| Screenshot options panel | <kbd>Cmd+Shift+5</kbd> |
| Forward delete (Windows Backspace) | <kbd>Fn+Delete</kbd> |
| Toggle hidden files in Finder (eg .git folder) | <kbd>Cmd+Shift+.</kbd> |

### Mouse & Scrolling

Windows users often find macOS scroll direction counterintuitive when using a mouse.

- **Natural scrolling** matches trackpad feel but feels reversed on a traditional mouse
- **Best solution with a Logitech mouse:** Use [Logi Options+](https://www.logitech.com/en-au/software/options.html) to set per-device scroll direction independent of the trackpad
- **No Logitech mouse?** [Scroll Reverser](https://pilotmoon.com/scrollreverser/) is a free utility that lets you invert scroll direction for mice and trackpads independently

## Finder (File Explorer Equivalent)

From the **View** menu, enable:

- **Show Toolbar**
- **Show Path Bar**
- **Show Status Bar**

### Quick Look

Press <kbd>Space</kbd> on any file in Finder for an instant preview — images, PDFs, videos, text files — without opening an app.

### Add VS Code to Finder Toolbar

Drag a folder or file directly onto the VS Code icon in the toolbar to open it instantly:

1. Install VS Code
2. In Finder, navigate to **Applications**
3. press and hold <kbd>cmd</kbd> and drag the VS Code icon in Applications folder ad **drag it onto the Finder toolbar**

### Show Hidden Files

Press <kbd>Cmd+Shift+.</kbd> in Finder to toggle hidden files (dotfiles, `.git` folders, etc.).

### Disable Sidebar Tags

**Finder → Settings → Sidebar → uncheck Recent Tags**

### Set Default Folder for New Finder Windows

**Finder → Settings → General → New Finder windows show** — select your preferred folder (e.g. your `GitHub` folder).

### Set Search Scope to Current Folder

**Finder → Settings → Advanced → When performing a search → Search the Current Folder**

## Window Management

macOS has a key distinction from Windows: **apps and windows are separate concepts**. If you are familiar with Ubuntu and Mint Linus then it works in a similar way.

- An app can have multiple windows — e.g. VS Code can have several project windows open simultaneously
- <kbd>Cmd+Tab</kbd> switches between **apps**, not windows
- <kbd>Cmd+`</kbd> (backtick) switches between **windows of the same app** — very useful for VS Code, Word, browsers, etc.

### Window Tips

- **Snap windows:** Hover over the green full-screen button, or hold <kbd>Option</kbd> and drag a window to the left or right edge
- **Resize snapped windows:** Grab the divider between two snapped windows and drag
- **Hide vs Minimize:** Prefer <kbd>Cmd+H</kbd> to hide over clicking minimize — hidden apps integrate better with <kbd>Cmd+Tab</kbd>

### Window Management Apps

For a PowerToys FancyZones equivalent:

- [Magnet](https://apps.apple.com/au/app/magnet/id441258766?mt=12) — App Store, paid but polished
- [Rectangle](https://github.com/rxhanson/Rectangle) — free and open source

### Mission Control

Press <kbd>F3</kbd> or swipe up with three fingers on the trackpad to see all open windows across all apps — equivalent to Task View (<kbd>Win+Tab</kbd>) on Windows.

## Terminal

macOS ships with **zsh** as the default shell (analogous to PowerShell). The built-in Terminal app is at Applications → Utilities → Terminal.

### Customise Terminal Exit Behaviour

**Terminal → Settings → Shell → When the shell exits** → set to **Close if the shell exited cleanly**

### Homebrew — Essential Package Manager

[Homebrew](https://brew.sh) is the `winget`/`apt` of macOS. Install it first:

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Then install tools like:

```sh
brew install git node python pyenv
```

Update brew catalog:

```sh
brew update
```

Upgrade installed brew apps:

```sh
brew upgrade
```

## Developer Tools

### Docker Desktop

Download [Docker Desktop for Mac](https://docs.docker.com/desktop/setup/install/mac-install/) — choose **Apple Silicon** if on an M-series Mac. During installation you'll be prompted to also install **Rosetta** for x86/x64 emulation — accept it.

### Running Local LLMs

- [Ollama](https://ollama.com) — CLI-based, great for scripting and API use
- [LM Studio](https://lmstudio.ai) — GUI with support for MLX-optimised models, which run ~20% faster than GGUF models on Apple Silicon — preferred for M-series Macs

## Utilities

### Clipboard Manager — Flycut

[Flycut](https://apps.apple.com/au/app/flycut-clipboard-manager/id442160987?mt=12) provides persistent clipboard history — far more accessible than the built-in clipboard.

**Setup:**

1. Add Flycut to **System Settings → Privacy & Security → Accessibility**
2. Customise icon: **Flycut → Preferences → Appearance → White Scissors**

**Usage:** <kbd>Cmd+C</kbd> to copy, <kbd>Shift+Cmd+V</kbd> to cycle through clipboard history

### Screenshots — Teampaper Snap

The built-in screenshot tool works, but [Teampaper Snap](https://apps.apple.com/au/app/teampaper-snap/id1199502670?mt=12) is more flexible and efficient.

**Recommended for Windows users:** Map the shortcut to <kbd>Shift+Cmd+S</kbd> to match Windows muscle memory.

**Setup:**

1. **Teampaper → Settings** — set shortcut to <kbd>Shift+Cmd+S</kbd>
2. Enable **Open at Mac Startup**

### Monitor Brightness & Volume — MonitorControl

Equivalent to Twinkle Tray on Windows, for controlling non-Apple external monitors.

- [MonitorControl](https://github.com/MonitorControl/MonitorControl) — full version (brightness + volume), install via `.dmg`
- [MonitorControl Lite](https://apps.apple.com/au/app/monitorcontrol-lite/id1595464182?mt=12) — App Store version (brightness only)

## Managing Login Items (Startup Apps)

**System Settings → General → Login Items & Extensions**

Ensure these start automatically at login:

- Flycut
- Teampaper Snap
- MonitorControl
- Rectangle or Magnet (if using)


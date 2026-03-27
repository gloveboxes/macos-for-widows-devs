# macOS Tips and Tricks for Windows Users

A practical guide for developers making the switch from Windows to macOS.

## Key Differences to Know First

Before diving into settings, here are the fundamental mental model shifts:

| Windows              | macOS                                                           |
| -------------------- | --------------------------------------------------------------- |
| <kbd>Ctrl</kbd>      | <kbd>Cmd</kbd> (for most shortcuts)                             |
| <kbd>Alt</kbd>       | <kbd>Option</kbd>                                               |
| <kbd>Backspace</kbd> | <kbd>Delete</kbd> — use <kbd>Fn+Delete</kbd> for forward delete |
| Task Manager         | Activity Monitor                                                |
| File Explorer        | Finder                                                          |
| Start Menu / search  | Spotlight (<kbd>Cmd+Space</kbd>)                                |

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

| Action                                         | Shortcut                  |
| ---------------------------------------------- | ------------------------- |
| Spotlight (app launcher + search)              | <kbd>Cmd+Space</kbd>      |
| Switch between apps (eg VS Code, Terminal)     | <kbd>Cmd+Tab</kbd>        |
| Switch windows within same app                 | <kbd>Cmd+`</kbd>          |
| Quit app (fully)                               | <kbd>Cmd+Q</kbd>          |
| Hide app                                       | <kbd>Cmd+H</kbd>          |
| Force quit                                     | <kbd>Cmd+Option+Esc</kbd> |
| Close window                                   | <kbd>Cmd+W</kbd>          |
| Full-screen screenshot                         | <kbd>Cmd+Shift+3</kbd>    |
| Area screenshot                                | <kbd>Cmd+Shift+4</kbd>    |
| Screenshot options panel                       | <kbd>Cmd+Shift+5</kbd>    |
| Forward delete (Windows Backspace)             | <kbd>Fn+Delete</kbd>      |
| Toggle hidden files in Finder (eg .git folder) | <kbd>Cmd+Shift+.</kbd>    |

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

### Open a Terminal in a folder

From the file path at the bottom of Finder, right mouse click on the desired location on the path and select "Open in Terminal".

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

macOS has a key distinction from Windows: **apps and windows are separate concepts**. If you are familiar with Ubuntu and Mint Linux then it works in a similar way.

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

## Productivity apps

- macOS includes free Pages (Word equiv), Numbers (Excel), Keynote (Powerpoint).
- MS Office on macOS is very good, Outlook very good, as is OneDrive and OneNote.

## Microcontroller Dev

For C dev

### Espressif

- Install the [Espressif VS Code](https://marketplace.visualstudio.com/items?itemName=espressif.esp-idf-extension) Extension, and then follow the instructions in the welcome page to install the SDK.
- Limit parallel C compiles to 6 threads. Without this limit, the default -j setting triggers excessive parallelism, which can double build times due to resource contention. Tested on MacBook Pro M3 and M5 Pro models.

### Raspberry Pi Pico

- Install the [Raspberry Pi Pico](https://marketplace.visualstudio.com/items?itemName=raspberry-pi.raspberry-pi-pico) extension, and then follow the instructions in the welcome page to install the SDK.

## Xcode and GitHub Copilot for XCode

1. Install Xcode from App Store
2. Install [GitHub Copilot for Xcode](https://github.com/github/CopilotForXcode) with Brew

    ```sh
    brew install --cask github-copilot-for-xcode
    ```

3. From Intelligence menu, enable "Allow external agents to use Xcode tools
4. As of March 2026, Claude Sonnet 4.6 is a fun experience building your first macOS app.

## Enrolling macOS

See [Enroll your macOS device using the Company Portal app](https://learn.microsoft.com/en-us/intune/intune-service/user-help/enroll-your-device-in-intune-macos-cp)

## Native Apple Container Framework

Installing and using the native Apple **Container CLI** is straightforward on macOS 26 (Tahoe). It follows a similar workflow to Docker but leverages the **Virtualization framework** to run each container in its own isolated, lightweight micro-VM.

Here is the step-by-step guide to installing the tool and running a PostgreSQL instance.

---

## 1. Installation

The CLI tool is currently available as a signed package on GitHub or via Homebrew.

### Option A: Via Homebrew (Recommended)

```bash
brew install container

```

### Option B: Manual Installation

1. Go to the [Apple Container GitHub Releases](https://github.com/apple/container/releases).
2. Download the latest `.pkg` installer (e.g., `container-1.0.0-installer-signed.pkg`).
3. Run the installer and follow the on-screen prompts.

### Step 2: Initialize the System

Once installed, you must start the container service. The first time you run this, it will prompt you to download a **Linux kernel** (usually a Kata-containers-based kernel optimized for Apple silicon).

```bash
container system start

```

> **Note:** When prompted to install the recommended kernel, type `y`. This sets up the environment required to spawn the micro-VMs.

---

## 2. Running PostgreSQL (pgvector)

Because the Apple Container framework uses OCI-compliant images, you can pull the official Postgres image directly from Docker Hub.

### Step 1: Create a Persistent Volume

To ensure your database data isn't lost when the container stops, create a local directory on your Mac to hold the data:

```bash
mkdir -p ~/postgres_data

```

### Step 2: Run the Postgres Container

Use the `run` command. Note that unlike Docker, each container gets its own IP address, but you can still use port mapping to access it via `localhost`.

```bash
container run -d \
  --name my-postgres \
  -e POSTGRES_PASSWORD=mysecretpassword \
  -p 5432:5432 \
  -v ~/postgres_data:/var/lib/postgresql \
  pgvector/pgvector:pg18-trixie

```

**Breaking down the flags:**

- `-d`: Detached mode (runs in the background).
- `--name`: Assigns a friendly name to the container.
- `-e`: Sets environment variables (required for the Postgres password).
- `-p 5432:5432`: Maps the container's port 5432 to your Mac's port 5432.
- `-v`: Mounts your local folder into the container for data persistence.

---

### Enable PG Vector Extension

Even though the image includes the pgvector binaries, you still need to enable the extension within your database. You can do this directly from your terminal:

```bash
container exec -it my-postgres psql -U postgres -c "CREATE EXTENSION IF NOT EXISTS vector;"
```

### Test Extension

Run a quick check to see the pgvector version and ensure the M5 Pro's ARM-based SIMD optimizations (which pgvector uses for distance calculations) are working as expected:

```bash
container exec -it my-postgres psql -U postgres -c "\dx vector"
```

## 3. Managing and Connecting

### Check Status

To see your running container and its dedicated IP address:

```bash
container ls

```

### Connect via CLI

If you want to run `psql` directly inside the container to create tables or check the version:

```bash
container exec -it my-postgres psql -U postgres

```

### Check Logs

If the container fails to start, check the logs for errors:

```bash
container logs my-postgres

```

---

## Key Tips for macOS 26

- **Network Access:** If you cannot connect to `localhost:5432` from a GUI tool (like TablePlus or DBeaver), ensure that **Local Network** access is enabled for the "Container Runtime" in *System Settings > Privacy & Security > Local Network*.
- **Resource Tuning:** If you notice Postgres is slow during heavy indexing, you can increase the VM resources:
`container run --cpus 4 --memory 4g ...`

## Windows on ARM64 with Parallels Desktop

### Python

As at March 2026, recommend Python 3.12 for ARM64.

### Building missing Python wheels on Windows on ARM64

Here is a summary of the "Golden Configuration" for building Python wheels on Windows ARM64.

---

#### 🛠️ Windows ARM64 Python Build Environment

##### 1. The Core Toolchain (Visual Studio)

Standard "Desktop development with C++" isn't enough; you must explicitly add the ARM64 compilers.

- **Install:** [Visual Studio Build Tools 2022](https://visualstudio.microsoft.com/visual-cpp-build-tools/).
- **Required Individual Components:**
  - `MSVC v143 - VS 2022 C++ ARM64 build tools (Latest)`
  - `Windows 11 SDK` (Matches your OS version)
  - `C++ CMake tools for Windows`

##### 2. The "Short-Path" Infrastructure

Windows has a legacy **MAX_PATH (260 characters)** limit. Python builds (like `lupa` or `aiohttp`) create deeply nested temporary folders that easily exceed this.

- **Enable Long Paths (Admin PowerShell):**

    ```powershell
    Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\FileSystem' -Name 'LongPathsEnabled' -Value 1
    ```

- **The Build Scratchpad:** Always keep a top-level directory (e.g., `C:\b`) for temporary build files to keep paths as short as possible.

##### 3. Essential Python Build Tools

Before trying to build complex wheels, ensure your virtual environment has the "Big Three" updated:

```powershell
python -m pip install --upgrade pip setuptools wheel
python -m pip install cython  # Frequently required for C-extensions like Lupa
```

##### 4. The "Successful Build" Workflow

When a standard `pip install` fails with `LNK1104` or "Metadata generation failed," use this sequence:

1. **Redirect Temp Folders:**

    ```powershell
    $env:TEMP = "C:\b"
    $env:TMP = "C:\b"
    ```

2. **Bypass Isolation:** Use `--no-build-isolation`. This forces `pip` to use the compilers and `cython` you already have installed, rather than trying to set up a new (and often broken) temporary environment.
3. **The Command:**

    ```powershell
    pip install <package-name> --no-cache-dir --no-build-isolation
    ```

##### 5. Troubleshooting Cheat Sheet

| Error                 | Probable Cause                 | Fix                                                   |
| :-------------------- | :----------------------------- | :---------------------------------------------------- |
| **LNK1104**           | Path too long or file locked.  | Use `C:\b` and `$env:TEMP`.                           |
| **Rust not found**    | Missing Rust compiler.         | Install [Rustup](https://rustup.rs/) (ARM64 version). |
| **SOABI mismatch**    | Python version too new (3.14). | Downgrade to Python 3.12 or 3.13.                     |
| **Permission Denied** | Misinterpreted `--build` flag. | Use the `$env:TEMP` method instead.                   |

# Windows on ARM64 with Parallels Desktop

## Python

As at March 2026, recommend Python 3.12 for ARM64.

## Building missing Python wheels on Windows on ARM64

Here is a summary of the "Golden Configuration" for building Python wheels on Windows ARM64.

---

### 🛠️ Windows ARM64 Python Build Environment

#### 1. The Core Toolchain (Visual Studio)

Standard "Desktop development with C++" isn't enough; you must explicitly add the ARM64 compilers.

- **Install:** [Visual Studio Build Tools 2022](https://visualstudio.microsoft.com/visual-cpp-build-tools/).
- **Required Individual Components:**
   - `MSVC v143 - VS 2022 C++ ARM64 build tools (Latest)`
   - `Windows 11 SDK` (Matches your OS version)
   - `C++ CMake tools for Windows`

#### 2. The "Short-Path" Infrastructure

Windows has a legacy **MAX_PATH (260 characters)** limit. Python builds (like `lupa` or `aiohttp`) create deeply nested temporary folders that easily exceed this.

- **Enable Long Paths (Admin PowerShell):**

```powershell
Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\FileSystem' -Name 'LongPathsEnabled' -Value 1
```

- **The Build Scratchpad:** Always keep a top-level directory (e.g., `C:\b`) for temporary build files to keep paths as short as possible.

#### 3. Essential Python Build Tools

Before trying to build complex wheels, ensure your virtual environment has the "Big Three" updated:

```powershell
python -m pip install --upgrade pip setuptools wheel
python -m pip install cython   # Frequently required for C-extensions like Lupa
```

#### 4. The "Successful Build" Workflow

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

#### 5. Troubleshooting Cheat Sheet

| Error                  | Probable Cause                  | Fix                                                    |
| :-------------------- | :----------------------------- | :---------------------------------------------------- |
| **LNK1104**            | Path too long or file locked.   | Use `C:\b` and `$env:TEMP`.                            |
| **Rust not found**     | Missing Rust compiler.          | Install [Rustup](https://rustup.rs/) (ARM64 version). |
| **SOABI mismatch**     | Python version too new (3.14). | Downgrade to Python 3.12 or 3.13.                      |
| **Permission Denied** | Misinterpreted `--build` flag. | Use the `$env:TEMP` method instead.                    |

## Guide: Installing Rust & OpenSSL on Windows ARM64

This guide explains how to set up a native ARM64 development environment for Rust and Python packages (like `cryptography`) that require OpenSSL compilation.

---

## 1. Install C++ Build Tools (The Linker)

Rust requires the Microsoft Visual C++ (MSVC) linker to create Windows executables.

1. Download the [Visual Studio Installer](https://visualstudio.microsoft.com/downloads/).
2. Select the workload: **Desktop development with C++**.
3. **CRITICAL:** Under the "Installation details" (right-hand panel), check:
   - **MSVC v143 - VS 2022 C++ ARM64 build tools (Latest)**
   - **Windows 11 SDK** (or latest version available).
4. Install and restart your computer.

---

## 2. Install Rust (Native ARM64)

1. Download **`rustup-init.exe`** from [rustup.rs](https://rustup.rs).
2. Run the installer. It should automatically detect `aarch64-pc-windows-msvc`.
3. Choose **Option 1** (Proceed with default installation).
4. Verify in a new PowerShell window:

```powershell
rustc --version
# Should show: host: aarch64-pc-windows-msvc
```

## 3. Setup vcpkg and OpenSSL

We use vcpkg to compile a native ARM64 version of OpenSSL, which is required for many encryption-based libraries.

Clone the vcpkg repository:

```PowerShell
cd C:\Data\GitHub   # Or your preferred directory
git clone https://github.com/microsoft/vcpkg.git
cd vcpkg
```

Bootstrap the tool:

```PowerShell
.\bootstrap-vcpkg.bat
```

Install OpenSSL for ARM64:

```PowerShell
.\vcpkg.exe install openssl:arm64-windows
```

(This step takes a few minutes as it compiles the source code for your processor).

## 4. Configure Environment Variables

You must tell the Rust compiler where to find the OpenSSL files you just built. Run these in your current PowerShell session:

```PowerShell
# Update the path if you installed vcpkg elsewhere
$vcpkgRoot = "C:\Data\GitHub\vcpkg\installed\arm64-windows"

$env:OPENSSL_DIR = "$vcpkgRoot"
$env:OPENSSL_LIB_DIR = "$vcpkgRoot\lib"
$env:OPENSSL_INCLUDE_DIR = "$vcpkgRoot\include"
```

Note: These variables only last for the current terminal session. If you close PowerShell, you must re-run these three $env lines before compiling again.

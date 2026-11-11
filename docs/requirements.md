# What To Install

TunManager is one portable program. It brings its own libraries and needs no
Python, Node.js, Java, developer tools or package manager on any system. What
it uses from the system is listed here, per platform: what it **needs**, what
the system **usually has already**, and what is **optional** for one feature
only. A feature whose program is missing says so and, where there is one,
offers the official download page; nothing else stops working.

## Every System

| What | Needed for | Notes |
| --- | --- | --- |
| OpenSSH client (`ssh`, `ssh-keygen`) | every tunnel, terminal and key setup | TunManager drives the system's OpenSSH. Check with `ssh -V`. |
| A server you can reach with SSH | everything | Your own server, VPS or relay; TunManager is only the client. |

## Windows

Windows 10 or 11, 64-bit (`amd64`).

| What | Needed? | How to get it |
| --- | --- | --- |
| OpenSSH Client | **needed** | Built in on current Windows. If `ssh -V` fails in PowerShell: Settings > System > Optional features > Add a feature > **OpenSSH Client**. |
| Microsoft Edge WebView2 Runtime | **needed** for app windows | Already on Windows 11 and updated Windows 10. Otherwise install the Evergreen runtime from [Microsoft](https://developer.microsoft.com/microsoft-edge/webview2/). |
| Windows Terminal | optional (Terminal button) | The Terminal button can also use a PowerShell or Command Prompt window. From the Microsoft Store. |
| PuTTY | optional (Terminal with PuTTY) | [putty.org](https://www.putty.org). |
| WinSCP | optional (Open with) | [winscp.net](https://winscp.net). |
| FileZilla | optional (Open with) | [filezilla-project.org](https://filezilla-project.org). |
| rclone and WinFsp | optional (Open with > Mount) | [rclone.org](https://rclone.org/downloads/) and [WinFsp](https://winfsp.dev/rel/). |
| Visual Studio Code with Remote - SSH | optional (Open with) | [code.visualstudio.com](https://code.visualstudio.com). |

Nothing needs administrator rights except installing those programs.

## Linux (desktop preview)

64-bit (`amd64`) desktop with GTK 3, for example Ubuntu 22.04 or later,
Debian 12 or later, Fedora 38 or later.

| What | Needed? | Ubuntu / Debian | Fedora | Arch |
| --- | --- | --- | --- | --- |
| OpenSSH client | **needed** | `openssh-client` | `openssh-clients` | `openssh` |
| GTK 3 | **needed** (window) | `libgtk-3-0` (`libgtk-3-0t64` on 24.04+) | `gtk3` | `gtk3` |
| WebKitGTK 4.1 | **needed** (window, app windows) | `libwebkit2gtk-4.1-0` | `webkit2gtk4.1` | `webkit2gtk-4.1` |
| A tray (StatusNotifier) host | for the tray icon | Ubuntu: built in. Plain GNOME: the **AppIndicator and KStatusNotifierItem Support** extension. KDE, Xfce, Cinnamon: built in. | | |
| A notification service | for notifications | Every desktop has one. `notify-send` (`libnotify-bin`) is used when no window runs. | `libnotify` | `libnotify` |
| Secret Service (GNOME Keyring or KWallet) | to remember passwords | Usually running; `gnome-keyring` | `gnome-keyring` | `gnome-keyring` |
| `paplay` or `aplay` | notification sounds | `pulseaudio-utils` (PipeWire provides it) or `alsa-utils` | `pulseaudio-utils` | `libpulse` |
| `xdg-open` / `gio` | opening links, files, folders | `xdg-utils` (usually installed) | `xdg-utils` | `xdg-utils` |
| A terminal emulator | Terminal button | the default terminal (`x-terminal-emulator`), GNOME Terminal, Konsole or xterm, or a command you choose | | |
| `zenity` or `kdialog` | questions from the command line when no window runs | `zenity` | `zenity` | `zenity` |
| rclone and FUSE 3 | optional (Open with > Mount) | `rclone fuse3` | `rclone fuse3` | `rclone fuse3` |
| `ssh-agent` | optional (FileZilla with a managed key) | in `openssh-client` | | |
| VS Code, FileZilla | optional (Open with) | from their sites or the distribution | | |

One command for the usual Ubuntu or Debian desktop:

```bash
sudo apt install openssh-client libgtk-3-0 libwebkit2gtk-4.1-0 xdg-utils libnotify-bin
```

On Ubuntu 24.04 and later the GTK package is `libgtk-3-0t64`. On Fedora:

```bash
sudo dnf install openssh-clients gtk3 webkit2gtk4.1 xdg-utils libnotify
```

## macOS (desktop preview)

macOS 12 Monterey or later, Intel or Apple Silicon (one universal app).

| What | Needed? | How to get it |
| --- | --- | --- |
| OpenSSH client | **needed**, built in | Nothing to install. |
| WebKit, Keychain, notifications | **needed**, built in | Nothing to install. Allow TunManager's notifications once when macOS asks (it shows as **TunManager** and **TunManager Notifier** in System Settings > Notifications). |
| Terminal, iTerm2 or PuTTY | Terminal button | Terminal is built in; [iTerm2](https://iterm2.com) or PuTTY are used when you choose them. |
| macFUSE or FUSE-T, and rclone | optional (Open with > Mount) | [macFUSE](https://osxfuse.github.io) or [FUSE-T](https://www.fuse-t.org); [rclone](https://rclone.org/downloads/). |
| VS Code, FileZilla | optional (Open with) | From their sites. |

TunManager does **not** need the Xcode Command Line Tools, Homebrew or Python.
If macOS ever offers to install the "command line developer tools", that came
from another program typing `python3`, `git` or `clang`; TunManager works
without them.

The preview is not signed yet: open it the first time with right-click >
**Open** (see [Unsigned Build Safety](unsigned-builds.md)).

## Checking A Computer

```bash
ssh -V
```

On Linux, this also shows whether the window's libraries are present:

```bash
ldd ./tunnelm-desktop | grep "not found"
```

No output means nothing is missing. `tunnelm doctor` checks the
configuration and OpenSSH.

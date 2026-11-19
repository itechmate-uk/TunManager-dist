# Platform Support

What each system needs installed (usually nothing) is in
[What To Install](requirements.md).

## Windows

Windows `amd64` is the current complete desktop release. Its archive contains:

- `tunnelm.exe`: no-console manager and tray application;
- `tunnelm-cli.exe`: PowerShell/CMD diagnostics;
- `tunnelm-webview.exe`: no-console WebView2 diagnostic; and
- `tunnelm-webview-cli.exe`: console WebView2 diagnostic.

The desktop supports manager/tray lifecycle, WebView2 app windows,
notifications, sounds, credential vault, file pickers, autostart, remote
services, and Local File Bridge workflows.

## Linux

Since v0.1.56 the Linux manager window is the release "TunManager desktop
VERSION" (`tunnelm-desktop_VERSION_linux_amd64.tar.gz`, amd64, WebKitGTK 4.1):
the same window and tabs as on Windows, a tray icon (GNOME needs the
AppIndicator extension; Ubuntu has it on), app windows, notifications,
autostart, the system keyring, Open with (rclone mount, FileZilla, the file
manager, VS Code) and in-place updates. Not yet: DEB/RPM, AppImage or Flatpak
packages.

The `tunnelm_*` Linux `amd64` and `arm64` archives are command builds: they
validate configuration and run the CLI workflows without a window.

## macOS

Since v0.1.56 the macOS manager window is the same release
(`tunnelm-desktop_VERSION_macos_universal.zip`, macOS 12 or later, Apple
silicon and Intel): TunManager.app with the same window and tabs, a menu bar
icon, app windows, notifications, the Keychain and in-place
updates. It is signed ad hoc, not with an Apple Developer ID, so the first
start asks you to allow it in System Settings > Privacy & Security. Not yet: a
signed installer; rclone mounts need macFUSE or FUSE-T.

The `tunnelm_*` macOS Intel and Apple Silicon archives are command builds.

Cross-compilation and CI prove that code builds; they do not prove desktop
behavior. macOS release certification requires a real Mac because WebView,
Keychain, notification permission, menu-bar, resume, and packaging behavior
depend on macOS services. Standard-user hosted Mac access is sufficient for
ordinary application QA. Admin/root access is needed later for privileged
package-install and system-integration scenarios.

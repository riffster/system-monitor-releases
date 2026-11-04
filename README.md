# System Monitor releases

Installers and the update feed for **System Monitor**, a small always-on desktop widget that
shows anything worth attention, every temperature your PC reports, memory, battery and
storage health in one 330 px view. **Windows and Linux.**

Get the files from the [latest release](../../releases/latest). Installed copies update
themselves: they check this repo's [`latest.json`](../../releases/latest/download/latest.json),
tell you when a new version is out, and install it when you choose.

## Windows 10 / 11 (x64)

Run `SystemMonitor_<version>_x64-setup.exe`. It installs per-machine (one administrator prompt) and sets up:

- **System Monitor**, the widget (starts with Windows in compact mode; the × hides it to the tray).
- **System Monitor Sensors**, a background service that reads the hardware sensors.
- **PawnIO**, a signed open-source driver the sensor library uses for CPU, motherboard and
  memory temperatures, installed only if it isn't already there.

> The installer isn't code-signed yet, so Windows SmartScreen may say *"Windows protected your
> PC"*. Choose **More info → Run anyway**.

Uninstall: Settings → Apps → System Monitor. PawnIO stays, because other hardware tools share
it; remove it separately from Settings → Apps if you like.

## Linux (x86-64)

| Distribution | Install |
|---|---|
| Ubuntu 22.04+, Debian 12+, Linux Mint 21+, Pop!_OS | `sudo apt install ./SystemMonitor_<version>_amd64.deb` |
| Fedora 40+ | `sudo dnf install ./SystemMonitor-<version>-1.x86_64.rpm` |
| openSUSE Tumbleweed / Leap 15.6 | `sudo zypper install ./SystemMonitor-<version>-1.x86_64.rpm` |

The package installs the widget (in your app launcher as **System Monitor**), the
`system-monitor-sensors` systemd service (enabled and started for you), and `smartmontools`
for drive health. Updates install from the widget with one password prompt.

- The tray icon needs an AppIndicator host: built into Ubuntu, KDE Plasma, Cinnamon and most
  desktops; on stock GNOME add the *AppIndicator and KStatusNotifierItem Support* extension.
- On Wayland the widget can't keep itself on top or remember its position (the compositor decides).
- NVIDIA GPU temperatures need NVIDIA's own driver; AMD and Intel work with the built-in drivers.
- To see everything the service reads: `sudo /usr/lib/system-monitor/system-monitor-sensors --dump --raw`.

Uninstall: `sudo apt remove system-monitor` or `sudo dnf remove system-monitor`.

This repository holds releases only.

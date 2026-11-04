# System Monitor releases

Installers and the update feed for **System Monitor**, a small always-on Windows widget that
shows anything worth attention, every temperature your PC reports, memory, battery and
storage health in one 330 px view.

## Install

Download `SystemMonitor_<version>_x64-setup.exe` from the [latest release](../../releases/latest)
and run it. It installs per-machine (one administrator prompt) and sets up:

- **System Monitor**, the widget (starts with Windows in compact mode; the × hides it to the tray).
- **System Monitor Sensors**, a background service that reads the hardware sensors.
- **PawnIO**, a signed open-source driver the sensor library uses for CPU, motherboard and
  memory temperatures, installed only if it isn't already there.

Windows 10 or 11, x64. Installed copies update themselves: they check this repo's
[`latest.json`](../../releases/latest/download/latest.json) and offer new versions, which you
choose when to install.

> The installer isn't code-signed yet, so Windows SmartScreen may say *"Windows protected your
> PC"*. Choose **More info → Run anyway**.

## Uninstall

Settings → Apps → System Monitor → Uninstall. This removes the widget, the service and the
sign-in entry. PawnIO stays, because other hardware tools share it; remove it separately
from Settings → Apps if you like.

This repository holds releases only.

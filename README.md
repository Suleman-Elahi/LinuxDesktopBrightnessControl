
# Simple Brightness Control (Debian)

A lightweight, dependency-free system tray slider to control external monitor brightness on Debian 13 (Trixie) and other Linux distributions.

Designed for desktop monitors which often lack native software brightness sliders, this tool lets you dim external displays beyond their hardware minimum limits. By using software-based rendering to darken the output, it provides a much dimmer, softer viewing experience—perfect for late-night usage or users with light sensitivity who need to reduce eye strain.

It uses `xrandr` for the backend and `zenity` for the GUI, meaning no heavy Python or GTK/Qt compilation is required.

<img src ="Screenshot_20251227_161854.png">

## Features
- 🚀 **Zero Dependencies**: Uses standard tools pre-installed on most Debian systems (`bash`, `awk`, `xrandr`, `zenity`).
- 🎚️ **Live Updates**: Brightness changes immediately as you drag the slider.
- 🖥️ **Desktop Integration**: Installs as a native application that can be pinned to your Panel, Dock, or System Tray.

## Prerequisites
Most Debian installations have these by default. You can verify with:
```bash
sudo apt update
sudo apt install xrandr zenity
```

## Installation

### Option 1: Install via .deb (Recommended)
Go to the **Releases** page (or download the .deb file from this repo) and run:

```bash
sudo apt install ./brightness-control-1.0.deb
```
Once installed, search for **"Brightness Control"** in your application menu and pin it to your favorites/taskbar.

### Option 2: Manual Install
1. Download `brightness-slider` and make it executable:
   ```bash
   chmod +x brightness-slider
   ```
2. Run it directly:
   ```bash
   ./brightness-slider
   ```

## Configuration (Important!)
By default, this script targets the **DP-3** output (DisplayPort). If your monitor is plugged into HDMI or a different port, you need to edit the script.

1. **Find your monitor name:**
   ```bash
   xrandr | grep " connected"
   ```
   *Example output: `HDMI-1 connected primary...`*

2. **Edit the script:**
   If you installed via `.deb`, edit the installed file:
   ```bash
   sudo nano /usr/local/bin/brightness-slider
   ```
   Change `DP-3` to your monitor name (e.g., `HDMI-1` or `eDP-1`).

## Usage
1. Click the **Brightness Control** icon in your panel.
2. A slider window will appear.
3. Drag to adjust brightness.
4. Close the window when finished.

## Uninstallation
To remove the package:
```bash
sudo apt remove brightness-control
```

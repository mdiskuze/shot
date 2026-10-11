# Shot

A screenshot and annotation tool for GNOME Shell (Wayland) and Cinnamon (X11). Shot freezes all monitors at once, lets you pick a region, a window or a monitor, draw on the frozen screen, and then copy, save, pin, upload or OCR the result. It also records a region to GIF or WebP and captures content taller than the screen by scrolling it.

This repository holds the signed release files and the issue tracker. The source code is not published here.

## Supported desktops

- GNOME Shell 45 to 50
- Cinnamon 6 (Linux Mint 22.x)

The installer uses `apt`, so it is meant for Debian, Ubuntu and Linux Mint.

## Install

Download the `shot-install-<version>` file from the latest release, make it executable and run it:

```
chmod +x shot-install-<version>
./shot-install-<version>
```

The installer detects the desktop, installs the optional programs Shot uses (`ffmpeg`, `tesseract-ocr`, `zenity` and, on Cinnamon, a few more) and makes Shot the screenshot tool. It backs up everything it changes, and `./shot-install-<version> restore` puts the previous state back.

## Updates

Releases are signed. Shot checks for a newer release in its settings window and installs it only after the signature has been verified.

## Reporting a problem

Open an issue here. Please include the Shot version, the desktop (GNOME Shell or Cinnamon and its version) and the steps that lead to the problem.

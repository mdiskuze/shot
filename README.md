# Shot

A screenshot and annotation tool for GNOME Shell (Wayland) and Cinnamon (X11). Shot freezes all monitors at once, lets you pick a region, a window or a monitor, draw on the frozen screen, and then copy, save, pin, upload or OCR the result. It also records a region to GIF or WebP, records a procedure click by click (with the option to cover personal data), captures content taller than the screen or wider by scrolling it, and has a guided tour of all of it.

This repository holds the signed release files and the issue tracker. The source code is not published here.

## Supported desktops

- GNOME Shell 45 to 50 (Wayland or X11)
- Cinnamon 6 (Linux Mint 22.x)

The installer uses `apt`, so it is meant for Debian, Ubuntu and Linux Mint. In the commands below `<version>` is the number of the latest release.

## Install

You need Debian, Ubuntu or Linux Mint with GNOME Shell 45 to 50 or Cinnamon 6, `python3` (3.8 or newer, the installer says so at once when it is missing) and `ssh-keygen` (the OpenSSH client).

1. Download `shot-<version>-linux.sh` (the installer) and `shot-<version>-linux.sh.sig` (its signature) from the files below.
2. Open a terminal in the folder with the download (a double click only opens the file in an editor) and run `sh shot-<version>-linux.sh`. If programs Shot uses are missing (`ffmpeg`, `tesseract-ocr` with Czech, `zenity`, on Cinnamon also `gjs`, GTK 4, libadwaita and `xdotool`), the installer installs them with `sudo apt` and `sudo` asks for your password once. Shot works without them, only the feature that needs one says what is missing.
3. GNOME: the first install needs one log out and log in, because GNOME Shell finds a new extension only at login. An update after that needs nothing, Shot loads the new version by itself. Cinnamon: Shot is on at once, after an update restart Cinnamon (Ctrl+Alt+Esc, the windows stay).

Print then opens Shot. If you have Shot 1.8 or older, the installer moves it to its new name (`shot@mdiskuze.github.io`) and keeps your settings, on GNOME that needs one log out and log in because GNOME finds the renamed extension only at login. Later updates come from Settings > About inside Shot, which verifies the signature before it installs.

## What the installer changes

- It stops the screenshot tool you use now (Flameshot, ksnip, Shutter, Spectacle, xfce4-screenshooter) and switches off its autostart, its keys and its panel launcher. Nothing of it is removed.
- It takes the keys for screenshots (Print and the others Shot uses) from the desktop. Your own shortcuts stay, only without the key.
- It copies Shot to `~/.local/share/gnome-shell/extensions/shot@mdiskuze.github.io` (Cinnamon: `~/.local/share/cinnamon/extensions/...` and the applet), `shot-cli` to `~/.local/bin` and `shot.desktop` to `~/.local/share/applications`.
- Everything it changes it backs up first, to `~/.local/share/shot/install`.
- Every run writes a report (what it found, changed, installed and backed up, the steps and any error, without your user name or host name) to `~/.local/share/shot/install-reports`. `sh shot-<version>-linux.sh report` prints the last one. Attach it to an issue when something goes wrong.

## Uninstall

Run `sh shot-<version>-linux.sh restore`. It puts back every setting, file and launcher from the backup, removes Shot and the packages the installer added, starts the tool it stopped, and then checks each change against the backup. The report of the restore says whether the system is as it was before the install, and lists any difference. `--purge` also removes Shot's own settings, cache and history. Screenshots you saved are never touched.

## Files

- `shot-<version>-linux.sh` is the installer (a shell script with a Python zip application inside, for Debian, Ubuntu and Linux Mint), `shot-<version>-linux.sh.sig` its signature. The signature is made with `ssh-keygen -Y sign`, the public key is `release-key.pub` in the extension folder of an installed Shot. To check it by hand: `ssh-keygen -Y verify -f release-key.pub -I shot-release -n shot-release -s shot-<version>-linux.sh.sig < shot-<version>-linux.sh`.

## Updates

Releases are signed. Shot checks for a newer release once a day in the background (a switch in Settings > About turns it off, only GitHub is asked and nothing is sent) and installs it from Settings > About after the signature has been verified.

## Reporting a problem

Open an issue here. Please include the Shot version, the desktop (GNOME Shell or Cinnamon and its version), the steps that lead to the problem and, for an installation problem, the report of the installer (`sh shot-<version>-linux.sh report`).

---
date: 2020-06-07
description: "Automatically switch macOS Terminal theme at sunrise and sunset"
externalUrl: "https://github.com/cboone/diurnal-terminal"
title: "Diurnal Terminal"
---

Automatically switch macOS Terminal.app theme at sunrise and sunset.

## Installation

Install the command:

```bash
brew tap cboone/diurnal-terminal https://github.com/cboone/diurnal-terminal.git
brew install diurnal-terminal
```

Edit `~/.config/diurnal-terminal.conf` with your coordinates and themes:

```bash
LATITUDE=37.783N
LONGITUDE=122.417W
DAY_THEME=GitHub Light
NIGHT_THEME=GitHub Dark
```

**Note:** Coordinates must use cardinal direction suffixes: `N` or `S` for latitude, `E` or `W` for longitude. For example, San Francisco is `37.783N` latitude and `122.417W` longitude.

Start the service:

```bash
brew services start diurnal-terminal
```

The config file is created automatically during installation with default values.

## Usage

The script supports several commands and options:

```text
diurnal-terminal (-h|--help)          Show help
diurnal-terminal --overwrite-plist    Create new plist scheduled for the next event
diurnal-terminal --print-plist        Print plist scheduled for the next event
diurnal-terminal --restart-agent      Reload the LaunchAgent
diurnal-terminal --update-theme       Apply the correct theme for the current time
```

### Examples

Apply the correct theme for the current time of day:

```bash
diurnal-terminal --update-theme
```

Preview the plist that would be generated:

```bash
diurnal-terminal --print-plist
```

## How it works

1. The script reads your coordinates from `~/.config/diurnal-terminal.conf`
2. Uses [heliocron](https://github.com/mfreeborn/heliocron) to calculate sunrise/sunset times
3. Generates a LaunchAgent plist scheduled for the next sun event
4. When triggered, switches the Terminal theme and reschedules for the next event

## See also

### [heliocron](https://github.com/mfreeborn/heliocron)

A command line application capable of delaying execution of another command until sunrise or sunset.

### [Homebrew](https://brew.sh)

The package manager for macOS used to install and manage diurnal-terminal.

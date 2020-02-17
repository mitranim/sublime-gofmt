## Overview

Gofmt is a Sublime Text 3 plugin that auto-formats Go code. Requires Sublime Text version 3124 or later. Simpler alternative to [noonat/sublime-gofmt](https://github.com/noonat/sublime-gofmt) without error highlighting.

## Installation

This plugin is not on Package Control and requires manual installation.

Clone the repo:

```sh
git clone https://github.com/mitranim/sublime-gofmt.git
```

Then symlink it to your Sublime packages directory. Example for MacOS:

```sh
mv sublime-gofmt Gofmt
cd Gofmt
ln -sf "$(pwd)" "$HOME/Library/Application Support/Sublime Text 3/Packages/"
```

To find the packages directory, use Sublime Text menu → Preferences → Browse Packages.

## Usage

By default, Gofmt will autoformat files before saving. You can trigger it
manually with the `Gofmt: Format Buffer` command in the command palette.

I **highly recommend** installing [`goimports`](https://godoc.org/golang.org/x/tools/cmd/goimports) and using it instead of `gofmt`:

```sublime-settings
  "executable": ["goimports"]
```

## Settings

See [`Gofmt.sublime-settings`](Gofmt.sublime-settings) for all available settings. To override them, open:

```
Preferences → Package Settings → Gofmt → Settings
```

Gofmt looks for settings in the following places:

  * `"Gofmt"` dict in general Sublime settings, possibly project-specific
  * `Gofmt.sublime-settings`, default or user-created

The general Sublime settings take priority. To override them on a per-project basis, create a `"Gofmt"` entry:

```sublime-settings
  "Gofmt": {
    "format_on_save": false
  },
```

## Commands

In Sublime's command palette:

* `Gofmt: Format Buffer`

## Hotkeys

To avoid potential conflicts, this plugin does not come with hotkeys. To hotkey
the format command, add something like this to your `.sublime-keymap`:

```sublime-keymap
{
  "keys": ["ctrl+super+k"],
  "command": "gofmt_format_buffer",
  "context": [{"key": "selector", "operator": "equal", "operand": "source.go"}]
}
```

## License

https://en.wikipedia.org/wiki/WTFPL

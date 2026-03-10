{
  "$schema": "https://github.com/fastfetch-cli/fastfetch/raw/dev/doc/json_schema.json",
  "logo": {
    "source": "arch",
    "padding": {
      "top": 2,
      "left": 1,
      "right": 2
    },
    "color": {
      "1": "blue",
      "2": "magenta"
    }
  },
  "modules": [
    "break",
    {
      "type": "custom",
      "format": "\u001b[90m┌──────────────────────Hardware──────────────────────┐"
    },
    {
      "type": "host",
      "key": " PC",
      "keyColor": "blue"
    },
    {
      "type": "cpu",
      "key": "│ ├",
      "showPeCoreCount": true,
      "keyColor": "blue"
    },
    {
      "type": "gpu",
      "key": "│ ├",
      "detectionMethod": "pci",
      "keyColor": "blue"
    },
    {
      "type": "display",
      "key": "│ ├󱄄",
      "keyColor": "blue"
    },
    {
      "type": "disk",
      "key": "│ ├󰋊",
      "keyColor": "blue"
    },
    {
      "type": "memory",
      "key": "│ ├",
      "keyColor": "blue"
    },
    {
      "type": "swap",
      "key": "└ └󰓡",
      "keyColor": "blue"
    },
    {
      "type": "custom",
      "format": "\u001b[90m└────────────────────────────────────────────────────┘"
    },
    "break",
    {
      "type": "custom",
      "format": "\u001b[90m┌──────────────────────Software──────────────────────┐"
    },
    {
      "type": "command",
      "key": " OS",
      "keyColor": "magenta",
      "text": "version=$(omarchy-version); echo \"Omarchy $version\""
    },
    {
      "type": "command",
      "key": "│ ├󰘬",
      "keyColor": "magenta",
      "text": "branch=$(omarchy-version-branch); echo \"$branch\""
    },
    {
      "type": "command",
      "key": "│ ├󰔫",
      "keyColor": "magenta",
      "text": "channel=$(omarchy-version-channel); echo \"$channel\""
    },
    {
      "type": "kernel",
      "key": "│ ├",
      "keyColor": "magenta"
    },
    {
      "type": "wm",
      "key": "│ ├",
      "keyColor": "magenta"
    },
    {
      "type": "de",
      "key": "│ ├",
      "keyColor": "magenta"
    },
    {
      "type": "terminal",
      "key": "│ ├",
      "keyColor": "magenta"
    },
    {
      "type": "packages",
      "key": "│ ├󰏖",
      "keyColor": "magenta"
    },
    {
      "type": "wmtheme",
      "key": "│ ├󰉼",
      "keyColor": "magenta"
    },
    {
      "type": "command",
      "key": "└ └󰸌",
      "keyColor": "magenta",
      "text": "theme=$(omarchy-theme-current); echo -e \"$theme\""
    },
    {
      "type": "custom",
      "format": "\u001b[90m└────────────────────────────────────────────────────┘"
    },
    "break",
    {
      "type": "custom",
      "format": "\u001b[90m┌────────────────Age / Uptime / Update───────────────┐"
    },
    {
      "type": "command",
      "key": "󱦟 Age",
      "keyColor": "cyan",
      "text": "birth_install=$(stat -c %W /); current=$(date +%s); time_progression=$((current - birth_install)); days_difference=$((time_progression / 86400)); echo $days_difference days"
    },
    {
      "type": "uptime",
      "key": "󱫐 Uptime",
      "keyColor": "cyan"
    },
    {
      "type": "command",
      "key": " Update",
      "keyColor": "cyan",
      "text": "updated=$(omarchy-version-pkgs); echo \"$updated\""
    },
    {
      "type": "custom",
      "format": "\u001b[90m└────────────────────────────────────────────────────┘"
    },
    "break",
    "colors"
  ]
}
# 🍃 Mint Post-Install Setup Guide

---

## 1. 📦 Package Setup

```sh
# Update apt packages:
sudo apt update
sudo apt -y upgrade
sudo apt -y dist-upgrade

# Install dnf packages:
sudo apt -y install vim zsh git
```

---

## 2. 📝 Zed

```sh
# Install Zed
curl -f https://zed.dev/install.sh | sh
```

Press `Ctrl`+`Alt`+`,` and replace the content with the following settings:
```json
{
  // --- AI ---
  "agent": {
    "sidebar_side": "right",
    "dock": "right",
  },
  "edit_predictions": {
    "provider": "none",
  },

  // --- Git ---
  "git": {
    "inline_blame": {
      "enabled": false,
    },
  },
  "git_panel": { "button": false },

  // --- Toolbar ---
  "toolbar": {
    "selections_menu": false,
  },
  "gutter": {
    "runnables": false,
  },

  // --- Tabs ---
  "tabs": {
    "git_status": true,
    "file_icons": true,
  },

  // --- Panels ---
  "project_panel": {
    "dock": "left",
    "show_diagnostics": "off",
  },
  "outline_panel": { "button": false },
  "collaboration_panel": { "button": false },
  "search": { "button": false },
  "diagnostics": { "button": false },
  "debugger": { "button": false },
  "global_lsp_settings": { "button": false },

  // --- Privacy ---
  "telemetry": {
    "diagnostics": false,
    "metrics": false,
  },

  // --- Session ---
  "session": {
    "trust_all_worktrees": true,
  },

  // --- CLI ---
  "cli_default_open_behavior": "new_window",
}
```

Install [charmed-icons](https://zed.dev/extensions/charmed-icons) theme.

Login using the **Github Account**.

Press `Ctrl`+`Alt`+`B`, then `Ctrl`+`Alt`+`C` and configure **Github Copilot Chat**.

---

## 3. ⚙️ Settings

```sh
# Set background:
gsettings set org.cinnamon.desktop.background picture-options 'none'
gsettings set org.cinnamon.desktop.background color-shading-type 'solid'
gsettings set org.cinnamon.desktop.background primary-color '#2a2a2e'

# Disable lock screen:
gsettings set org.cinnamon.desktop.lockdown disable-lock-screen true
gsettings set org.cinnamon.desktop.screensaver lock-enabled false
gsettings set org.cinnamon.settings-daemon.plugins.power lock-on-suspend false
gsettings set org.cinnamon.desktop.session idle-delay 0

# Disable suspension:
gsettings set org.cinnamon.settings-daemon.plugins.power sleep-display-ac 0
gsettings set org.cinnamon.settings-daemon.plugins.power sleep-inactive-ac-timeout 0
gsettings set org.cinnamon.settings-daemon.plugins.power sleep-display-battery 0
gsettings set org.cinnamon.settings-daemon.plugins.power sleep-inactive-battery-timeout 0
gsettings set org.cinnamon.settings-daemon.plugins.power idle-dim-battery 'false'

# Change the key to move a window:
gsettings set org.cinnamon.desktop.wm.preferences mouse-button-modifier "<Super>"

# Set dark mode:
gsettings set org.x.apps.portal color-scheme 'prefer-dark'
gsettings set org.cinnamon.desktop.interface gtk-theme 'Mint-Y-Dark-Aqua'
```

Set the following pinned app order:
1. Firefox
2. Thunderbird
3. Files
4. Terminal

### 4. 🦊 Configure Firefox

Hide startpage weather widget and shortcuts.

Install the following extension:
- [**uBlock Origin**](https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/)

### 3. 🐚 Configure Zsh

```sh
# Install Oh My Zsh:
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
```sh
# Clear .zshrc
echo 'export PATH=$HOME/bin:$HOME/.local/bin:/usr/local/bin:$PATH' > ~/.zshrc
echo 'export ZSH="$HOME/.oh-my-zsh"' >> ~/.zshrc
echo 'ZSH_THEME="bira"' >> ~/.zshrc
echo 'source $ZSH/oh-my-zsh.sh' >> ~/.zshrc
```
> [!TIP]
> Close and re-open the terminal to apply the shell change.

---

## 4. 🔁 Cleanup and Final Reboot

```sh
# Cleanup unused dependencies:
sudo apt-get -y autoremove --purge
sudo apt autoclean

# Reboot the system:
systemctl reboot
```

---

## ✅ Done!

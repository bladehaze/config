# 💻 Dotfiles

My personal configuration files managed via a **Bare Git Repository**. 
This setup allows me to keep my home directory clean while syncing shared aliases and functions across **macOS** and **Linux**.

## 🛠 Features
- **Non-destructive:** Doesn't overwrite your existing `.zshrc`.
- **Modular:** Uses a `~/.zsh_shared` file for common settings.
- **Cross-Platform:** Detects if you are on Mac or Linux for specific aliases.

---

## 🚀 Setup on a New Machine

Follow these steps to deploy these configs on a fresh target machine.

### 1. Define the Alias
Copy and paste this into your terminal to interact with the config repo:
```bash
alias config='git --git-dir=$HOME/.myconfig/ --work-tree=$HOME'
```

### 2. Clone the Repository
Clone the repo as a bare repository into a hidden folder:
```bash
git clone --bare git@github.com:bladehaze/config.git $HOME/.myconfig
```

### 3. Checkout the Files
Apply the tracked files to your home directory:
```bash
config checkout
```

### 4. Silence Untracked Files
Ensure myconfig status doesn't show every single file in your home directory:
```bash
config config --local status.showUntrackedFiles no
```

## Linking to Environment

To keep your setup modular, the main ~/.zshrc is not tracked. This allows local installers (nvm, brew, etc.) to modify it safely.

Add this line to the end of your local ~/.zshrc to load your synced settings:

```bash
# Load shared configurations from GitHub
[[ -f ~/.zshrc_common ]] && source ~/.zshrc_common
```

## Usage & Maintenance

```bash
config add ~/.zshrc_common
config commit -m "Update shared aliases"
config push -u origin main
```

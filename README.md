## 🚀 System Setup: Personalized Zsh Configuration

This guide details the steps to set up a powerful and customized terminal environment using **Zsh**, **Oh My Zsh**, the **Spaceship** prompt, and essential plugins.

### 1. Install Zsh and Core Utilities

First, install the Zsh shell and other utilities required for the enhanced terminal experience.

```bash
sudo apt update
sudo apt install -y zsh curl autojump
```

**Note**: To set Zsh as your default shell run: 

```bash
chsh -s $(which zsh)
```
You will need to log out and log back in for the change to take effect.

### 2. Install Oh My Zsh

Oh My Zsh is a delightful, open-source framework for managing your Zsh configuration.
```bash
sh -c "$(curl -fsSL [https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh](https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh))"
```

### 3. Install the Spaceship Prompt
#### 3.1. Install the Theme

Clone the repository into your custom themes directory:

```bash
git clone [https://github.com/spaceship-prompt/spaceship-prompt.git](https://github.com/spaceship-prompt/spaceship-prompt.git) "$ZSH_CUSTOM/themes/spaceship-prompt" --depth=1
```

#### 3.2. Create a Symlink

Create a symbolic link to make the theme easily loadable by Oh My Zsh:

```bash
ln -s "$ZSH_CUSTOM/themes/spaceship-prompt/spaceship.zsh-theme" "$ZSH_CUSTOM/themes/spaceship.zsh-theme"
```

#### 3.3. Update .zshrc

Edit your ~/.zshrc file and set the theme:

```bash
# In ~/.zshrc, change the line to:
ZSH_THEME="spaceship"
```

### 4. Install Nerd Fonts (Crucial for Spaceship)

The Spaceship prompt uses special icons and symbols that require a Nerd Font to display correctly.

1. Visit [the Nerd Fonts website](https://www.nerdfonts.com/font-downloads).

2. Download and install a font of your choice (e.g., Hack, FiraCode, Meslo).

3. Configure your terminal emulator (e.g., Gnome Terminal, iTerm2, VS Code Integrated Terminal) to use the installed Nerd Font.

### 5. Configure Zsh Plugins
#### 5.1. Install Custom Plugins

Clone the repositories for the history and syntax highlighting features:

```bash
# Install Zsh History Substring Search
git clone [https://github.com/zsh-users/zsh-history-substring-search](https://github.com/zsh-users/zsh-history-substring-search) ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-history-substring-search

# Install Zsh Syntax Highlighting
git clone [https://github.com/zsh-users/zsh-syntax-highlighting.git](https://github.com/zsh-users/zsh-syntax-highlighting.git) ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

#### 5.2. Activate All Plugins

Edit your ~/.zshrc file and update the plugins array with the following list:

```bash
# In ~/.zshrc, update the line to:
plugins=(
    git
    opentofu
    python
    autojump
    zsh-autosuggestions
    zsh-syntax-highlighting
    sudo
    docker
    zsh-history-substring-search
)
```

### 6. Spaceship Prompt Customization (.spaceshiprc)

Create a new configuration file named .spaceshiprc in your home directory (~/.spaceshiprc) and add the following settings:

```bash
# ~/.spaceshiprc
SPACESHIP_TIME_SHOW=false
SPACESHIP_USER_SHOW=always
SPACESHIP_DIR_TRUNC_REPO=false
SPACESHIP_USER_COLOR=blue
SPACESHIP_HOST_COLOR=red
SPACESHIP_DIR_COLOR=green
SPACESHIP_GIT_BRANCH_COLOR=cyan
SPACESHIP_GIT_STATUS_COLOR=yellow

# Add a prompt character before the input line
spaceship add --before char
```

### 7. Finalize and Reload

After making all changes to ~/.zshrc and creating ~/.spaceshiprc, apply the configuration by reloading your Zsh environment:
Bash

```bash
source ~/.zshrc
```
# Arch Setup

## Basic userspace setup

```bash
packages=(
    # basic utilities
    git
    base-devel
    curl
    wget
    zsh
    python
    ssh
    # advanced
    firefox
    github-cli
)

sudo pacman -S --needed "${packages[@]}"

# install yay
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
cd .. && rm -rf yay
```

## ZSH Setup

Install packages:

```bash
yay -S ttf-firacode-nerd antigen
```

Edit `.zshrc`:

```zsh
alias gac="git add -A && git commit -m"
alias spm="sudo pacman"
alias open="xdg-open"

# install antigen
source /usr/share/zsh/share/antigen.zsh

# load ohmyzsh
antigen use oh-my-zsh

# ohmyzsh plugins
antigen bundle git
antigen bundle pip
antigen bundle globalias

# external plugins
antigen bundle zsh-users/zsh-syntax-highlighting
antigen bundle zsh-users/zsh-autosuggestions
antigen bundle marlonrichert/zsh-autocomplete@main

# theme
antigen theme spaceship-prompt/spaceship-prompt

# Apply setup
antigen apply
```

## Neovim Setup

```zsh
# prerequisits
yay -S nvim-packer-git neovim
mkdir ~/.config

# install config
git clone https://github.com/haasal/nvim-config ~/.config/nvim
```

Then do `:PackerSync` inside neovim.
To add support for a new language/framework use:

```nvim
:TSInstall <lang>
:MasonInstall <lang>
```

# Ubuntu Linux - ZSH(OhMyZsh) - NeoVim - Tmux Configuration

# Linux - Ubuntu - VirtualBox Setup (Optional)
*  Virtualization - **ON**
*  Download the `.iso` file (ex. ubuntu-22.04.3-desktop-amd64.iso)
*  Create Virtual Machine Prompt
   * Version - Ubuntu (64-bit)
   * Allocate disk space
* Display
  * Video memory - max
  * Enable 3D Acceleration
* Storage
  * Click on Empty -> Click on DVD icon -> Chose a disk file -> Add `.iso` file
* Run the virtual machine and install ubuntu
* Erase disk and install Ubuntu
* Do not check `active directory`
* When booted
  * Click `Devices` in the menu, and click `Insert Guest Addittions CD Image...`
  * Copy **everything** from the `VBox mount`, to the `Documents` directory
  * Open the terminal, while in the `Documents` directory
  * Run `sudo apt update`
  * `sudo apt install linux-headers-$(uname -r)`
  * `chmod +x VBoxLinuxAdditions.run`
  * `sudo ./VBoxLinuxAdditions.run`

# Global install
* `sudo apt update`
* `sudo apt upgrade`
* `sudo apt install git wget curl xclip gcc ripgrep pandoc npm python3-pip python3-venv`
* `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash`

# Git Config
* `git config --global user.name "username"`
* `git config --global user.email "email"`
* `git config --global credential.helper store`

# ZSH (OhMyZsh)
* Installing zsh
    * `sudo apt install zsh`

* Changing zsh to be main terminal (restart needed)
    * `chsh -s $(which zsh)`

* Installing Oh-My-Zsh
    * `sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`

* Installing Oh-My-Zsh plugins
    * `git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions`
    * `git clone https://github.com/zsh-users/zsh-syntax-highlighting ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting`

* Installing Catpuccin theme for GNOME-terminal
    * `curl -L https://raw.githubusercontent.com/catppuccin/gnome-terminal/v0.2.0/install.py | python3 -`

* Downloading the Nerd Font(Hack Nerd Font)
    * `wget https://github.com/ryanoasis/nerd-fonts/raw/master/patched-fonts/Hack/Regular/HackNerdFont-Regular.ttf -P ~/.local/share/fonts`

* Downloading the terminal theme
    * `git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k`

# NEOVIM

* NeoVim Installation (lazy.nvim requires Neovim >= 0.8.0)
    * `sudo add-apt-repository ppa:neovim-ppa/unstable` 
    * `sudo apt-get update`
    * `sudo apt-get install neovim`

* Download `live-server` (for markdown-preview)
    * `sudo npm install -g live-server`

# CLONING THE CONFIG
  ```bash
    mkdir ~/.config/temp
    git clone https://github.com/cviki76/linux-ubuntu-config ~/.config/temp
    rm -rf ~/.config/temp/.git
    rm -rf ~/.config/temp/README.md
    rm -rf ~/.config/temp/script.sh
    mv ~/.config/temp/* ~/.config
    mv ~/.config/temp/.* ~
    rm -rf ~/.config/temp
  ```
# TMUX

* Tmux Installation
   * `sudo apt-get install tmux`
* Tmux Plugin Installation
   * `git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm`
* Create a folder for tmux sessions(for tmux-ressurect)
   * `mkdir ~/.config/tmux_sessions`
* Reboot the PC
* Select the GNOME terminal theme(Catppuccin Mocha) and the nerd font in the terminal `Preferences`**
* Make a tmux session
* For every plugin in ~/.config/tmux/tmux.conf (`set -g @plugin *`)
   * `Ctrl + Space`(leader key for tmux configured in the tmux.conf file) + I --> for install
   * The plugins should be appearing in the `~/.config/tmux/plugins` directory
* In `.config/tmux/plugins/vim-tmux-navigator` change the bind keys to be like this
    * ```bash
        tmux bind-key -n C-j if-shell "$is_vim" "send-keys C-j" "select-pane -L"
        tmux bind-key -n C-k if-shell "$is_vim" "send-keys C-k" "select-pane -D"
        tmux bind-key -n C-i if-shell "$is_vim" "send-keys C-i" "select-pane -U"
        tmux bind-key -n C-l if-shell "$is_vim" "send-keys C-l" "select-pane -R"
        ```
* Sourcing tmux conf
    * `tmux source-file ~/.tmux.conf`
* Installing plugins
    * `~/.tmux/plugins/tpm/bin/install_plugins`

# Setup using a script
* `sudo apt install curl`
* `sh -c "$(curl -fsSL https://raw.githubusercontent.com/cviki76/linux-ubuntu-config/main/config_init.sh)"`
* `nvm install 20`

# configs
Personal Linux dotfiles.

For the moment this repository contains only conf files situated at the root of the home folder.

# Pre-setup
- Install [zsh](https://github.com/ohmyzsh/ohmyzsh/wiki/Installing-ZSH):
```
apt install zsh
```
- Install [oh-my-zsh](https://github.com/ohmyzsh/ohmyzsh):
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
- Install [tmux](https://github.com/tmux/tmux/wiki/Installing):
```
sudo apt install tmux
```

# Setup
Courtesy of https://developer.atlassian.com/blog/2016/02/best-way-to-store-dotfiles-git-bare-repo/
### If you already store your configuration/dotfiles in a Git repository, on a new system you can migrate to this setup with the following steps:

script: https://gist.githubusercontent.com/csbenz/f5c8560e9a29cb9cccf8a6522c89943a/raw/ce12ed5e3469e889e4cd116507b7f3dd5faabad8/cfg-install.sh

* Prior to the installation make sure you have committed the alias to your .bashrc or .zsh:
```
alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'
```

* And that your source repository ignores the folder where you'll clone it, so that you don't create weird recursion problems:
```
echo ".cfg" >> .gitignore
```

* Now clone your dotfiles into a bare repository in a "dot" folder of your $HOME:
```
git clone --bare https://github.com/csbenz/configs.git $HOME/.cfg
```

* Define the alias in the current shell scope:
```
alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'
```

* Checkout the actual content from the bare repository to your $HOME:
```
config checkout
```

* Set the flag showUntrackedFiles to no on this specific (local) repository:
```
config config --local status.showUntrackedFiles no
```

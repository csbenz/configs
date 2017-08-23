# configs
Personal Linux config files.

For the moment this repository contains only conf files situated at the root of the home folder.

# Setup
Courtesy of https://developer.atlassian.com/blog/2016/02/best-way-to-store-dotfiles-git-bare-repo/
### If you already store your configuration/dotfiles in a Git repository, on a new system you can migrate to this setup with the following steps:

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

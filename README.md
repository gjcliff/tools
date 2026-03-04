# my tools

## nvim
### intro
neovim is a community fork of vim. it's so cool bro

i would you like to direct your attention to the following diagram:  
![vim_graph](./vim_graph.png)

i would recommend starting out with the vscode vim or neovim plugins for vscode,
so that you don't just fully jump off into the deep end all at once. that's what
i did.

instead of reading my half explanations of stuff through this section, 
you could watch these videos to get a better version of the same information:
https://www.youtube.com/playlist?list=PLep05UYkc6wTyBe7kPjQFWVXTlhKeQejM

this guy is a core maintainer of neovim

### install
to install neovim, i find it's simplest to install it from source. the pinned
version of neovim in the ubuntu package registry is pretty old, especially on
OS's such as Ubuntu 22.04

neovim has great [build instructions](https://github.com/neovim/neovim/blob/master/BUILD.md)

building neovim is great because when neovim releases a new stable version, you 
can update by running ```git pull``` inside the neovim repo, and then rebuilding 
and reinstalling.

### package managers
i watched [this video](https://www.youtube.com/watch?v=w7i4amO_zaE) to learn how to configure neovim
it's pretty outdated now. the package manager he uses, "packer", is abandoned.

one very popular package manager and the one i use now is [lazy.nivm](https://github.com/folke/lazy.nvim)

in neovim, the package manager installs and manages your plugins. these are
exactly like vscode plugins. most plugins live on github, and you can install
anthing you want. you can even [write your own](https://www.youtube.com/watch?v=VGid4aN25iI&list=PL8M9ZjrDX7lp_Cfr5cul2pLZm-vle9Sns)

this is my neovim config that i use every day:
https://github.com/gjcliff/nvim


### plugins
there are a huge amount of plugins, here are some ones i like

#### essential
- [which-key.nvim](https://github.com/folke/which-key.nvim) (keybinding hints)
- [telescope.nvim](https://github.com/nvim-telescope/telescope.nvim) (https://www.youtube.com/watch?v=iqdCshrIKIg)
- [nvim-treesitter](https://github.com/nvim-treesitter/nvim-treesitter) (https://www.youtube.com/watch?v=09-9LltqWLY)

#### colorschemes
- [brightburn](https://github.com/erikbackman/brightburn.vim)
- [kanagawa](https://github.com/rebelot/kanagawa.nvim)
- [nightfox](https://github.com/EdenEast/nightfox.nvim)
- [gruvbox](https://github.com/ellisonleao/gruvbox.nvim)
- [rose-pine](https://github.com/rose-pine/neovim)

#### amazing
- [oil.nvim](https://github.com/stevearc/oil.nvim) (warning: life changingly great)
- [fugitive.nvim](https://github.com/tpope/vim-fugitive) (git stuff, illegally good)
- [conform.nvim](https://github.com/stevearc/conform.nvim) (formatting)
- [lualine.nvim](https://github.com/nvim-lualine/lualine.nvim) (pretty)
- [autopairs.nvim](https://github.com/windwp/nvim-autopairs) (attention vscode users)
- [leetcode.nvim](https://github.com/kawre/leetcode.nvim)
- [luasnip](https://github.com/L3MON4D3/LuaSnip)
    - https://www.youtube.com/watch?v=Dn800rlPIho
    - https://www.youtube.com/watch?v=KtQZRAkgLqo&t=271s
    - https://www.youtube.com/watch?v=aNWx-ym7jjI

### lsp
watch this:
https://www.youtube.com/watch?v=bTWWFQZqzyI

this is kinda hard to figure out. you can checkout my lsp.lua file in my config as 
an example. i use something called [Mason] to install lsps easily.

ask me if you have questions

here is my lsp config:
https://github.com/gjcliff/nvim/blob/main/lua/graham/lazy/lsp.lua

and configuration of individual lsps:
https://github.com/gjcliff/nvim/tree/main/after/lsp

i'd say this is the trickiest part you have to figure out before you can do real 
work in nvim

### learning
it takes time

you can view neovim's extensive help pages and manual by opening neovim and
typing ":help"

read the first bit to learn how to navigate the manual

you can also add keywords to help, like ":help tabs"

amazing:
https://www.youtube.com/watch?v=X6AR2RMB5tE&list=PLm323Lc7iSW_wuxqmKx_xxNtJC_hJbQ7R

here's a playlist with some great videos on youtube for learning vim motions.
https://www.youtube.com/watch?v=X6AR2RMB5tE&list=PLm323Lc7iSW_wuxqmKx_xxNtJC_hJbQ7R

vim be good
https://github.com/ThePrimeagen/vim-be-good

you can just hop right into vim-be-good with this docker command:
```bash
docker run -it --rm brandoncc/vim-be-good:stable
```

## alacritty
alacritty is a terminal emulator that uses gpu acceleration and can be
configured with a simple toml file. other terminals you may be interested in
include:
- [ghostyy](https://ghostty.org/)
- [kitty](https://sw.kovidgoyal.net/kitty/)
- [wezterm](https://wezterm.org/index.html)

my alacritty config can be found at:
https://github.com/gjcliff/.dotfiles/blob/main/.config/alacritty/alacritty.toml

install a nerd font so that things work right. this is the one i use:
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/JetBrains/JetBrainsMono/master/install_manual.sh)"
```

there are other fonts:
- [Hack](https://github.com/source-foundry/Hack)
- [FiraCode](https://github.com/tonsky/FiraCode)
- many many many other fonts

## tmux
install with
```bash
sudo apt install tmux
```

you can configure tmux with a file. tmux looks for its config at these locations
in order:
- $TMUX_CONF (set in ```~/.bashrc```)
- ```~/.tmux.conf```
- ```$XDG_CONFIG_HOME/tmux/tmux.conf``` (usually ```~/.config/tmux/tmux.conf```)
- /etc/tmux.conf (system wide)

i use the second method. you can take a look at my tmux config file [here](https://github.com/gjcliff/.dotfiles/blob/main/.tmux.conf)

here are some things i think you should definitely have in your config:
```sh
# allows you to reload your config with ctrl+r, instead of having to quit tmux
# to see the changes you make
unbind r
bind r source-file ~/.tmux.conf \; display-message "Config reloaded..."

# change default prefix to ctrl+s from ctrl+b because it's easier for me
set -g prefix C-s

# mouse support
set -g mouse on

# change vertical and horizontal split to ctrl+s+v and ctrl+s+s, respectively.
# as opposed to the defaults of % and " (gross)
bind-key v split-window -h
bind-key s split-window -v

# use ctrl+y to full screen your active tmux pane, hit it again to unfullscreen
unbind-key z
bind-key y resize-pane -Z

# color settings for nvim
set -g default-terminal "xterm-256color"
set-option -a terminal-overrides 'alacritty:Tc'

# tpm: https://github.com/tmux-plugins/tpm
# follow the instructions in the installation section.
# you'll need this:
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-sensible'

# install the dracula plugin for pretty colors in the status bar at the top
# https://github.com/dracula/tmux
set -g @plugin 'dracula/tmux'
set -g @dracula-show-powerline true
set -g @dracula-fixed-location "Washington D.C."
set -g @dracula-show-flags true
set -g @dracula-show-left-icon "#h | #S"
set -g @dracula-battery-label false
set -g @dracula-show-battery-status true
set -g @dracula-network-hosts "1.1.1.1 8.8.8.8"
set -g @dracula-network-ethernet-label "󰌗 Eth"
set -g @dracula-network-offline-label "󱍢 "
set -g @dracula-network-wifi-label ""
set -g @dracula-show-ssh-only-when-connected true
set -g @dracula-plugins "network ssh-session network-bandwidth cpu-usage ram-usage battery weather time"
set -g status-position top

run '~/.tmux/plugins/tpm/tpm'
```

in order for this to work right you need to install the tmux plugin manager (tpm)
https://github.com/tmux-plugins/tpm

and then once it's installed, start tmux fresh and you should be good to go.

## zsh
https://zsh.sourceforge.io/

zsh feels better than bash. tab is your best friend. with zsh, you can use tab and enter
to lazily navigate through directories on the command line, and it's great!

you can just install it from apt, but there are other ways if you want a newer
version:
https://github.com/ohmyzsh/ohmyzsh/wiki/Installing-ZSH

```bash
sudo apt install zsh
zsh --version
# change shell to zsh
chsh -s $(which zsh)
```

if you want to test out a proper zsh experience with oh-my-zsh installed, you
can do this:
```bash
docker run -it --rm -e TERM=xterm-256color ubuntu:24.04 \
bash -c "apt-get update -q && apt-get install -y -q zsh && exec zsh"

ls # then hit tab a bunch of times
```

## omz
this is how you get themes, better tab completion with your favorite programs,
timestamps in your terminal, etc.
https://ohmyz.sh/
https://ohmyz.sh/#install

## conda/mamba
conda is similar to python virtual environments except it's different

with conda, you can install:
* different versions of python easily
* non-python dependencies such as CUDA, R, C libraries, and other stuff

that's why you see it in a lot of pytorch/machine learning projects.

mamba is like a free, open source, faster version of conda. the company behind
conda made it so you have to pay to download packages from them using conda,
mamba is totally free.

https://github.com/mamba-org/mamba
https://mamba.readthedocs.io/en/latest/installation/mamba-installation.html

i'm using this at work right now for pytorch projects which is why i'm including
it

## configs
you can see all the configs i use here:
https://github.com/gjcliff/.dotfiles

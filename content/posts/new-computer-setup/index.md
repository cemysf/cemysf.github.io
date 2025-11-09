---
title: "New computer setup"
date: 2025-11-07T23:55:00+01:00
draft: false
tags: ["productivity", "setup"]
showToc: true
TocOpen: false
draft: false
hideMeta: false
comments: true
# description: "Desc Text."
# canonicalURL: "https://canonical.url/to/page"
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
---

Starting my new SWE job, I had recently set-up my new development purpose macbook. Writing those below so I can (you can too!) refer to whenever needed. Will update here later, when I stumble upon another interesting thing.

## Terminal & related stuff

- Install [iTerm2](https://iterm2.com/)
- Get [Oh My Zsh](https://ohmyz.sh/)
  - Theme: [powerlevel10k](https://github.com/romkatv/powerlevel10k)
  > CAUTION: As of 2025, p10k is no longer maintained, but it's not yet broken and I still use it, will look for a new one later
  - Autosuggestions: [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions)
  - Bookmarks: [zshmarks](https://github.com/jocelynmallon/zshmarks)
- Some aliases that I use. Add `source ~/.aliases` to your `.zshrc`
{{<details summary="`~/.aliases`">}}

```sh
alias g=git
alias d=docker
alias j=jump
```

{{</details>}}

- Resulting `.zshrch` file
{{<details summary="`~/.zshrc`">}}

```sh
# Enable Powerlevel10k instant prompt. Should stay close to the top of ~/.zshrc.
# Initialization code that may require console input (password prompts, [y/n]
# confirmations, etc.) must go above this block; everything else may go below.
if [[ -r "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh" ]]; then
  source "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh"
fi

# If you come from bash you might have to change your $PATH.
# export PATH=$HOME/bin:$HOME/.local/bin:/usr/local/bin:$PATH

# Path to your Oh My Zsh installation.
export ZSH="$HOME/.oh-my-zsh"

# Set name of the theme to load --- if set to "random", it will
# load a random theme each time Oh My Zsh is loaded, in which case,
# to know which specific one was loaded, run: echo $RANDOM_THEME
# See https://github.com/ohmyzsh/ohmyzsh/wiki/Themes
ZSH_THEME="powerlevel10k/powerlevel10k"

# Set list of themes to pick from when loading at random
# Setting this variable when ZSH_THEME=random will cause zsh to load
# a theme from this variable instead of looking in $ZSH/themes/
# If set to an empty array, this variable will have no effect.
# ZSH_THEME_RANDOM_CANDIDATES=( "robbyrussell" "agnoster" )

# Uncomment the following line to use case-sensitive completion.
# CASE_SENSITIVE="true"

# Uncomment the following line to use hyphen-insensitive completion.
# Case-sensitive completion must be off. _ and - will be interchangeable.
# HYPHEN_INSENSITIVE="true"

# Uncomment one of the following lines to change the auto-update behavior
# zstyle ':omz:update' mode disabled  # disable automatic updates
# zstyle ':omz:update' mode auto      # update automatically without asking
# zstyle ':omz:update' mode reminder  # just remind me to update when it's time

# Uncomment the following line to change how often to auto-update (in days).
# zstyle ':omz:update' frequency 13

# Uncomment the following line if pasting URLs and other text is messed up.
# DISABLE_MAGIC_FUNCTIONS="true"

# Uncomment the following line to disable colors in ls.
# DISABLE_LS_COLORS="true"

# Uncomment the following line to disable auto-setting terminal title.
# DISABLE_AUTO_TITLE="true"

# Uncomment the following line to enable command auto-correction.
# ENABLE_CORRECTION="true"

# Uncomment the following line to display red dots whilst waiting for completion.
# You can also set it to another string to have that shown instead of the default red dots.
# e.g. COMPLETION_WAITING_DOTS="%F{yellow}waiting...%f"
# Caution: this setting can cause issues with multiline prompts in zsh < 5.7.1 (see #5765)
# COMPLETION_WAITING_DOTS="true"

# Uncomment the following line if you want to disable marking untracked files
# under VCS as dirty. This makes repository status check for large repositories
# much, much faster.
# DISABLE_UNTRACKED_FILES_DIRTY="true"

# Uncomment the following line if you want to change the command execution time
# stamp shown in the history command output.
# You can set one of the optional three formats:
# "mm/dd/yyyy"|"dd.mm.yyyy"|"yyyy-mm-dd"
# or set a custom format using the strftime function format specifications,
# see 'man strftime' for details.
# HIST_STAMPS="mm/dd/yyyy"

# Would you like to use another custom folder than $ZSH/custom?
# ZSH_CUSTOM=/path/to/new-custom-folder

# Which plugins would you like to load?
# Standard plugins can be found in $ZSH/plugins/
# Custom plugins may be added to $ZSH_CUSTOM/plugins/
# Example format: plugins=(rails git textmate ruby lighthouse)
# Add wisely, as too many plugins slow down shell startup.
plugins=(
    git
    zsh-autosuggestions
    zshmarks
)

source $ZSH/oh-my-zsh.sh

# User configuration

# export MANPATH="/usr/local/man:$MANPATH"

# You may need to manually set your language environment
# export LANG=en_US.UTF-8

# Preferred editor for local and remote sessions
# if [[ -n $SSH_CONNECTION ]]; then
#   export EDITOR='vim'
# else
#   export EDITOR='nvim'
# fi

# Compilation flags
# export ARCHFLAGS="-arch $(uname -m)"

# Set personal aliases, overriding those provided by Oh My Zsh libs,
# plugins, and themes. Aliases can be placed here, though Oh My Zsh
# users are encouraged to define aliases within a top-level file in
# the $ZSH_CUSTOM folder, with .zsh extension. Examples:
# - $ZSH_CUSTOM/aliases.zsh
# - $ZSH_CUSTOM/macos.zsh
# For a full list of active aliases, run alias.
#
# Example aliases
# alias zshconfig="mate ~/.zshrc"
# alias ohmyzsh="mate ~/.oh-my-zsh"

# To customize prompt, run p10k configure or edit ~/.p10k.zsh.
[[ ! -f ~/.p10k.zsh ]] || source ~/.p10k.zsh

# import aliases
source ~/.aliases
```

{{< /details >}}

Here's how the terminal looks like after the setup:
{{< figure src="/img/posts/terminal_after_setup.png" caption="Minimalist terminal, visuals can be adjusted with `p10k configure`, gray text is the suggested by the autocomplete engine, based on shell commands history." >}}

## Gitconfig

Enhancing git experience overall.

{{<details summary="`~/.gitconfig`">}}

```sh
[alias]
  alias = "!git config -l | grep alias | cut -c 7-"
  au = add -u
  b = "!git for-each-ref --sort='-authordate' --format='%(authordate)%09%(objectname:short)%09%(refname)' refs/heads | sed -e 's-refs/heads/--'"  # list branches sorted by last modified
  cm = commit
  co = checkout
  cob = checkout -b
  d = diff
  diffr  = "!f() { git diff "$1"^.."$1"; }; f"
  discard = reset HEAD --hard
  dlc = 
  dlc = diff --cached HEAD^
  graph = log --graph --abbrev-commit --date=relative --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %Cblue%cn%Creset committed %s %Cgreen(%cr)%Creset'
  ld = log --pretty=format:"%C(yellow)%h\\ %ad%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate --date=relative
  lds = log --pretty=format:"%C(yellow)%h\\ %ad%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate --date=short
  ll = log --pretty=format:"%C(yellow)%h%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate --numstat
  ls = log --pretty=format:"%C(yellow)%h%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate
  p = pull
  pf = pull --ff-only
  s = status
  uncommit = reset --soft HEAD^
  unstage = reset HEAD --

[merge]
  conflictstyle = diff3
```

{{</details>}}

## Apps

Some apps that I find useful.

### Productivity

- [Rectangle](https://rectangleapp.com/)

> Window arranger

- [BetterDisplay](https://github.com/waydabber/BetterDisplay), (or [MonitorControl](https://github.com/MonitorControl/MonitorControl) for a simpler one)

> Display manager

- [Bluesnooze](https://github.com/odlp/bluesnooze)

> Prevents bluetooth connections while sleeping

- [Maccy](https://github.com/p0deje/Maccy)

> Clipboard manager, auto-saves whatever copied to clipboard (careful with secrets!)

### Dev helper tools

- [DBeaver](https://dbeaver.io/download/)

> Database management tool

- [Lens](https://k8slens.dev/)

> Kubernetes management tool

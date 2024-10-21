---
layout: page
title: "Shell"
---

# Shell script & Terminal

## iTerm2

[features](https://iterm2.com/features.html)

[cheat sheet](https://gist.github.com/squarism/ae3613daf5c01a98ba3a)

## Run Command File

differences between `'` and `"` in `bash` and in `zsh` ?

`tput` documentation ?

`.zshrc`

```sh
# https://www.moncefbelyamani.com/how-to-install-xcode-homebrew-git-rvm-ruby-on-mac/
source /opt/homebrew/opt/chruby/share/chruby/chruby.sh
source /opt/homebrew/opt/chruby/share/chruby/auto.sh
chruby ruby-3.3.5

# https://github.com/zsh-users/zsh-autosuggestions/blob/master/INSTALL.md
source $(brew --prefix)/share/zsh-autosuggestions/zsh-autosuggestions.zsh

# https://github.com/zsh-users/zsh-syntax-highlighting/blob/master/INSTALL.md
source $(brew --prefix)/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh

#bindkey -v
#function zle-line-init zle-keymap-select {
    #RPS1="${${KEYMAP/vicmd/%B〈%b}/(main|viins)}"
    #RPS2=$RPS1
    #zle reset-prompt
#}
#zle -N zle-line-init
#zle -N zle-keymap-select

PS1='%B%F{141}%n@%m 〉%f%1~ 〉%b'
PS2='%B 〉%b'
```

`.vimrc`
```vim
set shiftwidth=4 smarttab
set expandtab
set number
set relativenumber
syntax on
```

## Expansions

[special variables](https://tecadmin.net/bash-special-variables/)

### Prompt expansion

Variable expanded in `PS0` to `PS4` and `PROMPT_COMMAND`

[zsh](https://zsh.sourceforge.io/Doc/Release/Prompt-Expansion.html)

[bash](https://ss64.com/bash/syntax-prompt.html)

| Xterm-[colors](https://www.ditig.com/publications/256-colors-cheat-sheet) | RGB conversion | example |
| - | - | - |
| 0-15 | binary; RGB; *255 | 10 → 110<sub>2</sub> → (0, 255, 255)<sub>RGB</sub> |
| 16-231 | -16, hexal; BGR; 0, *40+55 | 141 → 125 = 325<sub>6</sub> → (175, 135, 255)<sub>RGB</sub> |
| 232-255 | -232; R=G=B; *10+8 | 249 → 17 → (178,178,178)<sub>RGB</sub> |

### Parameter expansion

usually, `expr` contains the wildcard `*` and can be expanded in multiple forms.

| expression | result of the expansion |
| - | - |
| `${var:=def}` | `var` or `def` if `var` is null |
| | |
| `${var:offset}` | substring of var starting at of `offset` (can be negative) |
| `${var:offset:len}` | substring of var starting at of `offset` of length `len` |
| | |
| `${var/expr}` | remove the longest form of `expr` from `var` |
| `${var#expr}` | remove the shortest form of `expr` form the begining of `var` |
| `${var##expr}` | remove the longest form of `expr` from the begining of `var` |
| `${var%expr}` | remove the shortest form of `expr` form the end of `var` |
| `${var%%expr}` | remove the longest form of `expr` from the end of `var` |
| | |
| `${var/expr/repl}` | replace the first match of `expr` by ` repl` in `var` |
| `${var//expr/repl}` | replace all matches of `expr` by ` repl` in `var` |
| `${var/#expr/repl}` | replace `expr` by ` repl` in the begining`var` |
| `${var/%expr/repl}` | replace `expr` by ` repl` in the end `var` |
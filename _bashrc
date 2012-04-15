# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

case "$COLORTERM" in
    gnome-terminal) color_prompt=yes; export TERM=xterm-256color;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
    # We have color support; assume it's compliant with Ecma-48
    # (ISO/IEC-6429). (Lack of such support is extremely rare, and such
    # a case would tend to support setf rather than setaf.)
    color_prompt=yes
    else
    color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi


################################################################################
# READLINE                                                                             ################################################################################

# For those who want to use Vi bindings in bash, this corrects a
# few annoyances:
#
# 1) up and down arrows retrieve history lines even in insert mode
# 2) left and right arrows work in insert mode
# 3) Ctrl-A and Ctrl-E work how you expect if you have had to
# live in Emacs mode in the past.
# 4) So does Ctrl-D.

## Command-mode bindings
# Ctrl-A or Home: insert at line beginning like in emacs mode
bind -m vi-command 'Control-a: vi-insert-beg'
# Ctrl-E or End: append at line end like in emacs mode
bind -m vi-command 'Control-e: vi-append-eol'
# to switch to emacs editing mode
bind -m vi-command '"ZZ": emacs-editing-mode'

## Insert-mode bindings
# up arrow or PgUp: append to previous history line
bind -m vi-insert '"\M-[A": ""' # <---- CTRL-P CTRL-E
bind -m vi-insert '"\M-[5~": ""' #<---- CTRL-P CTRL-E
bind -m vi-insert 'Control-p: previous-history'
# dn arrow or PgDn: append to next history line
bind -m vi-insert '"\M-[B": ""' #<---- CTRL-P CTRL-E
bind -m vi-insert '"\M-[6~": ""' #<---- CTRL-P CTRL-E
bind -m vi-insert 'Control-n: next-history'
# Ctrl-A: insert at line start like in emacs mode
bind -m vi-insert 'Control-a: beginning-of-line'
# Ctrl-E: append at line end like in emacs mode
bind -m vi-insert 'Control-e: end-of-line'
# Ctrl-D: delete character
bind -m vi-insert 'Control-d: delete-char'
# Ctrl-L: clear screen
bind -m vi-insert 'Control-l: clear-screen'

## Emacs bindings
# Meta-V: go back to vi editing
bind -m emacs '"\ev": vi-editing-mode'

export EDITOR='vim'

# enable vi mode
set -o vi


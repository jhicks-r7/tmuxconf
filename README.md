# Installation
Kill any Tmux Sessions:

`tmux kill-server`

Clone the repo to ~/.config/tmux:

`git clone https://github.com/jhicks-r7/tmuxconf ~/.config/tmux`

Clone the Tmux Plugin Manager (TPM)

`git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm`

Start Tmux, then input `prefix + Shift-i` (prefix key is Ctrl-Space) to install the remaining plugins

# What and how
This is my custom Tmux configuration, including plugins. I use it in both personal things and when doing pentests.

## Hotkeys
### Prefix
In this configuration, the prefix key has been changed to ctrl+space. You can change it to what you want by modifying lines 16 and 17:
```
set -g prefix C-space
bind C-Space send-prefix
```
But i'd recommend keeping it ctrl+space because it is the best.

The rest of these are keybinds I use, but are not the only keybinds provided by modules

### Logging
Toggle logging for the current pane: `prefix + Shift-p`

Capture current pane:     `prefix + Alt-p`

Save complete history:    `prefix + Alt-Shift-p`

Clear pane history:       `prefix + Alt-c`

### Saving and loading panes
Save:                     `prefix + Ctrl-s`

Restore:                  `prefix + Ctrl-r`

### Navigation with Vim Tmux Navigator
Left:                     `Ctrl-h`

Down:                     `Ctrl-j`

Up:                       `Ctrl-k`

Right:                    `Ctr-l`

Previous Split:           `Ctrl-\`

## The Modules
### Tmux Plugin Manager (TPM)
https://github.com/tmux-plugins/tmux-sensible

The plugin manager. Manages plugins.

### Tmux Sensible
https://github.com/tmux-plugins/tmux-sensible

A group of sensible Tmux configurations

### Vim Tmux Navigator
https://github.com/christoomey/vim-tmux-navigator

Allows for navigating between vim panes and tmux splits using vim keybinds, see the hotkeys!

### Catppuccin-Tmux
https://github.com/dreamsofcode-io/catppuccin-tmux

Just a theme. My favorite theme. I use a slightly modified one from @Dreamsofcode-io

### Tmux Yank
https://github.com/tmux-plugins/tmux-yank

Allows for some configuration with copying to the system clipboard. Also has some keybindings that I don't use, but probably should

### Tmux Logging
https://github.com/jhicks-r7/tmux-logging

Allows for logging of Tmux panes. I have a slightly modified fork that I use, which I changed some of the sed replacements for control characters in the original. The control characters I'm removing (and the ones I'm leaving) work with the current version of Kali AND my particular prompt color settings to produce a greppable, but still colored, log output.
When utilizing this for engagements, instead of having to manually toggle logging (see keybinds), I will add the folowing to my .zshrc/.profile/whatever is appropriate to have it start up atuomatically on every new pane/window/session:
```
if [ "$TERM_PROGRAM" = tmux ]; then
    ~/.config/tmux/plugins/tmux-logging/scripts/toggle_logging.sh
fi
```
### Tmux Resurrect
https://github.com/tmux-plugins/tmux-resurrect

Adds the ability to save and restore sessions in the case that a host needs rebooted, or crashes (see below for the latter)

### Tmux Continuum
https://github.com/tmux-plugins/tmux-continuum

Works in conjunction with Tmux Resurrect and auto-saves your session every 15 minutes for restoration. Also has options for configuring auto-starting and auto-restoring

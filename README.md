# tmux cheat sheet
tmux cheat sheet and other settings.

### general 

* C+q is the prefix key
* recommanded (in _.tmux.conf_):
```
set -g default-command "reattach-to-user-namespace -l $SHELL"
unbind -t emacs-copy M-w
bind-key -t emacs-copy M-w copy-pipe "reattach-to-user-namespace pbcopy"
```

* `c` to `ctrl`, `m` to `meta` 
* iterm2 > profile > keys > option key acts as `+Esc`
* default (emacs style key bindings) 


### command line

1. ```$ tmux attach -t target```
2. ```$ tmux new-session -s name```
3. ```$ tmux list-sessions / tmux ls```
4. ```$ tmux kill-session -t target```

### pane

1. `o` switch pane orderly 
2. `"` / `%` split pane 
3. `c+arrow` / `m+arrow` resize pane slowly / quickly
4. `c+o` rotate panes / `{` / `}` swap this pane with the previous / next one
5. `x` kill pane

### session 

1. `$` rename session 
2. `S` switch to another session
3. `(` / `)` cycle through sessions
4. `r`  refresh this client
5. `d` / `D` detach yourself / someone from session 

### window

1. `c` create window
2. `0...9` choose window
3. `n` / `p` next / previous window
4. `w` list windows
5. `l` switch to last window
6. `&` kill window
7. `,` rename window

### misc

1. `:` enter command
2. `?` list key bindings
3. `t` show clock
4. `i` display information

### copy mode 

1. `[` enter copy mode
2. `]` paste (with in tmux) 
3. `c+space` / `shift + ctrl + 2` start selection 
4. `m+w` copy

### others 

use vi mode and other customize key bindings (in _.tmux.conf_)

ps: your life won't be easy with these settings, until you copy them to every machine you have.

```
setw -g mode-keys vi
set-window-option -g mode-keys vi
bind-key -t vi-copy v begin-selection
bind-key -t vi-copy y copy-pipe "reattach-to-user-namespace pbcopy"
unbind -t vi-copy Enter
bind-key -t vi-copy Enter copy-pipe "reattach-to-user-namespace pbcopy"

# vim style pane movement
bind C-h select-pane -L
bind C-j select-pane -D
bind C-k select-pane -U
bind C-l select-pane -R

# pane re-sizing
bind -r H resize-pane -L 20
bind -r J resize-pane -D 20
bind -r K resize-pane -U 20
unbind L
bind -r L resize-pane -R 20

# split pane
unbind C-s
unbind C-v
bind C-v split-window -h
bind C-s split-window -v

unbind l
bind C-p previous-window
bind C-n next-window

unbind-key C-r
bind R source-file '/path/to/home/.tmux.conf'

# plugins
set -g @plugin 'tmux-plugins/tmux-sidebar'

run '~/.tmux/plugins/tpm/tpm'
```

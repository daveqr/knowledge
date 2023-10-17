# tmux

## Config 

### Remap the prefix from 'C-b' to 'C-a'

```
unbind C-b
set-option -g prefix C-a
bind-key C-a send-prefix
```

### Split panes using | and -
```bind | split-window -h
bind - split-window -v
unbind '"'
unbind %
```

## Quick commands

* Navigate panes: `C-a arrow`
* Create window: `C-a c`
* Split pane vertically: `C-a |`
* Split pane horizontally: `C-a -`
* Detach current session: `C-a d`
* List current sessions: `$ tumux ls`
* Attach to sessions: `$ tmux attach -t 0`
* Create session with name: `$ tmux new -s database`
* Rename existing session: `tmux rename-session -t 0 database`
* Make page full-screen: `C-a z`

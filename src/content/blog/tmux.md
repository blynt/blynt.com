---
title: "tmux - boosting your terminal experience"
publishDate: "9 november 2024"
description: "tmux - the terminal multiplexer"
---

Even though I generally expect apps to have sensible defaults and thus restrain
from playing too much with their configuration, there is one setting I always
update when I open a new terminal emulator. That is which command to run when it
starts. I always pick `tmux`.

Many terminal emulators support opening shells in tabs and splitting windows
into horizontal or vertical panels. This is functionality that’s entirely
redundant because that’s one of the core features of `tmux`.

With `tmux` I can bring that functionality with me regardless of which app I use
to access the shell with no need to learn new keyboard shortcuts when I borrow a
friend’s esoteric Windows machine to `ssh` to my Linux box.

But `tmux` is more than just that. It also allows me to detach from a session and
resume it later. This is a feature that I use all the time. At home I have my
workstation running all the time with a bunch of `tmux` sessions open (remember,
the only setting I change).

So when I'm out and about and using my laptop, I can just `ssh` back home and
type `tmux`, hit `Ctrl-b w` to scroll through all my `tmux` windows and dig up
that old `vim` session I was working in. Magic!

![](/blog/tmux/tmux-01.webp)

*Three panels in a tmux window.*

## Installation

On Debian-based systems, installing `tmux` is as simple as:

```bash
sudo apt install tmux
```

The `man` page will of course provide you with everything you need to know about
`tmux`, but here is the list of commands I use the most:

## When not in tmux

- `tmux` - start a new session
- `tmux ls` - list all sessions
- `tmux a -t <session>` - attach to a running session

## When in tmux

When you're inside `tmux`, you can interact with it by using the `Ctrl-b` prefix
and then issue a command. Here are the ones I use the most:

### Full-screen windows

- `Ctrl-b c` - create a new full-screen window
- `Ctrl-b <number>` - move to window `<number>`

![](/blog/tmux/tmux-02.apng)

*Window management in `tmux`.*

### Splitting windows into panes

- `Ctrl-b %` - split the window vertically
- `Ctrl-b "` - split the window horizontally
- `Ctrl-b q` - show pane numbers (then hit the number to move to that pane)
- `Ctrl-b z` - zoom pane to full-screen (hit `Ctrl-b z` again to zoom back)
- `Ctrl-b x` - kill the current pane (e.g if some app is stuck)
- `Ctrl-b Ctrl-arrow keys` - resize the pane
- `Ctrl-b !` - move the current pane into a new window

![](/blog/tmux/tmux-03.apng)

*Managing panes in `tmux`.*

### Switching between sessions

- `Ctrl-b s` - list sessions
- `Ctrl-b w` - choose a session from a list (with all windows)
  - Use arrow keys to navigate (or `j` and `k`)
  - Use `/` to search for a window
- `Ctrl-b d` - detach from the current session (and leave it running)

![](/blog/tmux/tmux-04.apng)

*Listing sessions + listing windows and finally jumping to `ncspot`.*

### Finding and copying text

- `Ctrl-b [` - enter copy mode
  - Use arrow keys to navigate (or `j` and `k`)
  - Use `Space` to start selecting text
  - Use `Enter` to copy the selected text
- `Ctrl-b ]` - paste the copied text

![](/blog/tmux/tmux-05.apng)

*Copying text from one pane to a `vim` session running in another.*

### Miscellaneous

- `Ctrl-b t` - show the time
- `Ctrl-b ?` - show all key bindings (saves the day!)

## Configuration

Even though I started this post by saying that I don't like to fiddle with the
settings of my apps, I have set some config options to boost my `tmux`
experience.

Essentially what I do is the following:

- I turn on mouse support:
  - I.e. I can scroll in windows and switch windows / panes with the mouse.
- Whenever I copy text (as described above), tmux also runs it through `xsel`
  so that I can paste it with `Ctrl-v` in any graphical app (you can update this
  to whatever clipboard manager you use).
- I turn on `vi` key bindings for scrolling, etc.
- I install a few plugins through the [`tpm` plugin manager][tpm]:
  - [`tmux-sensible`][tmux-sensible] just provides some sensible defaults.
  - [`dracula`][dracula] is the color scheme you see in all screenshots.
  - [`tmux-powerline`][tmux-powerline] adds a status line at the bottom of the screen.


Here is my full `~/.tmux.conf`:

[tpm]: https://github.com/tmux-plugins/tpm
[tmux-sensible]: https://github.com/tmux-plugins/tmux-sensible
[dracula]: https://github.com/dracula/tmux
[tmux-powerline]: https://github.com/erikw/tmux-powerline

```bash
set -g mouse on
set -s copy-command 'xsel -b'
set -g mode-keys vi
set -g pane-border-status top
set -g pane-border-format "#{pane_index}: #{pane_current_command}"
set -g default-shell /bin/bash

# List of plugins
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-sensible'
set -g @plugin 'dracula/tmux'

set -g @plugin 'erikw/tmux-powerline'

# Fix true colors
set-option -sa terminal-overrides ',XXX:RGB'

# Capture the pane title and set it to the window title
set -g set-titles on
set -g set-titles-string '#I:#P: #{pane_current_command}'

set -g default-shell /usr/bin/bash

# Initialize TMUX plugin manager (keep this line at the very bottom)
run '~/.tmux/plugins/tpm/tpm'
```

If you haven't already, make sure to give `tmux` a try!

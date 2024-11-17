---
title: "Navigating the command line"
description: "How to effectively navigate your shell's command line"
publishDate: "17 november 2024"
---

One of the first jobs I got in IT was at a [local
webhost](https://www.loopia.se/). That was exactly 20 years ago and at that time
I was an avid Emacs user who had learned enough Perl[^1] to use it to provide
the business logic of my hobby websites as
[CGI](https://en.wikipedia.org/wiki/Common_Gateway_Interface) scripts.

The ones who influenced me the most at that place were the devops guys[^2]. They
were heavy vim users and smirked at my Emacs usage. They also influenced me to
start using PHP in favor of Perl as that performed much better with the
`mod_php` module that they had installed on the webservers.

Slowly but surely, my Perl scripts became PHP scripts and Emacs was soon
replaced by [vim](https://www.vim.org/) (and later
[neovim](https://neovim.io/)). While PHP has since fallen out of fashion, vim is
still my editor of choice - it's perfect in the terminal and you can find it on
every Unix-like system out there.

It's interesting what you might get influenced by.

So why do I mention this?

Besides the quite inefficient "Windows" way of navigating text (using the arrow
keys), learning both Emacs and vim means you know how to effectively input text
using the most commonly used ways of doing so (at least to my knowledge).

I guess the most commonly used shells are `bash` (default on most Linux distros)
and `zsh` (default on MacOS). Both of these shells default to Emacs-like
keybindings[^3]. Interestingly enough, both support vi keybindings as well, but
I've never seen anyone using them. And to be honest, even for vim users, Emacs
keybindings work so much better in the shell.

So if you want to effectively input text in the shell, don't cheat by using the
arrow keys. Take the time to learn basic Emacs keybindings. It will pay off in
the long run.

There are a few keybindings that are essential to know:

Navigation with `Ctrl`:

- `Ctrl-a` - move to the beginning of the line
- `Ctrl-e` - move to the end of the line
- `Ctrl-u` - delete from the cursor to the beginning of the line
- `Ctrl-k` - delete from the cursor to the end of the line
- `Ctrl-w` - delete the word before the cursor
- `Ctrl-d` - delete character under cursor (or exit shell if line is empty)

Navigation with `Alt` (Meta):

- `Alt-f` - move forward one word
- `Alt-b` - move backward one word
- `Alt-d` - delete the word after the cursor
- `Alt-Backspace` - delete the word before the cursor

Extras with `Ctrl`:

- `Ctrl-r` - search backwards in history
- `Ctrl-s` - search forwards in history
- `Ctrl-p` - go to the previous command in history
- `Ctrl-n` - go to the next command in history
- `Ctrl-y` - paste the last deleted text
- `Ctrl-l` - clear the screen
- `Ctrl-c` - kill the current process
- `Ctrl-z` - suspend the current process (use `fg` to resume)
- `Ctrl-Shift-c` - copy the selected text
- `Ctrl-Shift-v` - paste the copied text

Extras with `Alt`:

- `Alt-t` - transpose characters before cursor with the character under cursor
- `Alt-y` - paste the last deleted text
- `Alt-?` - show the list of all possible completions
- `Alt-*` - insert all possible completions
- `Alt-~` - expand the current word to all possible completions

If you need to type in a commond that spans multiple lines, I'm sure you know
that you can use '\\' and 'Enter' to continue on the next line, like so:

```bash
curl -X POST \
     -H "Content-Type: application/json" \
     -d '{"key": "value"}' \
     https://example.com
```

The problem with this approach, however, is that if you want to go back and edit
something on a previous line, you're stuck.

What will save the day is hitting `Ctrl-x Ctrl-e` which will open the command in
your default editor (in my case, vim). Now it's super-easy to edit the command
in the comfort of your favorite editor, and when you're done, just save and exit
and the command will execute.

Oh, by the way. This is how you can enable `vi keybindings`.

In `bash`:

```bash
set -o vi
```

In `zsh`:

```zsh
bindkey -v
```

But please just ignore this and learn the Emacs keybindings instead[^4].

[^1]: Back then, this knowledge had to be acquired by reading actual books!
[^2]: But this wasn't really a word back then.
[^3]: If this is because [Richard
      Stallman](https://en.wikipedia.org/wiki/Richard_Stallman) is the original
      author of Emacs, I don't know.
[^4]: Emacs keybindings is the default in the `readline` utility used by many
      applications, so don't be surprised if you can hit `Ctrl-n` or `Ctrl-p` when
      scrolling through options. Also, if you're using Gnome as your desktop
      environment, you can enable Emacs keybindings for all input fields so that you
      have a consistent way of navigating text everywhere.

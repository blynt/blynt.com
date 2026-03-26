---
layout: '../../layouts/Page.astro'
title: "vim Cheatsheet"
---

## Enable soft linebreaks with markers

```vim
:set wrap             # Wrap long lines
:set linebreak        # Break lines at word boundaries
:set showbreak=+      # Show a plus sign at the end of a line that is wrapped
```

## Search and replace across multiple files

Load all files into argument list:

```
:args **/*.md
```

Search and replace (and save):

```
:argdo %s/old/new/g | w
```

- `:argdo` runs a command on all files in the argument list

## Splits

### Zooming

Maximize horizontal split:

```
Ctrl-w _
```

Maximize vertical split:

```
Ctrl-w |
```

Restore split:

```
Ctrl-w =
```

### Swapping

Swap splits horizontally (swap right (L), swap left (H)):

```
Ctrl-w L/H
```

Swap splits vertically (swap down (J), swap up (K)):

```
Ctrl-w J/K
```

### Resizing

Resize split horizontally (increase (>) and decrease (<)):

```
Ctrl-w >/<
```

Resize split vertically (increase (+) and decrease (-)):

```
Ctrl-w +/-
```

## Scrolling

One row up and down:

```
Ctrl-e   // Down
Ctrl-y   // Up
```

Half page up and down:

```
Ctrl-d   // Down
Ctrl-u   // Up
```

## Diff between two splits

In each split, type:

```
:diffthis
```

Then, to turn off diff:ing:

```
:diffoff
```

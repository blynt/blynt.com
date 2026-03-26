---
layout: '../../layouts/Page.astro'
title: "Linux random Cheatsheet"
---

## Truncating Video

Remove the first 10 seconds of a video (length in HH:MM:SS format):

```bash
ffmpeg -i input.mp4 -ss 00:00:10 -c copy output.mp4
```

Remove the last 10 seconds of a video:

```bash
ffmpeg -i input.mp4 -t 00:00:10 -c copy output.mp4
```

## Static webserver with Python

Serve the current directory on port 8000:

```bash
python3 -m http.server 8000
```

## List block devices (e.g. for mounting USB drives)

```bash
lsblk
```

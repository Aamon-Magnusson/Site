+++
title = "Tmux"
date = "2022-11-29T22:10:35-07:00"
author = "Aamon"
tags = ["How-To", "Software"]
description = "My beginners guide to `tmux`."
showFullContent = false
readingTime = true
hideComments = false
+++

# Intro

`tmux` is a well known *terminal multiplexer*.
I like to think of it as a window manager for within terminal sessions.
Allowing the user to have multiple terminal sessions within a single terminal session, in the form of splits or tabs.

I'm going to be honest, I've been against learning `tmux` for some time.
I found that `DWM` was enough terminal control for me, until I started using server `ssh` sessions more often.
I'm no server admin, but just using `ssh` for this site, and some work I do is enough for me to begin to appreciate being able to use multiple terminal sessions.
(Now I just run a `kali` laptop behind me a use `ssh` to run whatever I need on that machine)

`DWM` allows me to show as many terminals as I want at a given time, or to put them over top of each other.
However, if I'm using `ssh` it will not use the same session.
What I had done in the past was just open up the `ssh` session in the new terminal should I need it, but this gets annoying, especially if I'm using Windows.
Now with the use of `tmux` I do much more from the same window.
As I write this I still have 3 terminal windows open at the same time, but each is running a different machine's shell.

---

# Keybindings

As it is a terminal program the most important thing to learn are keybindings.
I have not changed any keybindings, as this makes it easier to jump between different machines.

The most important keybinding is going to be the ***prefix***.
The prefix is what tells `tmux` that you are telling it to do something, and not some other program.
The default is `<C-b>`.
The *pre*fix will lead each command, similar to the `<leader>` key in `Vim`.
Like `<C-b> c`, for example.

```
<C-b> c New tab
<C-b> " New horizontal split
<C-b> % New vertical split

<C-b> & Close tab
<C-b> x Close split
<C-b> d Detach from session

<C-b> n Next tab
<C-b> p Previous tab
<C-b> <number> Move to respective tab
<C-b> <arrow key> Move to respective split

<C-b> , Rename tab

<C-b> [ Allow scrollback with arrow keys

<C-b> ? Help menu for keybindings
```

# Conclusion

I am far from an advanced `tmux` user.
But I think the keybindings above should make for an easy entry into `tmux`.
Pretty much just tabs and splits.

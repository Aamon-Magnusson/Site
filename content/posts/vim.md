+++
title = "Vim"
date = "2022-11-21T20:18:28-07:00"
author = "Aamon"
#authorTwitter = "" #do not include @
#cover = ""
tags = ["How-To", "Vim", "Software"]
#keywords = ["", ""]
description = "Here's my guide for how I would recommend you learn `Vim`."
showFullContent = false
readingTime = true
hideComments = false
#colour = "" #colour from the theme settings
+++

# Intro

`Vi`, `Vim`, `Neovim`...

The `Vi` based text editors are known for their complexity, nuance, and speed, for those who learn it.

I happen to love using `Neovim` as my primary text editor, and find it super beneficial to writing and editing text files.
I do try to use text files more often than the average person, using `Markdown` where ever possible over Word, or other word processors, for example.

This post will go over the way I learned `Vim`, and how I would recommend someone you learn it.
(Pretty much all `Vim`-like text editors will apply to this post, as I will barely go into configuration, it's all about the `Vim`-like actions)

# `vimtutor`

The first step should always be `vimtutor`.
Just run the program in your terminal, and the team behind `Vim` will show you some important first keybindings.
It is not expected that you learn everything there, but a good portion of them are very useful.
Like you should know `hjkl`, `dcyp`, `web`, `iaIA`, `vV<c-v>`, `ggG<c-d><c-u>`, and of course `:q` and `:wq`.
If after `vimtutor` any of these groups, and letters don't make sense, I would recommend going back and reviewing what they mean.
By no means would I expect you to be able to use these super quick either, that will take practice, but the exposure is what will get you started.

# Configuration

I know I said I wouldn't go into configuration, but there are some defaults that I feel should come default.

If you're running standard `Vim` your configuration is done in `~/.vimrc`.
For `Neovim` it's in `~/.config/nvim/init.vim` or `init.lua` if you want to get fancy.
(I would recommend the `init.vim` for now, just keeps it the same as `Vim`)

The classic way to configure `Vim` is with `Vimscript`, a language made for `Vim`.
Below are some simple configurations I would make to a new config:

```vimscript
" Line numbers (This is really important)
set nu
set relativenumber
" Get rid of those annoying errorbells
set noerrorbells
" I like 4 space tabs, fight me
set tabstop=4
set shiftwidth=4
" Get syntax highlighting
syntax enable

" More advanced but comes default in Neovim
" Keeps Y more consistent with the other capital letters
nmap Y y$
```

These are the absolute bare minimum configurations I would use, but you may come to see that many write far more into their configs.
As I do as well.
I wouldn't recommend you go too crazy for now, as it's good to learn the basics of `Vim` before adding features, and you may be surprised, `Vim` can do a heck of a lot.
In in any case, you would like to see my real configs just check out [my Dotfiles](https://github.com/Aamon-Magnusson/Dotfiles/tree/main/nvim).

# Next Steps

From there I would recommend using `Vim` or `Neovim`.
Try to use the keybindings I mentioned above in the [`vimtutor` section](#vimtutor).
Adding stuff like:

```vimscript
nnoremap <Up> <Nop>
nnoremap <Down> <Nop>
nnoremap <Left> <Nop>
nnoremap <Right> <Nop>
```

Could help force you into `Vim` motions, but I never did that.
Many do recommend it, IDK.
¯\\\_(ツ)\_/¯

As you learn what you can't do with these simple motions Google if there's a `Vim` way to go it.
You should also end up learning the `:help` pages.
They take some practice but can be handy.

From there I would slowly adding keybindings.
Add a leader key:

```vimscript
set mapleader = " "
```

And map any little functions you want.
Like this:

```vimscript
" Enable spell check
nnoremap <leader>se :set spell spelllang=en_ca<CR>
nnoremap <leader>sf :set spell spelllang=fr_ca<CR>
nnoremap <leader>so :set nospell<CR>

" Fix last spelling error
function! FixLastSpellingError()
  normal! mm[s1z=`m"
endfunction
nnoremap <leader>sl :call FixLastSpellingError()<cr>
```

For example.

Some can be just commands you don't want to remember, or type in over and over again.
Or you can add functionality through the power of `Vimscript`.
(Or `Lua`)

After that you can always add plugins, I just feel this should be the last step, and only add what you think you're missing.

# Conclusion

And there's how I would recommend learning `Vim`.
Keep in mind this is not a fast process.
It took me about a year, to finally get comfortable in `Vim`.
And even then it was continuous improvement to my config, and my skills.

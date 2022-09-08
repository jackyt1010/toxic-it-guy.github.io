---
layout:     post
title:      "Vim Tips and tricks"
subtitle:   ""
description: ""
date:       2022-08-24 
author:  Jacky Tang
published: true
tags:
    - Tips
    - Vim
URL: "/2022/08/24/vim-tips/"
categories: [ Computer Science ]
---

<!--more-->
## Vim Jumps

* ^ — Move to start of line
* $ — Move to end of line
* b — Move back a word
* w — Move forward a word
* e — Move to the end of the next word
* Ctrl-o and Ctrl-i to go to the previous/next location you jumped to
* ``(two backticks) jump back to where you were
* gi go back to the last place you inserted a text and enter insert mode

## Vim Navigations

* { and } jump paragraph back and forth
* Ctrl-F/B move one screen back and forth
* Search the word under cursor, then n/p to jump to next/previous 


## Enable Vim mode in bash
vi ~/.inputrc
set editing-mode vi

## Enable system clipboard upport

See if system clipboard is supported:     
```
$ vim --version | grep clipboard
-clipboard       +iconv           +path_extra      -toolbar
+eval            +mouse_dec       +startuptime     -xterm_clipboard
```

Rinstall vim as vim-gnome:   
```
sudo apt-get install vim-gnome
```
Select what you want using the mouse - then type to copy to clipboard:  
```
"+y
```

To paste to vim from clipboard type:  
```
"+p
```
## Others
* Ex: open the current directory
* set number: show line number

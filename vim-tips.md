
### Command Line Shortcuts
http://stackoverflow.com/a/6921029/467034
```
Paste Ctrl+R "
:di
:display
Paste Ctrl+R 0
```

### Macros
```
qa
5@a
```

### Marks
```
ma
'a
```

### Shortcuts
```
Visted locations
:jumps
Ctrl-O Jump back
Ctrl+I Jump forward

Increase Number and Letter
Ctrl+A Inrease
Ctrl+X Decrease
~ Capitalize
```

### Selection to clipboard

```
:'<,'>!xclip -sel clip
:.!xclip -o
:.!xclip -o | html2jade
:.!filget rocks
```

### Folding
```
Unfold zR
```

### Tab
```
set shiftwidth=2
```

### Lines
```
Delete lines not containing the word function
:g!/function/d 
```

### Colors
https://github.com/altercation/vim-colors-solarized
```
:colorscheme hybrid
:colorscheme hybrid-light

set background=dark
set background=light
colorscheme solarized
```

### Plugins
```
:'<,'>Tabularize /,
```

https://github.com/tpope/vim-pathogen

https://github.com/nodejs/node-v0.x-archive/wiki/vim-plugins

http://stackoverflow.com/questions/14226390/how-to-use-nerd-commenter-for-vim-how-to-use-leader-key
```
" o es , o es \
let mapleader=","
set timeout timeoutlen=1500
```

https://github.com/scrooloose/nerdcommenter#usage

http://vimawesome.com/plugin/the-nerd-commenter

Nerd Commenter
```
cm
cu
cc
```



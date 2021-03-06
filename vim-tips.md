
CheatSheet

| Shortcut / Cmd | Description | Plugin |
|:-- | :-- | --- | 
| `3\cu` | Uncomment 3 lines | NerdComenter


### Replace last occurence
http://stackoverflow.com/questions/11865845/replace-last-occurrence-in-line
```
:%s/.*\zsone/two/
```

Add new line after N repetitions

```
:.s/\(\(\d\+ \)\{16\}\)/\1\r/gc
```
Turns this:

```
2 13 51 36 18 97 67 27 157 105 32 232 157 44 321 217 4 21 49 34 30 94 64 39 153 103 50 227 153 66 316 211 6 25 46 32 36 91 61 47 149 100 59 223 149 78 310 205
```

into this:
```
2 13 51 36 18 97 67 27 157 105 32 232 157 44 321 217 
4 21 49 34 30 94 64 39 153 103 50 227 153 66 316 211 
6 25 46 32 36 91 61 47 149 100 59 223 149 78 310 205
```

### Delete or change till occurence

```
dT0 -> deletes from the cursor to begining of line
dt$ -> from cursor to eol
cw -> deletes next word and let you keep editing
ci" -> removes the text inside " and let you edit
cit -> remvoes text inside html tag and let you edit
```


### Command Line Shortcuts
http://stackoverflow.com/a/6921029/467034
```
Paste Ctrl+R "
:di
:display
Paste Ctrl+R 0
```

Copy a word and save it under `"b` to paste it in the command prompt, with the cursor on the start of word

```
"byw
```

Then go to the prompt `:` and press Ctrl+R b, and there you go.



### Repeat

- `;` repeats movements
- `.` repeats actions


### Macros
```
qa
5@a
:g/pattern/norm! @a
```
- [Apply macro to certain lines](http://stackoverflow.com/a/390194/467034)

### Marks
```
ma
'a
```
Go to the last mark `''`

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

You can also paste by doing
```
"+p
```

http://unix.stackexchange.com/a/199222/92183

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

### Non-greedy

``` 
find $sec -type f -exec sed -i "s#customers#companies#g" "{}" +;
```

If we want to strip the first part `:%s/.*#/new-replacement-here/` would be a problem basically we use `\{-}` instead of `*` so we change to `:%s/.\{-}#/new-replacement-here/`.

The same can happen if you want to change the last part `:%s/#.*//` would be a problem, basically we can use `%s/.*\zs#.*/',/c`

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

Remove Tricks

```
http://stackoverflow.com/a/26908890/467034
J
```

Extra

- [Multiple commands at once](http://vim.wikia.com/wiki/Multiple_commands_at_once)


## redirect output to quickfix

 Quick fix example usage, see sending stdout to Quickfix http://stackoverflow.com/a/18119235/467034

```
:grep -nir "a" ./b-folder
:copen
:new|0read !grep -nir "a" ./b-folder
```



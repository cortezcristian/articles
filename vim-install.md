## Everything

- 1. Pathogen

```
sudo apt-get install curl vim git
mkdir -p ~/.vim/autoload ~/.vim/bundle && \
curl -LSso ~/.vim/autoload/pathogen.vim https://tpo.pe/pathogen.vim
```

- 2. Add to ~/.vimrc
```
mkdir ~/.vimbackuptemp
touch ~/.vimrc
```

- 2.1 New clean version
```
" Globals
" ------------------
set smartindent
set tabstop=2
set shiftwidth=2
set softtabstop=2
set expandtab
set hlsearch
set number
set cursorline
set encoding=utf-8
" for nerd commenter
filetype plugin on

" Shortcuts
" ------------------
set pastetoggle=<F2>
"let mapleader=","
"set timeout timeoutlen=1500
map <F3> :NERDTreeToggle <cr>
map <F2> :tabnext <cr>
map <F5> :w <cr>
map <F6> !xclip -sel clip <cr> u <cr>
" use pbcopy in mac
" INCREMENTING ALPHA STRINGS WITH VIM : Ctrl+a Ctrl+x
" http://blog.mozilla.org/jv/2011/01/12/incrementing-alpha-strings-with-vim/
set nf=octal,hex,alpha

" Folding
" ------------------
set foldmethod=syntax
set foldlevelstart=1
let javaScript_fold=0         " JavaScript
let perl_fold=1               " Perl
let php_folding=1             " PHP
let r_syntax_folding=1        " R
let ruby_fold=1               " Ruby
let sh_fold_enabled=1         " sh
let vimsyn_folding='af'       " Vim script
let xml_syntax_folding=1      " XML

" Backups
" ------------------
" Directory backup
" http://stackoverflow.com/questions/4824188/git-ignore-vim-temporary-files
set backupdir=~/.vimbackuptemp
set directory=~/.vimbackuptemp
" set backupdir=./.backup,.,~/.vimbackuptemp
" set directory=.,./.backup,~/.vimbackuptemp

" Colors
" ------------------
" Color schema
colorscheme hybrid
"set background=dark
"set background=light
"colorscheme solarized
"
"set background=dark
"syntax on
"color mango

" Plugin: vim-gitgutter
" https://github.com/airblade/vim-gitgutter
" ------------------
nmap <Leader>ha <Plug>GitGutterStageHunk
nmap <Leader>hu <Plug>GitGutterRevertHunk
let g:gitgutter_override_sign_column_highlight = 0
let g:gitgutter_sign_column_always = 1

" Plugin: syntastic
" https://github.com/scrooloose/syntastic
" ------------------
set statusline+=%#warningmsg#
set statusline+=%{SyntasticStatuslineFlag()}
set statusline+=%*
let g:syntastic_always_populate_loc_list = 1
let g:syntastic_auto_loc_list = 1
let g:syntastic_check_on_open = 1
let g:syntastic_check_on_wq = 0
let g:syntastic_javascript_checkers = ['jshint']

" Plugin: vim-jsbeautify
" https://github.com/maksimr/vim-jsbeautify
" ------------------
":call HtmlBeautify()
let g:config_Beautifier = {}
let g:config_Beautifier['html'] = {}
let g:config_Beautifier['html'].indent_size = '2'
let g:config_Beautifier['js'] = {}
let g:config_Beautifier['js'].indent_size = '2'
"Do Ctrl+F on selection
autocmd FileType javascript vnoremap <buffer>  <c-f> :call RangeJsBeautify()<cr>
autocmd FileType json vnoremap <buffer> <c-f> :call RangeJsonBeautify()<cr>
autocmd FileType jsx vnoremap <buffer> <c-f> :call RangeJsxBeautify()<cr>
autocmd FileType html vnoremap <buffer> <c-f> :call RangeHtmlBeautify()<cr>
autocmd FileType css vnoremap <buffer> <c-f> :call RangeCSSBeautify()<cr


" Plugin: vim-pathogen
" https://github.com/tpope/vim-pathogen
" ------------------
execute pathogen#infect()

```

- 2.2 Old Version
```
"execute pathogen#infect()
let g:php_xdebug=1 "1 to turn this on :D
let g:vdebug_options = {}
let g:vdebug_options["port"] = 9000
set pastetoggle=<F2>
set smartindent
set tabstop=4
set shiftwidth=2
set expandtab
set number
" for nerd commenter
filetype plugin on
"let mapleader=","
"set timeout timeoutlen=1500
map <F3> :NERDTreeToggle <cr>
map <F2> :tabnext <cr>
map <F5> :w <cr>
map <F6> !xclip -sel clip <cr> u <cr>

" Toggle auto complete
"
function! YouCompleteMeFixToggle()
    if g:ycm_auto_trigger
        let g:ycm_auto_trigger = 0
    else
        let g:ycm_auto_trigger = 1
    endif
endfunction

map <F7> :call YouCompleteMeFixToggle() <cr>
" set statusline=%F%m%r%h%w\ [FORMAT=%{&ff}]\ [TYPE=%Y]\ [ASCII=\%03.3b]\ [HEX=\%02.2B]\ [POS=%04l,%04v]\ [%p%%]\ [LEN=%L]
set cursorline
set encoding=utf-8

" Folds
set foldmethod=syntax
set foldlevelstart=1

let javaScript_fold=0         " JavaScript
let perl_fold=1               " Perl
let php_folding=1             " PHP
let r_syntax_folding=1        " R
let ruby_fold=1               " Ruby
let sh_fold_enabled=1         " sh
let vimsyn_folding='af'       " Vim script
let xml_syntax_folding=1      " XML
" Folds END

" INCREMENTING ALPHA STRINGS WITH VIM
" http://blog.mozilla.org/jv/2011/01/12/incrementing-alpha-strings-with-vim/
set nf=octal,hex,alpha

" Directory backup
" http://stackoverflow.com/questions/4824188/git-ignore-vim-temporary-files
set backupdir=~/.vimbackuptemp
set directory=~/.vimbackuptemp
" set backupdir=./.backup,.,~/.vimbackuptemp
" set directory=.,./.backup,~/.vimbackuptemp

" Airline
let g:airline_powerline_fonts = 1
let g:airline_enable_branch     = 1
let g:airline_enable_syntastic  = 1

set statusline=AAA%F%m%r%h%w\ 
set statusline+=%{fugitive#statusline()}\    
"set statusline+=[%{strlen(&fenc)?&fenc:&enc}]
"set statusline+=\ [line\ %l\/%L]          
"set statusline+=%{rvm#statusline()}  

" http://vim.wikia.com/wiki/Displaying_status_line_always
set laststatus=2
set ttimeoutlen=50
let g:airline_theme = 'powerlineish'
let g:airline_theme = 'kolor'
set t_Co=256
let g:airline#extensions#hunks#enabled=0
let g:airline#extensions#branch#enabled=1

if !exists('g:airline_symbols')
  let g:airline_symbols = {}
endif
let g:airline_symbols.space = "\ua0"
" unicode symbols
let g:airline_left_sep = '»'
let g:airline_left_sep = '▶'
let g:airline_right_sep = '«'
let g:airline_right_sep = '◀'
let g:airline_symbols.linenr = '␊'
let g:airline_symbols.linenr = '␤'
let g:airline_symbols.linenr = '¶'
let g:airline_symbols.branch = '⎇'
let g:airline_symbols.paste = 'ρ'
let g:airline_symbols.paste = 'Þ'
let g:airline_symbols.paste = '∥'
let g:airline_symbols.whitespace = 'Ξ'

let g:airline_left_sep = ''
let g:airline_left_alt_sep = ''
let g:airline_right_sep = ''
let g:airline_right_alt_sep = ''
let g:airline_symbols.branch = ''
let g:airline_symbols.readonly = ''
let g:airline_symbols.linenr = ''

let g:airline#extensions#tabline#enabled = 1
let g:airline#extensions#tabline#left_sep = ''
let g:airline#extensions#tabline#left_alt_sep = ''

"let g:airline_section_a = 'b%n, w%{winnr()}%#__accent_bold#%{winnr()==winnr("#")?" [LW]":""}%#__restore__#
function! AirlineInit()
    let g:airline_section_a = airline#section#create(['mode', '', 'branch', '%{fugitive#statusline()}'])
    let g:airline_section_b = airline#section#create_left(['ffenc','file'])
    let g:airline_section_c = airline#section#create(['%{getcwd()}'])
endfunction
"autocmd User AirlineAfterInit call AirlineInit()

" vim-gitgutte
nmap <Leader>ha <Plug>GitGutterStageHunk
nmap <Leader>hu <Plug>GitGutterRevertHunk
let g:gitgutter_override_sign_column_highlight = 0
let g:gitgutter_sign_column_always = 1

" Color schema
colorscheme hybrid
"
"set background=dark
"set background=light
"colorscheme solarized
"
"set background=dark
"syntax on
"color mango

" Syntastic
set statusline+=%#warningmsg#
set statusline+=%{SyntasticStatuslineFlag()}
set statusline+=%*

let g:syntastic_always_populate_loc_list = 1
let g:syntastic_auto_loc_list = 1
let g:syntastic_check_on_open = 1
let g:syntastic_check_on_wq = 0
let g:syntastic_javascript_checkers = ['jshint']

" Prevent loading YCompleteme
"let g:loaded_youcompleteme = 1
"let g:ycm_auto_trigger = 0

" git clone https://github.com/pangloss/vim-javascript.git
" set regexpengine=1
" syntax enable
execute pathogen#infect()

```

- 3. Install plugins

```
cd ~/.vim/bundle
git clone git://github.com/tpope/vim-abolish.git
git clone https://github.com/scrooloose/nerdtree.git
git clone git://github.com/airblade/vim-gitgutter.git
git clone git://github.com/altercation/vim-colors-solarized.git
git clone https://github.com/pangloss/vim-javascript.git
git clone https://github.com/scrooloose/syntastic.git
git clone git@github.com:tpope/vim-surround.git
git clone https://github.com/maksimr/vim-jsbeautify.git
cd vim-jsbeautify && git submodule update --init --recursive
cd ..
```

- 4. Plugins. Just some:

```
  crisboot@crisboot-Aspire-S3-391 ~/.vim/bundle$ ls
fonts                               nerdtree   tern_for_vim          vim-fugitive   vim-jade        vim-surround
jshint.vim                          node       vdebug                vim-gitgutter  vim-javascript  YouCompleteMe
nerdcommenter                       syntastic  vim-abolish           vim-html2jade  vim-jsbeautify
nerd-filetype-glyphs-fonts-patcher  tabular    vim-colors-solarized  vim-hybrid     vim-stylus
```

- 5. Shortcuts
```
Plugin: https://github.com/tpope/vim-surround
cs'"   : Reemplaza ' por "

Plugin: https://github.com/tpope/vim-abolish
crs    :    coerce to snake_case
crm    :    coerce to MixedCase
crc    :    coerce to camelCase
cru    :    coerce to UPPER_CASE

Plugin: https://github.com/godlygeek/tabular
:'<,'>Tabularize /:    -> tabularize for the specific character ":"

Extra Magic
J      :    move next line into current
D      :    deletes until eol
d0     :    deletes to beggining of line
d3w    :    deletes 3 words
~      :    change lowercase to uppercase
di     :    show clipboard
ctrl+R :    paste last from clipboard (also into command line)

Magic with Regex
:g!/random/d     : deletes all lines not containing "random"
```

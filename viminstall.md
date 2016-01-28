## Everything

- 1. Pathogen

```
mkdir -p ~/.vim/autoload ~/.vim/bundlep && \
curl -LSso ~/.vim/autoload/pathogen.vim https://tpo.pe/pathogen.vim
```

- 2. Add to ~/.vimrc
```
mkdir ~/.vimbackuptem
touch ~/.vimrc
```

- 2.1 New clean version
```
" Globals
" ------------------
set smartindent
set tabstop=4
set shiftwidth=2
set expandtab
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

```

- 4. Plugins. Just some:

```
  crisboot@crisboot-Aspire-S3-391 ~/.vim/bundle$ ls
fonts                               nerdtree   tern_for_vim          vim-fugitive   vim-jade        vim-surround
jshint.vim                          node       vdebug                vim-gitgutter  vim-javascript  YouCompleteMe
nerdcommenter                       syntastic  vim-abolish           vim-html2jade  vim-jsbeautify
nerd-filetype-glyphs-fonts-patcher  tabular    vim-colors-solarized  vim-hybrid     vim-stylus
```

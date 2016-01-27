## Everything

1. Pathogen
```
mkdir -p ~/.vim/autoload ~/.vim/bundle && \
curl -LSso ~/.vim/autoload/pathogen.vim https://tpo.pe/pathogen.vim
```

2. Add to ~/.vimrc

```
execute pathogen#infect()
set number
set shiftwidth=2
set background=dark
colorscheme solarized
```

3. Install plugins

```
cd ~/.vim/bundle
git clone git://github.com/tpope/vim-abolish.git
git clone https://github.com/scrooloose/nerdtree.git
git clone git://github.com/airblade/vim-gitgutter.git
git clone git://github.com/altercation/vim-colors-solarized.git

```

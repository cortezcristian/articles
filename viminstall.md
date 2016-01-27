## Everything

1. Pathogen
```
mkdir -p ~/.vim/autoload ~/.vim/bundle && \
curl -LSso ~/.vim/autoload/pathogen.vim https://tpo.pe/pathogen.vim
```

2. Add to ~/.vimrc

```
execute pathogen#infect()
```

3. Install plugins

```
cd ~/.vim/bundle
git clone git://github.com/tpope/vim-abolish.git
```

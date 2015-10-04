Search Freq
```bash
$ find ./ -name freq* | xargs grep weeks
```

Replace

```bash
find ./ -type f -exec sed -i 's/5% off/10% off/g' "{}" +;
```


```bash
find ./ -type f -exec sed -i 's#Test Game#Unit Tests#g' "{}" +;
```

Global find and rename folders
```bash
find ./root-backup/ -name .git -execdir mv {} backup-git \;
```

PHP




https://www.box.com/blog/how-to-debug-php-with-vim-and-xdebug-on-linux/

https://mutelight.org/minimal-guide-to-debugging-php-with-xdebug-and-vim



http://www.vim.org/scripts/script.php?script_id=2508


https://chrome.google.com/webstore/detail/xdebug-helper/eadndfjplgieldjbigjakmdgkmoaaaoc


http://localhost/mario/alamo/autos.php?XDEBUG_SESSION_START=1

https://blogs.oracle.com/netbeansphp/entry/howto_check_xdebug_installation



ahora se usa Vdebug
http://www.vim.org/scripts/script.php?script_id=4170

http://stackoverflow.com/questions/20706559/php-debugging-how-to-configure-xdebug-for-example-to-use-it-for-vdebug-vim-p

Hay que darle F5 al vim y dsp ir a la pagina y darle F5 de vuelta

http://localhost/phpinfos.php

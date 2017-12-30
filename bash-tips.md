Copy Recursively including hidden files
```bash
$ cp -rT /etc/skel /home/user
```


Search Freq
```bash
$ find ./ -name freq* | xargs grep weeks
```

Replace

```bash
find ./ -type f -exec sed -i 's/5% off/10% off/g' "{}" +;
```

OSX
```bash
find . -type f|xargs perl -pi -e 's/\t/    /g';
```


```bash
find ./ -type f -exec sed -i 's#Test Game#Unit Tests#g' "{}" +;
```

Global find and rename folders
```bash
find ./root-back/ -name .git -execdir mv {} backup-git \;
```

Split big files
```bash
split -a 4 -d -l 5000 bigfile.json
```

Avoid using -o PubkeyAuthentication=no

```bash
ssh -o PreferredAuthentications=password -o PubkeyAuthentication=no example.com
```

http://unix.stackexchange.com/questions/15138/how-to-force-ssh-client-to-use-only-password-auth


```bash
ssh -o PreferredAuthentications=keyboard-interactive,password -o PubkeyAuthentication=no root@cortezcristian.com
```

http://serverfault.com/questions/130346/ssh-use-only-my-password-ignore-my-ssh-key-dont-prompt-me-for-a-passphrase


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


# SSH

```
ssh user@cccc -R 10003:localhost:22
```

# grep

Global Regular Expression Prompt
Matches repetition `a{3}|b`, then concatenation `aaa|b` and then alternation
`aaa` or `b`. The rules can be override with parentesis. What do i use often (that's why i install gnu grep on mac cause i'm use to)

Search recursiveley
```
$ grep -nir "sample" ./folder
```

Got file names only (this is faster)
```
$ grep -lir "sample" ./folder
```

To demostrate you can run the counts `-c`
```
$ grep -nirc "sample" ./folder
$ grep -lirc "sample" ./folder
```

The `-L` option does the opposite of `-l`, shows files not matching.

Put a stop to the matchings
grep -m 4 "input" templates/*

Using grep to count files

``` 
$ ls templates |grep html | grep -v event | wc -l
```

Match exact word

```
grep -nir "\bicon\b" templates
grep -wir icon templates
```

Match exact line `-X`

In example utitlity i crafted
```
cat detect-bad-merge.sh 
#!/bin/bash
errors=$( grep -r ">>>>>>" frontend/src app |wc -l |tr -d ' ' )
if [ "$errors" -gt "0" ]; then
  echo "${RED}[FAIL] Bad merge found ($errors)"
else
  echo "${GREEN}[ OK ] No bad merges, check passed ($errors)"
fi
```


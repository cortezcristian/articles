
Recipe to avoid hosting

```
$ # Download the site
$ httrack http://anyandgo.io/
$ cd anyandgo.io
$ # Check it
$ http-server
$ cd ~/repo
$ git checkout -b gh-pages
$ cp anyandgo.io/* .
$ git add *
$ echo "anyandgo.io" > CNAME
$ git add CNAME && git commit -am "Adding site" && git push -u origin gh-pages
$ google-chrome http://cortezcristian.github.io/anyandgo/ & ## check the site
```


- [GitHub Pages + GoDaddy](https://medium.com/@LovettLovett/github-pages-godaddy-f0318c2f25a#.17elmtj0i)
- [Tips for configuring an A record with your DNS provider](https://help.github.com/articles/tips-for-configuring-an-a-record-with-your-dns-provider/)

```
- Add A record -> 192.30.252.153
- Modify CNAME alias www ->	cortezcristian.github.io
```

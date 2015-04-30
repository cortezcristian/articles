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

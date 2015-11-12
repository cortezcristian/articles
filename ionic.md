# Ionic

## Articles

- [Unit Testing Your Ionic Framework App](http://mcgivery.com/unit-testing-ionic-app/)
- [Using Admob With IonicFramework](https://blog.nraboy.com/2014/06/using-admob-ionicframework/)
- [Update Cordova: cordova platform update android](http://stackoverflow.com/questions/30393324/i-cant-install-cordova-plugins)
- [AdMob Libraries](https://github.com/floatinghotpot/cordova-admob-pro/wiki/Difference-of-Plugin-IDs)

## Starting ionic

```
$ ionic start mynewapp blank
$ ionic serve
```

### Splash & Icons

http://blog.ionic.io/automating-icons-and-splash-screens/

## Build Android

To test
```
$ ionic platform add android
$ ionic build android
...
BUILD SUCCESSFUL
Total time: 17 seconds
Built the following apk(s):
    /var/www/mynewapp/platforms/android/ant-build/MainActivity-debug.apk
```

To publish

```
$ ionic build --release android
...
BUILD SUCCESSFUL
Total time: 30 seconds
Built the following apk(s):
    /var/www/mynewapp/platforms/android/ant-build/MainActivity-release-unsigned.apk
$ keytool -genkey -v -keystore my-release-key.keystore -alias alias_name -keyalg RSA -keysize 2048 -validity 10000
$ which jarsigner
/usr/bin/jarsigner
$ jarsigner -verbose -sigalg SH
A1withRSA -digestalg SHA1 -keystore my-release-key.keystore /var/www/mynewapp/platforms/android/ant-build/MainActivity-release-unsigned.apk alias_name
$ which android
/home/crisboot/adt-bundle-linux/sdk/tools//android
$ /home/crisboot/adt-bundle-l
inux/sdk/build-tools/21.1.2/zipalign -v 4 /var/www/mynewappt/platforms/android/ant-build/MainActivity-release-unsigned.apk AppFinal.apk
Verifying alignment of AppFinal.apk (4)...
      50 META-INF/MANIFEST.MF (OK - compressed)
...
12974469 classes.dex (OK - compressed)
Verification succesful
$ ls
AppFinal.apk
```

# Ionic

### OSX
-[How to submit iOS app to app store using Xcode](https://forum.ionicframework.com/t/how-to-submit-ios-app-to-app-store-using-xcode/1795/5)
- [Submitting an App to the iOS App Store (Xcode)](https://www.youtube.com/watch?v=6uX7B8ZfMiw)
- [How To Submit An App To Apple's App Store](https://www.youtube.com/watch?v=rRlOdp4uZoo)
- [Get Published on Apple - Create and Upload a Distribution Certificate](https://www.youtube.com/watch?v=gRJA9qkMNhw)
- [ERROR ITMS-90032:“Invalid Image Path - No image found at the path referenced under key 'CFBundleIcons':AppIcon40x40”](http://stackoverflow.com/a/35283545/467034)

## Services

- http://a5hik.github.io/ng-sortable/#/
- playground http://play.ionic.io/app/e3547f0f6b05
- Ionic view 

## Articles

- [Unit Testing Your Ionic Framework App](http://mcgivery.com/unit-testing-ionic-app/)
- [Using Admob With IonicFramework](https://blog.nraboy.com/2014/06/using-admob-ionicframework/)
- [Update Cordova: cordova platform update android](http://stackoverflow.com/questions/30393324/i-cant-install-cordova-plugins)
- [AdMob Libraries](https://github.com/floatinghotpot/cordova-admob-pro/wiki/Difference-of-Plugin-IDs)
- [Angular.js, Ionic apps](https://github.com/appfeel/admob-google-cordova/wiki/Angular.js,-Ionic-apps)

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

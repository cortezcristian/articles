# Ionic

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
$ /home/crisboot/adt-bundle-linux/sdk/build-tools/21.1.2/zipalign HelloWorld-release-unsigned.apk HelloWorld.apk
```


# Solar2D AdMob plugin fork

This is a fork of Solar2D (formerly know as CoronaSDK) AdMob plugin. This has been forked for the following reasons:

* document the versions of the used libraries
* document some info how to make compatible with Firebase Analytics plugin
* document some of the steps used to build an app that uses firebaseAnalytics plugin, adMob plugin and notifications plugin (all of these plugins use Firebase frameworks and may have conflicting versions of those frameworks)
* trying to fix ["missing close"] (https://forums.solar2d.com/t/admob-rewarded-video-fixed/351876/8) button on Android video reward ads.
* store these notes

The development computer used is Mac OS X. I guess all of these steps can be done also in Windows computers but I have not tried out that.

[A blog article] (https://cleanseagame.docommit.com/blog/blog_solar2d_admob_notifications_firebase_plugins_on_ios.html) that explains how to get plugin.notifications, plugin.firebaseAnalytics and plugin.admob work together.

# Used AdMob version from Google:

* Version that is part of firebase-ios-sdk 6.32.0, downloaded from https://github.com/firebase/firebase-ios-sdk/releases/tag/CocoaPods-6.32.0
* Based on Readme.md on that file we have to use only these two libraries:

- GoogleMobileAds.framework
- UserMessagingPlatform.framework

# Used Solar2D version

* 2020.3620

# To compile this ios plugin on Mac OS X

* include AdMob plugin normally and build for the device so that Solar2D can fetch the original version.
* Then cd to the toor of this repository and 

```
cd src/ios
./build.sh
cd BuiltPlugin/iphone/
tar -czf ~/Solar2DPlugins/Caches/Solar2Directory/coronalabs/com.coronalabs/plugin.admob/iphone/data.tgz .
```

* sources of coronalabs admob plugin: https://github.com/coronalabs/com.coronalabs-plugin.admob
* these are clearly maintained
* In ios the log says: options.appId is not supported anymore. Move it to plist
* The documentation says: Make sure to use same AdMob app ID as in the build.settings section of the [plugin][plugin.admob].
* It seems that plist section is a good place: GADApplicationIdentifier = "ca-app-pub-?????????????~????????",

# To compile this Android plugin on Mac OS X

* set ANDOIRD_SDK_ROOT (and Android Studio) if you have not it setup already. For more info see: https://developer.android.com/studio/command-line/variables

```
cd src/android
./gradlew build
```

If that is not successful comment out exportAARToThePluginBinary on the first build. After the first successful build it can be put back.

```
cd plugins/2020.3607/android
tar -czf ~/Solar2DPlugins/Caches/Solar2Directory/coronalabs/com.coronalabs/plugin.admob/android/data.tgz .
```

# firebaseAnalytics plugin:

Note - these are here just fot future usage.

```
cd src/ios
./build.sh
cd BuiltPlugin/iphone/
tar -czf ~/Solar2DPlugins/Caches/Solar2Directory/solar2d/tech.scotth/plugin.firebaseAnalytics/iphone/data.tgz .
```

* sources of an early version of firebaseAnalytics plugin: https://github.com/scottrules44/firebaseAnalytics-source
* seems not to be up-to-date with the current plugin version


# plugin.notifications

Another plugin that uses firebase. It would be great to separate local notifications that probably do not need
Firebase :)

* sources of the notifications plugin: https://github.com/scottrules44/firebaseAnalytics-source

# multiple xcode versions

https://medium.com/@hacknicity/working-with-multiple-versions-of-xcode-e331c01aa6bc

sudo xcode-select -s /Applications/Xcode10.app

# Useful links

* https://firebase.google.com/docs/admob/ios/quick-start
* https://github.com/firebase/quickstart-ios
* https://github.com/firebase/firebase-ios-sdk




# Original text in Coronalabs github

Sources for the plugin `plugin.admob`.

Add following to your `build.settings` to use:
```lua
{
    plugins = {
        "plugin.admob" = {
            publisherId = "com.coronalabs",
        },
    },
}
```



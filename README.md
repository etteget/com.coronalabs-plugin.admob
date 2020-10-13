
# Solar2D AdMob plugin fork

This is a fork of Solar2D (formerly know as CoronaSDK) AdMob plugin. This has been forked for the following reasons:

* document the versions of the used libraries
* ensure compatibility with Firebase Analytics
* document some of the steps used to build an app that uses firebaseAnalytics plugin, adMob plugin and notifications plugin (all of these plugins use Firebase frameworks and may have conflicting versions of those frameworks)

All of this has been done only to get the plugins to run and work together on iOS side. The development computer used is Mac OS X.
On Android side no changes to the existing plugins was needed in order to get everything to work.

# Used AdMob version:

* Version that is part of firebase-ios-sdk 6.32.0, downloaded from https://github.com/firebase/firebase-ios-sdk/releases/tag/CocoaPods-6.32.0
* Based on Readme.md on that file we have to use only these two libraries:

- GoogleMobileAds.framework
- UserMessagingPlatform.framework

# Used Solar2D version

* 2020.3620

# To use the plugin 

* include AdMob plugin normally and build for the device so that Solar2D can fetch the original version.
* Then cd to the toor of this repository and 

* cd src/ios
* ./build.sh
* cd BuiltPlugin/iphone/
* tar -czf ~/Solar2DPlugins/Caches/Solar2Directory/coronalabs/com.coronalabs/plugin.admob/iphone/data.tgz .

* sources of coronalabs admob plugin: https://github.com/coronalabs/com.coronalabs-plugin.admob
* these are clearly maintained
* In ios the log says: options.appId is not supported anymore. Move it to plist
* The documentation says: Make sure to use same AdMob app ID as in the build.settings section of the [plugin][plugin.admob].
* It seems that plist section is a good place: GADApplicationIdentifier = "ca-app-pub-?????????????~????????",

# firebaseAnalytics plugin:

* cd src/ios
* ./build.sh
* cd BuiltPlugin/iphone/
* tar -czf ~/Solar2DPlugins/Caches/Solar2Directory/solar2d/tech.scotth/plugin.firebaseAnalytics/iphone/data.tgz .

* sources of an early version of firebaseAnalytics plugin: https://github.com/scottrules44/firebaseAnalytics-source
* seems not to be up-to-date with the current plugin version


# plugin.notifications

Another plugin that uses firebase. It would be great to separate local notifications that probably do not need
Firebase :)

* At the moment we have to strip old files a way
* cd ~/Solar2DPlugins/Caches/Solar2Directory/coronalabs/com.coronalabs/plugin.notifications.v2/iphone
* open data.tgz

* sources of the notifications plugin: https://github.com/scottrules44/firebaseAnalytics-source
* very old but might be up-to-date with the current plugin version?


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



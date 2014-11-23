---
layout: post
title: "How to create the cordova app release version"
date: 2014-11-23 02:02:42 -0200
comments: true
categories: [all, cordova, mobile]
author: 'Diogo Menezes'
---

If you want to put your app at google play store, you will need a signed release version of the app.


To do this, the first step is to generate the release key running the following command:

```
keytool -genkey -v -keystore ~/.certs/your_app_release.keystore -alias your_app_release -keyalg RSA -keysize 2048 -validity 100000
```

After that you will need to set this key in the **_ant.properties_** file. This file  is normally
located at **_cordova_app_dir/platforms/android/_**, but if you dont find it, you can create this file.

In my case I needed to create the file and put this content:

```
key.store=~/.certs/your_app_release.keystore
key.alias=your_app_release
```

Finaly you will need to compile the release version. In **_platform/android_** directory run the command:

```
ant release
```

Now, you can send the signed APK located at **_platform/android/bin_** to the [Google Play Store](https://play.google.com/apps/publish).

If you still have doubts [read this](http://himanen.info/publishing-android-app-to-google-play-store-with-cordova-cli/).

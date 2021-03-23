# React Native Background Geolocation Example

![Screenshot](/screenshot.png)

# Intro

# How to build

In cloned directory:

`yarn install`

## Android

Check android lib versions:

| Name                       | Version |
|----------------------------|---------|
| Google Play Services       | >=30    |
| Google Repository          | >=28    |

Go to [Google API Console](https://console.developers.google.com) and select your project, or create new one:

In `Overview` -> `Google Maps API` -> `Google Maps Android API` -> Check if it's enabled. If not, click button **Enable**!
Create a new key by clicking on `Create credentials` -> `API Key` -> `Android Key`, enter the name of the API key and your SHA1 key, generated before, and create it.

Add Google Maps Android API Key in `android/app/src/main/res/values/strings.xml`:

```xml
<resources>
    ...
    <string name="google_api_key">{{Your Google maps API Key Here}}</string>
</resources>
```

### Run on device (or simulator)

`react-native run-android`

## iOS

### Run on device (or simulator)

`react-native run-ios`

Enable **Freeway Drive** in `Debug` ➜ `Location` menu in iOS Simulator.

# Quirks

## Android

For compatibility with react-native-maps v0.20.1 library versions were locked in root `build.gradle` file:

```
ext {
    compileSdkVersion   = 23
    targetSdkVersion    = 23
    buildToolsVersion   = "23.0.3"
    supportLibVersion   = "23+"
    googlePlayServicesVersion = "11+"
    androidMapsUtilsVersion = "0.5"
}
```

```
compile(project(':react-native-maps')) {
    exclude group: 'com.google.android.gms', module: 'play-services-base'
    exclude group: 'com.google.android.gms', module: 'play-services-maps'
}
compile "com.google.android.gms:play-services-base:11+"
compile 'com.google.android.gms:play-services-location:11+'
compile 'com.google.android.gms:play-services-maps:11+'
```

# Troubleshoot

## Android

Check `adb logcat` for errors. For example wrong API key:

```
E/Google Maps Android API(31792): Authorization failure.  Please see https://developers.google.com/maps/documentation/android-api/start for how to correctly set up the map.
E/Google Maps Android API(31792): In the Google Developer Console (https://console.developers.google.com)
E/Google Maps Android API(31792): Ensure that the "Google Maps Android API v2" is enabled.
E/Google Maps Android API(31792): Ensure that the following Android Key exists:
E/Google Maps Android API(31792): 	API Key: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA                                             
E/Google Maps Android API(31792): 	Android Application (<cert_fingerprint>;<package_name>): 00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00;com.rnbgexample
```

# Mocking Locations & Test Server

# Integrate SDK

# Getting Library

We provide SDK via Pubspec and Github token. When we will be ready to work with you we provide that token.

# Import

Add our dependency to Pubspec of your application's project:

```yaml
dependencies:
  inappsdk:
    git:
      url: https://oauth2:*GITHUB_TOKEN*@github.com/nextmillenniummedia/SDKFlutter.git
      ref: publish
```
Where **GITHUB_TOKEN** is our token with rights to copy repo with SDK sources.
Use **publish** branch to get newest version.

Also you can set specific version by git tag as an example below:

```yaml
dependencies:
  inappsdk:
    git:
      url: https://oauth2:*GITHUB_TOKEN*@github.com/nextmillenniummedia/SDKFlutter.git
      ref: v.0.1.0
```
In that case you always get InApp SDK v.0.1.0

Main class of InApp SDK is `InAppSdk`. To use it and others classes of SDK in **.dart** file you need to import header file of library as at example below:

```dart
import 'package:inappsdk/in_app_sdk.dart';
```

# Setup

Very important to do next steps to start using InApp SDK:

## 1. Add InApp API key

We will give InApp API keys for both platforms. You need to set them in main.dart at initializing stage.

```dart
InAppSdk().androidApiKey = "ef0bc3f8-0f12-45e3-8761-f65c88f1f96e";
InAppSdk().iOSApiKey = "ef0bc3f8-0f12-45e3-8761-f65c88f1f96e";
```

## 2. Add provided AdMob keys to iOS and Android subprojects

We will also provide you AdMob keys and application ID for platform subprojects which are required for InApp SDK. Set them as described below.

### Android

Add AdMob key and application ID to the app's **android/app/src/main/AndroidManifest.xml** file by adding a **meta-data** tag with the name **com.google.android.gms.ads.APPLICATION_ID** as at example below:

```xml
<manifest>
    <application>
        <meta-data
            android:name="com.google.android.gms.ads.APPLICATION_ID"
            android:value="ADMOB_KEY"/>
    <application>
<manifest>
```
Where **ADMOB_KEY** are identifier that we will provide you.
**APPLICATION_ID** is your PlayStore ID.

### iOS

Add AdMob key to the **ios/Runner/info.plist** file. You need to set a new key with AdMob key as a value as at example below:

```xml
<key>GADApplicationIdentifier</key>
<string>ADMOB_KEY</string>
```
Where **ADMOB_KEY** is identifier that we will provide you.

## 3. Initialize SDK

Before loading ads, have your app initialize InApp SDK by calling **await InAppSdk().initialize();**.

Note, that you need to make your **main()** func async because initialize of SDK take a time.

Full example of **main()** func with initializing **InApp SDK**:

```dart
import 'package:inappsdk/in_app_sdk.dart';

...

void main() async {
  WidgetsFlutterBinding.ensureInitialized();

  // set InApp API keys for both platforms
  InAppSdk().androidApiKey = "INAPP_API_KEY";
  InAppSdk().iOSApiKey = "IN_APP_KEY";

  // initialize SDK
  await InAppSdk().initialize();

  runApp(const MyApp());
}
```

That’s all you need and now SDK is ready to go. Check other docs to learn how to implement ads showing.

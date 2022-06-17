# Integrate SDK

Your Flutter project must be updated to integrate the Next SDK.

Follow the steps below to update your existing Flutter project:

# Import

1. Open your Flutter project in Android Studio.
2. Open your project's `pubspec.yaml` file and append the following `next_sdk` block to the dependencies section:

```yaml
dependencies:
  next_sdk:
    git:
      url: https://oauth2:*GITHUB_TOKEN*@github.com/nextmillenniummedia/next-sdk-flutter.git
      ref: publish
```

**Note**: Replace GITHUB_TOKEN with the token we provided.

3. Run `pub get` to install the SDK.

Use **publish** branch to get newest version.

Also you can set specific version by git tag as an example below:

```yaml
dependencies:
  next_sdk:
    git:
      url: https://oauth2:*GITHUB_TOKEN*@github.com/nextmillenniummedia/next-sdk-flutter.git
      ref: v.0.2.0
```
In that case you always get Next SDK v.0.2.0

**Note:** If you are using an older version and want to upgrade, use `pub upgrade` in your project.

Main class of Next SDK is `NextSdk`. To use it and others classes of SDK in **.dart** file you need to import header file of library as at example below:

```dart
import 'package:next_sdk/next_sdk.dart';
```

### Modify Your Android Flutter Project

Follow the steps below to prepare your Android-based Flutter project:

1. Open Android Studio's **Project** window and navigate to `/app/src/main/`.
2. Open `/app/src/main/AndroidManifest.xml` and add the following lines inside the `application` block:

```xml
<manifest>
    <application>
        <meta-data
            android:name="com.google.android.gms.ads.APPLICATION_ID"
            android:value="GOOGLE_APP_ID"/>
    <application>
<manifest>
```
**Note:** Replace `GOOGLE_APP_ID` with the Google Application ID provided by us.

3. Ensure the following permission exists in the manifest block in `AndroidManifest.xml`:

```xml
<uses-permission android:name="android.permission.INTERNET" />
```

4. Navigate to **Build** > **Flutter** and select **Build APK** to ensure the project builds. If you receive a error about the minimum SDK version, navigate to `/flutter/packages/flutter_tools/gradle/flutter.gradle` and change the `minSdkVersion` to 21 or higher:

```
static int minSdkVersion = 21 // Set to 21 or higher
```

`minSdkVersion` is used by build.gradle:

```
defaultConfig {
     ...
     minSdkVersion flutter.minSdkVersion
     ...
}
```

5. Navigate to the **Run** menu and select **Run** to verify that the app successfully builds and executes on your Android device.


## Modify Your iOS Flutter Project

This section describes how to modify your iOS Flutter project.

**Note:** The Flutter project auto-generates projects for both Android and iOS. The iOS workspace and project are both named `Runner` and their files (`Runner.xcodeproj` and `Runner.xcworkspace`) are located in the `ios` sub-directory of your project.

Follow the steps below to prepare your iOS-based Flutter project:

1. Open your project's `ios/Runner/Info.plist` file in Android Studio.

2. Add a provided `GADApplicationIdentifier` key with the (string) value of your AdMob app ID to `Info.plist`:

```xml
<key>GADApplicationIdentifier</key>
<string>PUT_GOOGLE_APPLICATION_ID_HERE</string>
<!-- Replace PUT_GOOGLE_APPLICATION_ID_HERE with the live key provided to you by the Next Millennium Media -->
```

3. Open `Runner.xcworkspace` in Xcode.

4. Navigate to **Product** > **Destination** and select a target device.

5. Select **Product** > **Build** to ensure the app builds and signs.

**Tip:** Codesign will display a dialog box asking for keychain password to access the signing certificate key. Choose Always allow or this dialog will appear numerous times.

6. Return to Android Studio and select to **Build** > **Flutter** > **Build iOS** to ensure the project builds.

7. Select **Run main.dart** to verify that the app successfully builds and executes. Android Studio will launch the app on the iOS device you selected in Step 3.

**Notes: **

- When running the app for the first time, you may need to run it in Xcode first by selecting **Product** > **Run**.

- You may need to configure the iOS device to trust the developer via the on-device **Settings** app:

  1. Navigate to **General** > **Device Management**.

  2. Tap on your provisioning profile in the **Developer app** list.

  3. Allow the iOS device to *trust* the developer. 

- You may also need to configure your developer machine to *trust* apps from your developer profile:

  1. Navigate to the **Apple** menu on MacOS.

  2. Select **System Preferences** > **Security and Privacy** > **General** tab.

  3. Click the lock icon at the bottom and enter your password to allow changes.

  4. Navigate to **Allow apps downloaded from** and select** App Store and identified developers**.

  5. Click **Allow** to allow your app to run. 

## Setup SDK

### 1. Add Next API key

We will give Next API keys for both platforms. You need to set them in main.dart at initializing stage.

```dart
NextSdk().androidApiKey = "ef0bc3f8-0f12-45e3-8761-f65c88f1f96e";
NextSdk().iOSApiKey = "ef0bc3f8-0f12-45e3-8761-f65c88f1f96e";
```

**Note:** If you're only building for one of the target OS's, then you only need to set the corresponding property.

### 2. Initialize SDK

Before loading ads, have your app initialize Next SDK by calling `await NextSdk().initialize();`.

Note, that you need to make your `main()` func async because initialize of SDK take a time.

Full example of `main()` func with initializing **Next SDK**:

```dart
import 'package:next_sdk/next_sdk.dart';

...

void main() async {
  WidgetsFlutterBinding.ensureInitialized();

  // set Next API keys for both platforms
  NextSdk().androidApiKey = "NEXT_API_KEY";
  NextSdk().iOSApiKey = "NEXT_APP_KEY";

  // initialize SDK
  await NextSdk().initialize();

  runApp(const MyApp());
}
```

The Flutter project builds apps for both Android and iOS platforms. Once you've configured your project as described in the previous sections, you can use Next SDK methods which will run on both platforms to display ads.

# Prerequisites

Before continuing, ensure you have the following:

## General

This section lists the general requirements to build an application using the Next SDK.

**Note:** Android Studio is used for building both Android and iOS apps (for the latter, Android Studio is used in conjunction with Xcode).

- Full installation of Flutter.

- Contact us to obtain the following:

    - GitHub Token

    - Google Application ID

    - Next Millennium Media API Key

    [Contact us](https://nextmillennium.io/) for more information.

- Android Studio with the following installed:

    - Flutter Plugin (install from the **Welcome Screen** > **Plugins** tab). 
    
        **Note:** The installation may ask to install relevant Flutter dependencies.

    - Google Play Licensing Library (required for Flutter installation)

    - Android SDK Tools

    - Android SDK Command-line Tools

    - Android SDK Platform-Tools 

- An existing Flutter project. 

For additional information see the [Flutter install guide](https://docs.flutter.dev/get-started/install).

## Android

This section lists Android-specific requirements:

- Ensure your project's /app/build.gradle file contains the following dependency:

```xml
dependencies
{
    implementation "androidx.work:work-runtime:2.7.0"
}
```

**Notes:**

- You may need to first add the dependencies block.
- The Android project directory name can't contain dashes (-) due to Dart requirements. 
- The project name must be lowercase with optional underscores due to Dart.

## iOS

This section lists iOS-specific requirements:

- Xcode 12.3.
- Xcode Command-line Tools.
- Valid provisioning profile to assign a bundle ID and sign apps in Xcode. 

    **Note:** This may require a physical iOS device in order to set up the provisioning profile. Ensure that your Bundle Identifier is valid for your account (i.e. Replace `com.example` with `com.yoururl`).

- CocoaPods (for Flutter installation). 

    **Note:** If you get a CocoaPods output error when building on M1 Macs, run the following command: `sudo arch -x86_64 gem install ffi`

- Ruby (for CocoaPods installation).
# Integrate Ad Formats Dynamically

Dynamic mode allows publishers to display ads directly into the content of their App’s screens using pre-defined ad units at the inApp dashboard UI. This method saves publishers time setting up and lowers maintenance to the minimum, since you there’s no need to update code in case of ad format switch while serving ads dynamically.

# Add Screens

First, you need provide us a list of unique screens in your apps. In InApp SDK for Flutter you can do it calling function `InAppSdk.sendScreens()` at `main()` of your app:

```dart
import 'package:flutter/foundation.dart';
import 'package:inappsdk/in_app_sdk.dart';

...

void main() async {
  WidgetsFlutterBinding.ensureInitialized();

  // set InApp API keys for both platforms
  InAppSdk().androidApiKey = "INAPP_API_KEY";
  InAppSdk().iOSApiKey = "IN_APP_KEY";

  // initialize SDK
  await InAppSdk().initialize();

  // Call screens uploading only on debug mode.
  if (kDebugMode) {
    // Add to list all screen that will be used to show InApp ads.
    // We recommend to use class name of your widget as key so they'll be unique.
    List<String> screenNames = [
    "ExampleWidget",
    "ExampleWidget1",
    ];

    // Upload info about screens to InApp.
    await InAppSdk().sendScreens(screenNames);
  }

  runApp(const MyApp());
}
```

After you registered screens all this code won’t be needed. Make sure that you don’t have it in production build.

# Showing Ad

With registered screens your app is ready for Dynamic mode. Note, that main configuration and settings available at InApp dashboard. In your app’s sources you need to implement support of **Dynamic mode** by steps below.

## Banner Ads

Currently there are 3 types of banner ad supported in the **Dynamic mode**: 

- **Sticky Top** (*at top of screen or with offset*)
- **Sticky Bottom** (*at bottom of screen or with inset*)
- **In Content** *(by view container and with any content inside)*

### Sticky Top/Bottom Banner Ads

To use Sticky Top/Bottom ads you need to use our container widget `InAppBannerContainerWidget` with your original widget as child and also provide what registered screen name is will be used to showing ad.

Full example of usage:

```dart
import 'package:inappsdk/in_app_sdk.dart';

...

class ExampleWidget extends StatelessWidget {

  ...

  // example of build() function
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(title),
      ),
      // set our container widget as body of registered screen.
      // provide your own widget as child widget.
      body: InAppBannerContainerWidget(
          screenName: "ExampleScreen",
          child: originalWidget()
        ),
    );
  }

  // your own widget
  Widget originalWidget() {
    ...
  }
}
```

### In Content Banner Ads

We also provide automatic banner ad injection at scrollable lists with any content inside. Use `InAppInContentWidget` class and provided banner ad unit for that.

```dart
import 'package:inappsdk/in_app_sdk.dart';

...

class ExampleWidget extends StatelessWidget {
  
  ...

  // example of build() function
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      // set our container widget as body.
      // provide your own widget as item to itemBuilder.
      // we also give you ad unit that will be used ad identifier to show ad within.
      body: InAppInContentWidget(
        inAppId: "*your ad unit*",
        listener: const InAppBannerAdListener(),
        itemCount: 10,
        itemBuilder: (context, index) {
          return _itemWidget(context, index);
        },
      ),
    );
  }

  // your own widget
  Widget _itemWidget(BuildContext context, int index) {
    ...
  }
}
```
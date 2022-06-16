# Integrate Ad Formats Manually

Manual mode is a way of serving ads in your apps where publisher manually adjusts ad placing and does all of the ad management on his own. This way of integration allows more customization compared to Dynamic method, however Manual mode is recommended for advanced users.

First, you need to get two (for both platforms) configurated InApp ad units from your manager. Implement current platform check and use their IDs to show ads.

For example, you can add ad units to constants storage:
```dart
/// Constants used in the app.
class Constants {
  ...

  // Banner Ads
  static const androidBannerAdUnitId = "*your Android banner ad unit ID*";
  static const iosBannerAdUnitId = "*your iOS banner ad unit ID*";

  // Interstitial Ads
  static const androidInterstitialAdUnitId = "*your Android interstitial ad unit ID*";
  static const iosInterstitialAdUnitId = "*your iOS interstitial ad unit ID*";
}
```

## Banner Ads

Use `InAppBannerFutureWidget` class with your InApp ad unit to showing Banner ad manually. Make sure that your layout provide enough space to show ad with size you need.

Example of usage:

```dart
import 'package:inappsdk/in_app_sdk.dart';

...

class ExampleWidget extends StatelessWidget {

  ...

  // example of build() function.
  // in this case we made list view with some content and want to add banner ad to some place.
  @override
  Widget build(BuildContext context) {
    return ListView(children: [
      // some widgets with your content.
      ...
      InAppBannerFutureWidget(
            inAppId: Platform.isAndroid
                // use Android banner ad unit for Android
                ? Constants.androidBannerAdUnitId
                // use iOS banner ad unit for iOS
                : Constants.iosBannerAdUnitId,
            listener: getListener(context)),
      ...
    ]);
  }
}
```

## Interstitial Ads

Use `InAppInterstitialAd` class with your InApp ad unit to show Interstitial ad manually.
Use it within Widget builder and call `loadAndShow()` func when you want to show ad.

Example of usage:

```dart
import 'package:inappsdk/in_app_sdk.dart';

...

class ExampleWidget extends StatelessWidget {

  ...

  // example of build() function.
  // in this case we made list view with some content and want to show Interstitial ad when this widget is showing on screen.
  @override
  Widget build(BuildContext context) {
    // use loadAndShow() func to immediately show ad. you can also add some condition when ad will be showing.
    InAppInterstitialAd(
            adUnitId: Platform.isAndroid
                // use Android interstitial ad unit for Android
                ? Constants.androidInterstitialAdUnitId
                // use iOS interstitial ad unit for iOS
                : Constants.iosInterstitialAdUnitId,
            listener: getListener(context))
        .loadAndShow();
    return ListView(children: [
      // some widgets with your content.
    ]);
    );
  }
}
```
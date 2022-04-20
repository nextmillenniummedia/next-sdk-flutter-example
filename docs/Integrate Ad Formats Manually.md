# Integrate Ad Formats Manually

Manual mode is a way of serving ads in your apps where publisher manually adjusts ad placing and does all of the ad management on his own. This way of integration allows more customization compared to Dynamic method, however Manual mode is recommended for advanced users.

First, you need to get configurated InApp ad unit from your manager. Use it’s ID to next ads.

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
      InAppBannerFutureWidget(inAppId: "*your InApp ad unit ID*", listener: getListener(context)),
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
    InAppInterstitialAd(adUnitId: "*your InApp ad unit ID*", listener: getListener(context))
        .loadAndShow();
    return ListView(children: [
      // some widgets with your content.
    ]);
    );
  }
}
```
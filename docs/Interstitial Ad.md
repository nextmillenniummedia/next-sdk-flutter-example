# Interstitial Ads

Use `NextInterstitialAd` class with your Next ad unit to show Interstitial ad manually.
Use `load()` function to load ad. You will get ready ad from `onAdLoaded()` callback which you can show when you want.

Example of usage:

```dart
import 'package:next_sdk/next_sdk.dart';

...

class ExampleWidget extends StatelessWidget {

  ...

  // use load() func to load ad. you will get ready ad from onAdLoaded() which you can show by calling show().
  NextInterstitialAd(
          adUnitId: Platform.isAndroid
              // use Android interstitial ad unit for Android
              ? Constants.androidInterstitialAdUnitId
              // use iOS interstitial ad unit for iOS
              : Constants.iosInterstitialAdUnitId,
          listener: getListener(context))
           onAdLoaded(NextInterstitialAd ad) {
            // show ad or save it and use later.
            ad.show();
          }
      .load();
}
```
# Rewarded Interstitial Ads

Use `NextRewardedInterstitialAd` class with your Next ad unit to show Rewarded Interstitial ad manually.
Use `load()` function to load ad. You will get ready ad from `onAdLoaded()` callback which you can show when you want.

Example of usage:

```dart
import 'package:next_sdk/next_sdk.dart';

...

class ExampleWidget extends StatelessWidget {

  ...

  // use load() func to load ad. you will get ready ad from onAdLoaded() which you can show by calling show().
  NextRewardedInterstitialAd(
          adUnitId: Platform.isAndroid
              // use Android rewarded interstitital ad unit for Android
              ? Constants.androidRewardedInterstitialAdUnitId
              // use iOS rewarded interstitial ad unit for iOS
              : Constants.iosRewardedInterstitialAdUnitId,
          listener: getListener(context))
           onAdLoaded(NextRewardedInterstitialAd ad) {
            // show ad or save it and use later.
            ad.show();
          }
      .load();
}
```
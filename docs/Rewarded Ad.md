# Rewarded Ads

Use `NextRewardedAd` class with your Next ad unit to show Rewarded ad manually.
Use `load()` function to load ad. You will get ready ad from `onAdLoaded()` callback which you can show when you want.

Example of usage:

```dart
import 'package:next_sdk/next_sdk.dart';

...

class ExampleWidget extends StatelessWidget {

  ...

  // use load() func to load ad. you will get ready ad from onAdLoaded() which you can show by calling show().
  NextRewardedAd(
          adUnitId: Platform.isAndroid
              // use Android rewarded ad unit for Android
              ? Constants.androidRewardedAdUnitId
              // use iOS rewarded ad unit for iOS
              : Constants.iosRewardedAdUnitId,
          listener: getListener(context))
           onAdLoaded(NextRewardedAd ad) {
            // show ad or save it and use later.
            ad.show();
          }
      .load();
}
```
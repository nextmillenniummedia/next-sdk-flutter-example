# App Open Ads

Use `NextAppOpenAd` class with your Next ad unit to show App Open Ad.
Use `load()` function to load ad and it will be shown on the next opening of your app.

```dart
import 'package:next_sdk/next_sdk.dart';

NextAppOpenAd(
          adUnitId: Platform.isAndroid
              ? Constants.androidAppOpenAdUnitId
              : Constants.iosAppOpenAdUnitId,
          listener: getLogListener(context))
      .load();
```

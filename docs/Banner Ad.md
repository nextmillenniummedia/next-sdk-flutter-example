# Banner Ads

Use `NextBannerWidget` class with your Next ad unit to showing Banner ad manually. Make sure that your layout provide enough space to show ad with size you need.

Example of usage:

```dart
import 'package:next_sdk/next_sdk.dart';

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
      NextBannerWidget(
            adUnitId: Platform.isAndroid
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
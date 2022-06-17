# Integrate Ad Formats

First, you need to get two (for both platforms) configurated Next ad units from your manager. Implement current platform check and use their IDs to show ads.

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

  ...
}
```

Next SDK supports various ad formats. See usage guide for each of it below:

1.  [Banner Ad](https://github.com/nextmillenniummedia/next-sdk-flutter-example/blob/main/docs/Banner%20Ad.md)

2.  [Interstitial Ad](https://github.com/nextmillenniummedia/next-sdk-flutter-example/blob/main/docs/Interstitial%20Ad.md)

3.  [Rewarded Ad](https://github.com/nextmillenniummedia/next-sdk-flutter-example/blob/main/docs/Rewarded%20Ad.md)

4.  [Rewarded Interstitial Ad](https://github.com/nextmillenniummedia/next-sdk-flutter-example/blob/main/docs/Rewarded%20Interstitial%20Ad.md)

5.  [App Open Ad](https://github.com/nextmillenniummedia/next-sdk-flutter-example/blob/main/docs/App%20Open%20Ad.md)
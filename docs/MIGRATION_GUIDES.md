# Migration Guide from InApp SDK

Since v.0.2.0 we renamed our product from `InApp` to `Next`. You can see full list of breaking changes related to this below:

## Change package name

In your `pubspec` file change SDK's name:

From

```yaml
inappsdk
```

to

```yaml
next_sdk
```

## New name of SDK's main class

Call main instance by new `Next` name:

From

```dart
 InAppSdk().
```

to

```dart
 Next.
```

Also we have minor changes in public API. See other docs for more.
# Upgrading

This page will list any changes that you have to make when there is a breaking or major version change.

## From version 3.0.X to version 4.0.0

There is a breaking change on Android. The android image picker was changed from Matisse to FishBun.

The change was because Matisse was not very actively mantained and also requires a lot of effort to be customized via XML styles.

FishBun on other side is very actively mantained and also allows you to pass customization options via Dart code, just like on iOS.

The breaking changes are:

- Removed the `options` parameter from `pickImages` method. There are now two separate parameters that can be passed- `cupertinoOptions` and `materialOptions`. If you previously passed the `options` parameter to customize the iOS look and feel, you have to change that param name to `cupertinoOptions`.
- If you was overriding Mattise styles and localizations via XML, you can safely remove those now. Instead you can pass different customization options directly with `materialOptions` when invoking the image picker.
- Previously on Android when you take iamge with the camera in the gallery, the image picker was immediately closed, which is exactly the opposite on how it worked on iOS. With this new version both flows are consistent, meaning when you take a picture on Android you will go back to gallery and can select more images, including the one you've just taken.

## From version 2.4.11 to version 3.0.X

The project has migrated from using the old Android Support Library to [AndroidX](https://developer.android.com/jetpack/androidx/). If you haven't migrated you project to AndroidX yet, please use version 2.4.11 of the plugin.

If you migrated your project to AddroidX you can use version 3 and above of the plugin.

For more information how to migrate your project see [official migration guide](https://developer.android.com/jetpack/androidx/migrate).

!> Before migrating to AndroidX make sure all plugins you use in your project are supporting AndroidX. Recently the Flutter team started to migrate all of their plugins, but you should check the rest of the third party plugins you are using.

## From version 2.3.* to 2.4.11

If you are using the `Metadata` class you have to rename all priperties that you are checking to lowerCamelCase e.g.

- Previously `metadata.exif.Artist`
- Now `metadata.exif.artist`
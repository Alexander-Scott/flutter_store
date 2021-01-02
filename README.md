# Flutter Store - A guide to creating a generic store using Flutter and Firebase

In this repository you will find an example of a store, created using Flutter and Firebase. Store in this regard refers to a platform which allows users to push content and other users to pull that content. This is a generic solution but could be tailored towards a specific type of content, such as an App Store, Item store, Photo Gallery, Social Network, etc. All of these examples have content that is pushed and pulled by users.

This README contains a moderately detailed guide on how this example was created, broken down into various steps. Each step will correlate to a branch in this repository where you can browse the code if you so wish.

## Flutter Doctor

```
[✓] Flutter (Channel stable, 1.22.4, on Mac OS X 10.15.7 19H15 darwin-x64, locale en-GB)
[✓] Android toolchain - develop for Android devices (Android SDK version 30.0.2)
[✓] Xcode - develop for iOS and macOS (Xcode 11.5)
[✓] VS Code (version 1.52.1)
[✓] Connected device (iOS Simulator iPhone 11)
```

## Other pre-requisites

- Firebase setup complete and emulator installed


# Part 0 - Project Setup

This part involves creating the initial project and getting it running on your simulator/device. You can follow the steps [here](https://flutter.dev/docs/get-started/install) to create the default Flutter project and run it.

Alternatively you can use the source code from the part_0 branch in this repository but you may have to change the bundle identifer to get it to successfully deploy to your device. Search the project for all instances of `com.alexscott.flutter_store` and replace it with an appropriate identifer for your devices.

A basic Github actions workflow has also been created that operates on Pull Requests. It runs build and test commands on all changes to prevent any broken code from being merged. The job is run on a macOS VM and with the same Flutter version that I use locally.


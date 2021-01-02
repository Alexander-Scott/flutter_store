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


# Part 0 - [Project Setup](https://github.com/Alexander-Scott/flutter_store/tree/part_0_project_setup)

### 0.1 - Flutter Create

This part involves creating the initial project and getting it running on your simulator/device. You can follow the steps [here](https://flutter.dev/docs/get-started/install) to create the default Flutter project and run it.

Alternatively you can use the source code from the part_0 branch in this repository but you may have to change the bundle identifer to get it to successfully deploy to your device. Search the project for all instances of `com.alexscott.flutter_store` and replace it with an appropriate identifer for your devices.

### 0.2 - State Management

A constant discussion in the Flutter world is which state management solution to use for a project, and it is very advantageous to settle on a decision early on in a project. For this project we will be using [BLoC](https://bloclibrary.dev/#/). The structure of files in the project will be "component based", which means each component occupies a folder which contains the view and the business logic. Components are isolated from one another.

You can follow the tutorial [here](https://bloclibrary.dev/#/fluttercountertutorial) to amend the counter example to follow the BLoC pattern. With the tutorial followed we have a good basis to begin our development on. It also sets up some integration tests, which can be run with:

```bash
flutter drive \
  --driver=test_driver/main_test.dart \
  --target=test_integration/app_test.dart
```

### 0.3 - CI

A basic Github actions workflow has also been created that operates on Pull Requests. It runs build and test commands on all changes to prevent any broken code from being merged. The job is run on a macOS VM and with the same Flutter version that I use locally.

```yaml
jobs:
  build:
    runs-on: macos-latest # Run on MacOS VM
    steps:
    - uses: actions/checkout@v2 # Checkout the code from this PR
    - uses: actions/setup-java@v1 # Set up Java on the VM
      with:
        java-version: '12.x'
    - uses: subosito/flutter-action@v1 # Set up Flutter on the VM using the specified version
      with:
        flutter-version: '1.22.4'
    - run: flutter pub get # Fetch dependencies
    - run: flutter format --set-exit-if-changed lib test # Lint with flutter format
    - run: flutter analyze lib test # Lint with flutter analyse

    - run: flutter test
    - run: flutter build apk
    - run: flutter build ios --release --no-codesign
```

fastlane documentation
----

# Installation

Make sure you have the latest version of the Xcode command line tools installed:

```sh
xcode-select --install
```

For _fastlane_ installation instructions, see [Installing _fastlane_](https://docs.fastlane.tools/#installing-fastlane)

# Available Actions

## Android

### android deployInternalToFirebase

```sh
[bundle exec] fastlane android deployInternalToFirebase
```

Submit a new Internal Build to Firebase

>Optionally release notes can be added like so:

```sh

[bundle exec] fastlane deployInternalToFirebase release_notes:"testing notes"

```

### android buildReleaseApk

```sh
[bundle exec] fastlane android buildReleaseApk
```

Create new Release APK

Find it under app/build/outputs/apk/release

### android deployProdToPlayStore

```sh
[bundle exec] fastlane android deployProdToPlayStore
```

Submit a new Production Build to Play Store

By Default it sets the version_code to last from PlayStore + 1.

>Optionally version code increase can be skipped via:

```sh

[bundle exec] fastlane deployProdToPlayStore skip_build_number_increase:1

```

----

This README.md is auto-generated and will be re-generated every time [_fastlane_](https://fastlane.tools) is run.

More information about _fastlane_ can be found on [fastlane.tools](https://fastlane.tools).

The documentation of _fastlane_ can be found on [docs.fastlane.tools](https://docs.fastlane.tools).

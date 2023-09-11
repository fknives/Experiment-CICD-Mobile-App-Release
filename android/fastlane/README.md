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

### android deployInternalFirebase

```sh
[bundle exec] fastlane android deployInternalFirebase
```

Submit a new Internal Build to Firebase

>Optionally release notes can be added like so:

```sh

[bundle exec] fastlane deployInternalFirebase release_notes:"testing notes"

```

### android buildReleaseApk

```sh
[bundle exec] fastlane android buildReleaseApk
```

Create new Release APK

Find it under app/build/outputs/apk/release

### android deployProdPlayStore

```sh
[bundle exec] fastlane android deployProdPlayStore
```

Submit a new Production Build to Play Store

By Default it sets the version_code to last from Playstore + 1.

>Optionally version code increase can be skipped via:

```sh

[bundle exec] fastlane deployInternalFirebase skip_build_number_increase:1

```

----

This README.md is auto-generated and will be re-generated every time [_fastlane_](https://fastlane.tools) is run.

More information about _fastlane_ can be found on [fastlane.tools](https://fastlane.tools).

The documentation of _fastlane_ can be found on [docs.fastlane.tools](https://docs.fastlane.tools).

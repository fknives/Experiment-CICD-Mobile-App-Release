fastlane documentation
----

# Installation

Make sure you have the latest version of the Xcode command line tools installed:

```sh
xcode-select --install
```

For _fastlane_ installation instructions, see [Installing _fastlane_](https://docs.fastlane.tools/#installing-fastlane)

# Available Actions

## iOS

### ios deployInternalToFirebase

```sh
[bundle exec] fastlane ios deployInternalToFirebase
```

Creates Release Signed build and publishes it to firebase

>Optionally release notes can be added like so:

```sh

[bundle exec] fastlane deployInternalToFirebase release_notes:"testing notes"

```

### ios deployToTestFlight

```sh
[bundle exec] fastlane ios deployToTestFlight
```

Submit a new Production Build to TestFlight

By Default it sets the version_code to last from TestFlight + 1.

>Optionally version code increase can be skipped via:

```sh

[bundle exec] fastlane deployInternalFirebase skip_build_number_increase:1

```

### ios buildReleaseIPA

```sh
[bundle exec] fastlane ios buildReleaseIPA
```

Create new Release IPA

Find it under ios/builds

### ios setupCodeSigning

```sh
[bundle exec] fastlane ios setupCodeSigning
```

Sets up the and initialises the required authentications and project configurations to sign a build

Creates a temporary keychain which should be deleted at the end, see :cleanupKeyChain

### ios cleanupKeyChain

```sh
[bundle exec] fastlane ios cleanupKeyChain
```

Deletes the temporary keychain if it exists

The keychain is created via :setupCodeSigning

----

This README.md is auto-generated and will be re-generated every time [_fastlane_](https://fastlane.tools) is run.

More information about _fastlane_ can be found on [fastlane.tools](https://fastlane.tools).

The documentation of _fastlane_ can be found on [docs.fastlane.tools](https://docs.fastlane.tools).

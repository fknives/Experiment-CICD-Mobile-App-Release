# CI/CD Documentation 

For Continuous Delivery we are taking using [Fastlane](https://fastlane.tools/) and [GitHub Actions](https://github.com/features/actions).

Internal Builds are delivered to [Firebase](https://console.firebase.google.com/project/app-wl-59d27/overview).

Production Builds are Delivered to PlayStore Internal Test Track and App Store's TestFlight.

All workflows can be found in this [folder](.github/workflows).

## Pull Request Validations

A Workflow is run on every pull request. It's purpose is to verify the Pull Request is correct and it is buildable.

The workflow can be found [here](.github/workflows/validate_pullrequest.yml).

## Deployment To Firebase

This workflow can be triggered manually, on the project's GitHub page, via the following:
- choosing Actions
- selecting "Deploy To Firebase"
- clicking Run Workflow
- selecting branch and clicking Run Workflow

This will start the workflow which will in parallel build an apk and ipa file. These files will be distributed on Firebase.
As release notes they will contain the commit hash and the commit message for identification.

The workflow can be found [here](.github/workflows/deploy_to_firebase.yml).

## Deployment to PlayStore Internal & TestFlight

This workflow can be triggered manually, on the project's GitHub page, via the following:
- choosing Actions
- selecting "Deploy to Play Store Internal & TestFlight"
- clicking Run Workflow
- selecting branch and clicking Run Workflow

This will start the workflow which will in parallel build an aab and ipa file. These Files will be distributed to the respective Stores.

**Android aab** -> Play Store Internal Test track

**iOS ipa** -> App Store's Testflight.

From here the release notes and additional changes for publication should be done in the respective stores.

The workflow can be found [here](.github/workflows/deploy_to_playstore_testflight.yml).

### Versioning

For versioning the iOS `MARKETING_VERSION` and Android `versionName` should be updated.

The buildNumber and versionCode are automatically updated via the pipeline. 

These version name updates should be setup before the Workflow is started.

## Tooling

For the build, signing and distribution steps Fastlane is used.

For signing and other app specific values GitHub Actions Secrets & Environment Variables are used.

### Fastlane

Fastlane is a great tool to ease the building step and integration with the distribution tools.

There are 2 `Fastfile`, one for [Android](android/fastlane/Fastfile) and one for [iOS](ios/fastlane/Fastfile).

The lanes are automatically documented and contain the lane descriptions. Here they are [android](android/fastlane/README.md), [ios](ios/fastlane/README.md).

Fastlane can also be run locally if all the environment variables are setup on the local machine. This is useful if GitHub Actions is disrupted or if we are over the budgeted minutes.

### Secrets and Environment Variables

The signing of these files require a group of secrets. Some are passwords, aliases, some are files.

The secrets and env variables are grouped by where its used (android / ios) and have a name describing what they are.

You can find them by going to the repo's GitHub page then:
- Settings
- Secrets and variables
- Actions
- Repository Secrets
- OR Repository Variables

Variables are usually configure something in the build, for example: NO_FLIPPER=1 means flipper won't be included in the builds.

#### Secret Files

There are a couple of files that we use: provisioning profiles, signing certificates, service account credentials and keystore.


For now these are stored as base64. All Secrets that contain base64 file content is suffixed with BASE64.

During workflows these are written into file via `echo "$secret_base64" | base64 --decode > secret.file`.

To update such values you should do the inverse and decode them: `cat secret.file | base64 | pbcopy`. 

> Note: pbcopy copies the received input into clipboard on mac. 
> For Linux you may use xclip/xsel
> For Windows clip
> Or simply just let it written into the console and copy it by hand.

If the these file become to big to fit into the secret limit, an alternative is to store the file encrypted in the repo and store the decryption key as a secret.

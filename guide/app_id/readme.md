# App IDs

This is called the bundle id within XCode and is a reverse domain identifier which is unique per application. For example `uk.co.simpleweb.myapp`

A shared App ID should be used in development unless you are using one of the following:

  - App Groups
  - Apple Pay
  - Associated Domains
  - Complete Protection
  - Protected Unless Open
  - Protected Until First User Authentication
  - Game Center
  - HealthKit
  - HomeKit
  - Compatible with Xcode 5
  - Include CloudKit support
  - (requires Xcode 6 and explicit App ID)
  - In-App Purchase
  - Network Extensions
  - Personal VPN
  - Push Notifications
  - Wireless Accessory Configuration

An App ID is however required before submitting to iTunes Connect.

Identifiers **do not** download to your computer and are only used in reference to iTunes Connect and Provisioning Profiles.

#### Create a Shared App ID

- Go to the [iOS Dev Centre - Identifiers](https://developer.apple.com/account/ios/identifiers/bundle/bundleList.action)

- Click the plus icon to add a new iOS App ID

- Give the App ID a the name **Development**

- Set the App ID Suffix to be **Wildcard App ID** and enter `*` as the value.

- Check all available services and click continue

- Confirm the information on the next page and finally click submit to create.

#### Create a Production App ID

- Go to the [iOS Dev Centre - Identifiers](https://developer.apple.com/account/ios/identifiers/bundle/bundleList.action)

- Click the plus icon to add a new iOS App ID

- Give the App ID a sensible name such as **Contactzilla Mobile Importer**

- Give the App Bundle ID a reverse-domain name such as `com.contactzilla.mobileimporter`

  > Note: Bundle ID's should not have hyphens since this breaks compatibility with Android if you want to use the same value.

- Check any relevant services you require and click continue

- Confirm the information on the next page and finally click submit to create.

  > Note: App IDs can not change once the app has been published please ensure that this information is correct.

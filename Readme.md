# iOS Development For Teams

Follow There instructions to get your computer set up for iOS development. View the blog post [here](http://simpleweb.co.uk/2014/setting-up-your-team-for-ios-app-development).

## How to use this repository

- Fork this document
- Decide on a shared password for your `p12` files.
- Generate your shared files (see instruction in example files)
  - `/certificates/apn/_template/CertificateSigningRequest.certSigningRequest`
  - `/certificates/production/company_name/CertificateSigningRequest.certSigningRequest`
  - `/certificates/production/company_name/ios_distribution.cer`
  - `/certificates/production/company_name/Certificates.p12`
- Create a `Development` provisioning profile and Wildcard App ID
- Change the `company_name` paths to your company name as well as in this document.
- Your team can follow the instructions below


## Notes & Caveats

- Only use an Apple ID with your Company e-mail address

- Please follow these instructions carefully some instructions look similar but have subtle differences

- Certificates should be backed up as `p12` files since the `cer` file does not have all of the information required to transfer between terminals.

- **Never make your certificate files public.**

## Certificates

There are seven types of certificates used in iOS Development and Deployment.

- Intermediate Certificate
- Development
  - iOS App Development
  - Apple Push Notification service SSL (Sandbox)
- Production
  - App Store and Ad Hoc
  - Apple Push Notification service SSL (Production)
  - Pass Type ID Certificate
  - Website Push ID Certificate
  
 
### Intermediate Certificate

To use your certificates, you must have the intermediate signing certificate in your system keychain. This is automatically installed by Xcode. However, if you need to reinstall the intermediate signing certificate open the file `certificates/AppleWWDRCA.cer` in keychain access.

### iOS App Development

#### Generate an iOS App Development Certificate

- In the Applications folder on your Mac, open the Utilities folder and launch Keychain Access.

- Within the Keychain Access drop down menu, select Keychain Access > Certificate Assistant > Request a Certificate from a Certificate Authority.

- In the Certificate Information window, enter the following information:
  - In the User Email Address field, enter your **Company email address**.
  - In the Common Name field, create a name for your private key (e.g. **Adam Butler**).
  - The CA Email Address field should be left empty.
  - In the "Request is" group, select the "Saved to disk" option.
  - Save this file to `certificates/development/{firstname}_{surname}/CertificateSigningRequest.certSigningRequest`

- Click Continue within Keychain Access to complete the CSR generating process.

- Go to [iOS Dev Centre - Certificates](https://developer.apple.com/account/ios/certificate/certificateList.action)

- Click the plus icon to add a new iOS Certificate

- Select **iOS App Development** and continue through to the CSR upload screen

- Upload your `CertificateSigningRequest.certSigningRequest` file then click generate

- Click download and save the file as `certificates/development/{firstname}_{surname}/ios_development.cer`

- Open the file, this should launch Keychain Access. You can verify that your certificate has installed if you see the certificate

    iPhone Developer: {your_name} ({uuid})
    
- Select this certificate then go to `File > Export Items` and save this file as `certificates/development/{firstname}_{surname}/Certificates.p12`

  - Give this file your password
  
- Commit this change and push to origin

#### Restore a iOS App Development Certificate

- Download your p12 file for example `certificates/development/adam_butler/Certificates.p12`

- Open the file, this should launch Keychain Access and will ask you for your password. You can verify that your certificate has installed if you see the certificate

    iPhone Developer: {your_name} ({uuid})
    

### Apple Push Notification service SSL (Sandbox)

#### Generate an iOS App Development Certificate

- Go to [iOS Dev Centre - Certificates](https://developer.apple.com/account/ios/certificate/certificateList.action)

- Click the plus icon to add a new iOS Certificate

- Select **Apple Push Notification service SSL (Sandbox)** and then continue

- Select your App ID then continue to the CSR upload screen

- Upload the `certificates/apn/_template/CertificateSigningRequest.certSigningRequest` file then click generate

- Click download and save the file as `certificates/apn/{bundle_id}/aps_development.cer`

- Open the file, this should launch Keychain Access. You can verify that your certificate has installed if you see the certificate

    Apple Development IOS Push Services {bundle_id}
    
- Select this certificate then go to `File > Export Items` and save this file as `certificates/apn/{bundle_id}/Certificates.p12`

  - Give this file your password
  
- Commit this change and push to origin

### App Store and Ad Hoc

This certificate is like the iOS App Development but is shared among the team.


#### Restore a App Store and Ad Hoc Certificate

- Download the p12 file from `certificates/production/company_name/Certificates.p12`

- Open the file, this should launch Keychain Access and will ask you for your password. You can verify that your certificate has installed if you see the certificate

    iPhone Distribution: {your_name} ({uuid})
    
#### Pass Type ID Certificate

> *Yet to be documented*

#### Website Push ID Certificate

> *Yet to be documented*


## Identifiers

Identifiers should be created on deployment to Ad-hoc or the App Store. There is one `Development` AppID that can be used otherwise.

Identifiers **do not** download to your computer and are only used in reference to iTunes Connect and Provisioning Profiles.

#### Create a Production App ID

- Go to the [iOS Dev Centre - Identifiers](https://developer.apple.com/account/ios/identifiers/bundle/bundleList.action)

- Click the plus icon to add a new iOS App ID

- Give the App ID a sensible name such as **Contactzilla Mobile Importer**

- Give the App Bundle ID a reverse-domain name such as `com.contactzilla.mobileimporter`

  > Note: Bundle ID's should not have hyphens since this breaks compatibility with Android
      
- Check any relevant services you require and click continue

- Confirm the information on the next page and finally click submit to create.

  > Note: App IDs can not change once the app has been published please ensure that this information is correct.


## Devices

The device list needs to remain structured to have confidence that we are targeting the correct devices, this becomes especially important if we use [TestFlight](https://www.testflightapp.com) or [HockeyApp](http://hockeyapp.net/).

Please name devices in the following format -

  [Full name / Company Name] - [Device + Generation] - #[id]
  
For example

  Adam Butler - iPad Mini Retina 1st Gen - #1
  
...or...

  Simpleweb - iPad Retina 3rd gen - #1

## Provisioning Profiles

Provisioning Profiles should be created on deployment to Ad-hoc or the App Store. There is one `Development` Provisioning Profile that can be used otherwise.

Unlike certificates provisioning profiles to not need backing up and can be downloaded directly from the Dev Center.

#### Download the Development Provisioning Profile

- Go to the [iOS Dev Centre - Provisioning Profiles](https://developer.apple.com/account/ios/profile/profileList.action)

- Click on the profile with the name `Development`

- Click Edit

- **If your certificate is checked and your target device is check then press cancel otherwise select All certificates and All devices.** 

  > The reason for selecting all certificates and devices is that it will reduce the frequency of this certificate being regenerated. This also means all computers with a certificate are ready to develop on any app.
  
- Finally download the Profile and open the file, this will either open in Keychain Access or iPhone Configuration Utility depending on what version of OSX you use. If opened in iPhone Configuration Utility you will prompted to confirm you wish to add this profile to your library.
  
#### Create a provisioning profile for App Store


- Go to the [iOS Dev Centre - Provisioning Profiles](https://developer.apple.com/account/ios/profile/profileList.action)

- Click the plus icon to add a new provisioning profile

- Select either App Store or Ad Hoc

- Select your App ID

  > Note: Never set the App ID to Development
  
- In certificates select [Company Name] (iOS Distribution)

  > Note: This should be done regardless of who you are publishing on behalf of
  
> *Can not document complete process due to Dev Center bug*

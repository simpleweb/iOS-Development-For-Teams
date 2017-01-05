# Setup Apple Push Notification Service SSL (sandbox)

## Important

**This certificate is shared. If a valid certificate & key has been backed up as a P12 file in `certificates/apn/{app_bundle_id}/sandbox/Certificates.p12` then a new certificate should not be created. Follow the "Restore your shared certificate" instructions below.**

Creating a new certificate will invalidate the previous one and should only be done if the P12 file has not been backed up, the password for the P12 file has been lost, the certificate has expired or on setup for the first time.

## Create certificate

- In the Applications folder on your Mac, open the Utilities folder and launch Keychain Access.

- Within the Keychain Access drop down menu, select Keychain Access > Certificate Assistant > Request a Certificate from a Certificate Authority.

- In the Certificate Information window, enter the following information:
  - In the User Email Address field, enter the **shared email address** (e.g. info@mycompany.com).
  - In the Common Name field, create a name for your shared key (e.g. **Simpleweb LTD**).
  - The CA Email Address field should be left empty.
  - In the "Request is" group, select the "Saved to disk" option.
  - Save this file to `certificates/apn/{app_bundle_id}/sandbox/CertificateSigningRequest.certSigningRequest`

- Click Continue within Keychain Access to complete the CSR generating process.

- Go to [iOS Dev Centre - Certificates](https://developer.apple.com/account/ios/certificate/certificateList.action)

- Click the plus icon to add a new iOS Certificate

- Select **iOS App Development** and continue through to the CSR upload screen

- Upload your `CertificateSigningRequest.certSigningRequest` file then click generate

- Click download and save the file as `certificates/apn/{app_bundle_id}/sandbox/ios_distribution.cer`

- Open the file, this should launch Keychain Access. You can verify that your certificate has installed if you see the certificate

    iPhone Distribution: {company} ({team_id})

## Backup your shared certificate

- Select this certificate then go to `File > Export Items` and save this file as `certificates/apn/{app_bundle_id}/sandbox/Certificates.p12`

- Give this file a shared password (or leave blank if the repository is private)

## Restore your shared certificate

- Simply open the file you saved in `certificates/apn/{app_bundle_id}/sandbox/Certificates.p12` and enter your password when prompted.

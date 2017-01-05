# Setup iOS App Development Certificate

## Create certificate

- In the Applications folder on your Mac, open the Utilities folder and launch Keychain Access.

- Within the Keychain Access drop down menu, select Keychain Access > Certificate Assistant > Request a Certificate from a Certificate Authority.

- In the Certificate Information window, enter the following information:
  - In the User Email Address field, enter your **email address**.
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

    iPhone Developer: {your_name} ({team_id})

## Backup your personal certificate

- Select this certificate then go to `File > Export Items` and save this file as `certificates/development/{firstname}_{surname}/Certificates.p12`

- Give this file your personal password

## Restore your personal certificate

- Simply open the file you saved in `certificates/development/{firstname}_{surname}/Certificates.p12` and enter your password when prompted.

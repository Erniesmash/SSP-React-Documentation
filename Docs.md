# Docs
Welcome to the Docs!

## Prerequisites
You are expected to have installed the following:
- Node.js from the [Official Website](https://nodejs.org/en/download)
- Visual Studio Code
- Visual Studio 2022

## Initial Setup
To start coding in React, there is some configuration that has to be done for npm (Node Package Manager).
It has to be configured to work with the company's proxy server and CAs (Certificate Authorities).

### Proxy Setup
1. Open cmd
2. Run `reg query "HKCU\Software\Microsoft\Windows\CurrentVersion\Internet Settings" /v AutoConfigURL`
3. Copy the url returned and search it in your browser, which will download the .pac file
4. Open the .pac file and look for the proxy address returned
5. Run `npm config set proxy http://your.proxy.here.com:9000` and `npm config set https-proxy http://your.proxy.here.com:9000`

### CA Setup
1. Open Chrome settings
2. Navigate to Privacy and security -> Security -> Manage certificates -> Local Certificates -> View Imported Certificates
3. Click on the Export button
4. Run `npm config set cafile /path/to/your/company-ca.crt`

### Setup Verification
Verify that the npm settings were successfully updated using the following commands:
`npm config get cafile`
`npm config get proxy`
`npm config get https-proxy`

Finally, run `npm install -g npm@latest` to update to the latest version.
If your setup was correct, there should be no errors during this process.
# Sales Support Portal Documentation
Welcome to the Sales Support Portal Docs!

## Overall Structure
```sh
Sales Support Portal
|
+-- Frontend
|   +-- React with Typescript
|   +-- Vite
|
+-- Backend
|   +-- ASP.NET API
```

## Background

## Purpose

## Project Scope

## Requirements Gathered

## System Design

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

## Project Structure
The project uses a standardised file structure. Most of the code will be located in the src folder.
The file structure will be as follows:
```sh
src
|
+-- app               # application layer containing:
|   |
|   +-- routes        # application routes / pages
|   +-- app.tsx       # main application component
|   +-- router.tsx    # application router configuration
+-- assets            # assets folder can contain all the static files such as images, fonts, etc.
|
+-- components        # shared components used across the entire application
|
+-- config            # global configurations, exported env variables etc.
|
+-- features          # feature based modules
|
+-- hooks             # shared hooks used across the entire application
|
+-- lib               # reusable libraries preconfigured for the application
|
+-- types             # shared types used across the application
|
+-- utils             # shared utility functions
```
The features folder contains code specific to that feature. An example of a feature is a 'comments' or 'discussions' feature
for a social media website. The features folder will have the following structure:
```sh
src/features/awesome-feature
|
+-- api         # exported API request declarations and api hooks related to a specific feature
|
+-- assets      # assets folder can contain all the static files for a specific feature
|
+-- components  # components scoped to a specific feature
|
+-- hooks       # hooks scoped to a specific feature
|
+-- stores      # state stores for a specific feature
|
+-- types       # typescript types used within the feature
|
+-- utils       # utility functions for a specific feature
```

## Project Standards
For code quality reasons, there are some project standards that are enforced.
The project contains configuration files for **ESLint** and **Prettier**. These are extensions that can be downloaded and installed in VS Code. It is highly recommended that you do so.

The configuration file for **ESLint** is set to prevent imports between features. Features should only import from the shared components.
The configuration file is also set to enforce the use of `kebab-case` for the naming of all files in the project.
`kebab-case` refers to the use of only small letters and hyphens between words.

The configuration file for **Prettier** will allow for any new code to be automatically indented and formatted in a standardised manner after saving (Ctrl + S).

The project also uses **Typescript**, and has been configured to avoid messy import statements like `../../../component`. Simply use `@/*` instead, which represents `./src/*`. For example, some file that lives in `src/components/my-component` can be accessed using `@/components/my-component` instead of `../../../components/my-component`.

## Common Commands
- Start Development Server: `npm run dev`
- Stop Development Server: Ctrl + C
- Restore All Dependencies: `npm install`
- Check Code against ESLint: `npx eslint`
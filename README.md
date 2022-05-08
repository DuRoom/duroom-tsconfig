# DuRoom Typescript Config

A standardised `tsconfig.json` for use in DuRoom extensions.

## Usage

You'll need to configure a `tsconfig.json` file to ensure your IDE sets up Typescript support correctly.

You need to install this package as a dev dependency to your extension JS:

```properties
npm install --save-dev duroom-tsconfig
yarn add --dev duroom-tsconfig
```

A baseline `tsconfig.json` is provided below that you can modify as needed. This file needs to be copied into your extension's `js` folder for your IDE to apply the correct settings.

```jsonc
{
  // Use DuRoom's tsconfig as a starting point
  "extends": "duroom-tsconfig",
  // This will match all .ts, .tsx, .d.ts, .js, .jsx files in your `src` folder
  // and also tells your Typescript server to read core's global typings for
  // access to `dayjs` and `$` in the global namespace.
  "include": ["src/**/*", "../vendor/duroom/core/js/dist-typings/@types/**/*"],
  "compilerOptions": {
    // This will output typings to `dist-typings`
    "declarationDir": "./dist-typings",
    "baseUrl": ".",
    "paths": {
      "duroom/*": ["../vendor/duroom/core/js/dist-typings/*"]
    }
  }
}
```

You'll also need to ensure that you run `composer update` in your extension's root directory to ensure that a copy of DuRoom core is downloaded to your `vendor` folder. Remember that `vendor` should **not** be committed to Git repositories.

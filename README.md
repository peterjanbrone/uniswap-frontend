# Skynet Uniswap Frontend Demo

This is a demo on how to run the [Uniswap Frontend](https://github.com/Uniswap/uniswap-frontend) on [Skynet](https://siasky.net).  
To run the Uniswap Frontend on Skynet, we need to do some minor tweaks to ensure the Dapp navigates relative to the Skyink URL on Skynet.

## Required Changes

In `App.js`, update the `BrowserRouter` basename, so all locations point to Skynet as their base URL.
```
<BrowserRouter basename={`${window.location.pathname}#`}>
```

In `src/i18n.js`, update the `loadPath` so it loads the locale from a relative path, rather than an absolute path.
```
i18next
  ...
  .init({
    backend: {
      loadPath: './locales/{{lng}}.json'
    },
```

In `package.json`, update the `homepage` so the App is built using a relative path, rather than the root.
```
{
  ...
  "homepage": ".",
  ...
```

## Configuration

The Uniswap Frontend requires some environment variables to be set, in order for it to function.
You will find these in `.env.local.example`. Simply copy this file to `.env.local` and fill them out.

```
REACT_APP_CHAIN_ID="1"
REACT_APP_NETWORK_URL=""
REACT_APP_PORTIS_ID=""
REACT_APP_FORTMATIC_KEY=""
REACT_APP_IS_PRODUCTION_DEPLOY="false"
```

## Deployment

Deploying the Uniswap Frontend is very easy. First we need to build the project using `yarn`.
Before you continue, make sure you have completed the required changes, and have a valid configuration.

### Install Dependencies
```bash
yarn
```

### Build Project
```bash
yarn build
```

### Deploy to Skynet

You can deploy the dapp to Skynet by uploading the entire buildfolder at siasky.net.
This will give you a skylink, which houses your dapp. To access the Uniswap Frontend,
simply navigate to `https://siasky.net/[skylink]/build/index.html`.

## SkyDapp URL
https://siasky.net/EAByx9EagK71BoS1za93Q9s0l7xSe7VG6P8aUEtJK4mmDQ/build/index.html#/swap
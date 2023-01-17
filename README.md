# ION Tools

This repo is a fork of this one https://github.com/decentralized-identity/ion-tools.

It eliminates support for `ED25519` and upgrades `@noble/secp256k1` version to `1.7.1` in order to allow its execution in the browser.

`ED25519` has been removed as it is not needed for the scenario in which we use this library, so we prefer to remove unnecessary dependencies.

## Installation
```bash
npm install ion-tools-neoke
```

## Usage (browser)
```javascript
import { DID, generateKeyPair } from 'ion-tools-neoke/dist/browser-bundle';

const authnKeys = await generateKeyPair();
const did = new DID({
  content: {
    publicKeys: [
      {
        id: 'key-1',
        type: 'EcdsaSecp256k1VerificationKey2019',
        publicKeyJwk: authnKeys.publicJwk,
        purposes: [ 'authentication' ]
      }
    ],
    services: [
      {
        id: 'domain-1',
        type: 'LinkedDomains',
        serviceEndpoint: 'https://foo.example.com'
      }
    ]
  }
});
```

### Typescript
```bash
cd YOUR_INDEX_FOLDER
echo "declare module 'ion-tools-neoke/dist/browser-bundle';" > ion-tools-neoke.ts.d
```

### Browser compatibility

`package.json`

```json
..
  "browserslist": [
    ">0.2%",
    "not dead",
    "not op_mini all",
    "not IE 11"
  ],
..
```
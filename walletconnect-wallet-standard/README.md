# walletconnect-wallet-standard

Register the [WalletConnect sign client](https://github.com/WalletConnect/walletconnect-monorepo/tree/v2.0/packages/sign-client) as a [wallet-standard standard wallet](https://github.com/wallet-standard/wallet-standard) with [solana features](https://github.com/solana-labs/wallet-standard/tree/master/packages/core/features) on window

## Usage

Import and call the `registerWalletConnectWalletStandard` function:

```js
import { registerWalletConnectWalletStandard } from "walletconnect-wallet-standard";

// Get WalletConnect project ID from https://cloud.walletconnect.com
const projectId = "4374d1c29d9988dcea189594474af595";

registerWalletConnectWalletStandard({
  options: {
    projectId,
    metadata: {
      name: "My Dapp",
      description: "My Dapp description",
      url: "https://my-dapp.com",
      icons: ["https://my-dapp.com/logo.png"],
    },
  },
});
```

The WalletConnect adapter will be registered as a standard wallet:

```js
import { getWallets } from "@wallet-standard/app";
const { get } = getWallets();
const allWallets = get(); // the WalletConnect adapter should be a part of `allWallets`
```

## NOT SUPPORTED

`signTransaction` is currently doesn't work with WalletConnect sign client. This means that the WalletConnect adapter will not be able to sign transactions. This is a temporary limitation that will be resolved in the future.

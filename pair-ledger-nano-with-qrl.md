![QRL article banner](assets/banner-article.png)

# Pair Ledger Nano With QRL

**Short answer.** QRL works with a Ledger Nano through the QRL app installed on the device, with the QRL wallet driving it. Ledger Live manages the device and its apps, but it does not show or manage QRL accounts. The wallet displays your addresses and builds each transaction; the device holds the keys and approves the signature.

## What you need

A Ledger Nano S or Nano X with current firmware, the QRL app installed on it, and the QRL wallet on a computer with a working USB port. The device's own recovery phrase should already be written down and stored before any QRL is involved, because the device backup protects every app on it, not just this one.

The split of work is worth stating plainly before you plug anything in. The device stores keys and produces signatures. The wallet stores the transaction history it can see, builds the transaction you asked for, and sends it to the node. Neither one alone is a wallet in the everyday sense: the pair is.

Because of that split, Ledger Live will not show a QRL balance. It is the tool for firmware, app installation and the device's own accounts, and QRL does not appear in it as an account type. Anyone who tells you to add QRL in Ledger Live is describing a different product.

## Installing the QRL app

Open Ledger Live, connect and unlock the device, and go to the app manager. Search for QRL in the catalogue and install it. The app is small, but a Nano S holds only a few at a time, so you may be asked to remove another app to make room, which does not affect the coins that app managed.

If QRL does not appear in the catalogue, the device firmware is the usual reason. Update it through Ledger Live first and search again. A device that has never had its firmware updated can show a catalogue that is older than the one the wallet expects.

People ask what happened to the QRL app from time to time, usually because they remember installing it years ago. It is the same device-side app: install it, open it, and the wallet finds it. There is no phone version of it, and it is not something you run on a computer.

Nothing about the install touches your keys. The app is code that runs on the device and asks it to sign; the seed stays where it was.

## Connecting from the wallet

Start the QRL wallet, choose the hardware option, and follow the prompt. Unlock the device first, then open the QRL app on it, and only then confirm the connection. Opening the app after the wallet has already looked for the device is the most common ordering mistake.

On Windows the first connection may install a driver, and on Linux the device needs permission rules before the wallet can talk to it. A browser-based QRL interface has an extra layer, because the browser has to be granted access to the USB device; the desktop build avoids that layer entirely, which is why [QRL Desktop Wallet vs Web Wallet](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/qrl-desktop-vs-web-wallet.md) recommends it for a paired device.

Once connected, the wallet lists the addresses derived from the device. Those addresses were never on your computer in usable form: the wallet can ask the device for a public address, and it can ask the device to sign, but it cannot ask for the key.

## What the device signs

You enter the recipient and the amount in the wallet. The wallet builds the transaction, sends it to the device, and the device shows enough of it for you to approve. Approve on the device and the signature comes back to the wallet, which broadcasts the signed transaction to a node.

The keys stay on the device throughout, and the approval step is the point of the hardware: a compromised computer can propose a transaction, but it cannot sign one without you pressing the button.

What the device does not change is the one-time key model. A QRL address still has 1,024 signatures behind it, drawn in order, and the device keeps track of where that count has reached. The count moving forward is why the device backup matters as much as the wallet backup: restoring the device from its phrase is how the same addresses come back. [How Many QRL OTS Keys Remain?](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/how-many-qrl-ots-keys-remain.md) covers what happens when the count runs out, and [Is the QRL Wallet Safe to Use?](https://github.com/qrl-wallet/signatures-and-comparisons/blob/main/is-qrl-wallet-safe-to-use.md) covers the habits around a device.

## Mining to a web wallet and the Ledger question

You can mine to an address in a web wallet, and people do. The reward arrives at that address like any other payment, and nothing about mining requires a particular kind of wallet.

The question that follows is whether you then need a separate wallet for the Ledger. You do not need a second installation, but you do need to understand that the two are different key sources. An address inside a web wallet has its keys in that interface, not on the device, so a Ledger in a drawer is not protecting the mining rewards.

If you want the rewards behind the device, point the miner at an address derived from the Ledger and send from that address when you want to move the balance. That address signs through the device, which means the device has to be present for a spend. Choose deliberately between convenience and separation rather than assuming the device covers an address it never derived.

## When the device is not recognised

Work through the physical layer before the software. Use a cable that carries data rather than one that only charges, plug into the machine directly rather than through a hub, and try a different port. Close Ledger Live while the wallet is connected, because two applications claiming the device at once usually produces a failure in both.

Then check the order: unlock, open the QRL app, and connect from the wallet. A device sitting on its dashboard is not presenting the QRL app to the computer.

If the device is still invisible, update the firmware, restart the wallet, and try a different machine. A device that works elsewhere is a driver or permission problem, not a broken device. Never type the device's recovery phrase into any software while troubleshooting; no fix requires it.

[Download the Official QRL Wallet](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/download-the-official-qrl-wallet.md) has the current build if the wallet itself is out of date, and [QRL vs Trezor on Quantum Readiness](https://github.com/qrl-wallet/signatures-and-comparisons/blob/main/qrl-vs-trezor-quantum-readiness.md) explains what a hardware device does and does not change about quantum resistance.

## FAQ

### Does Ledger Live support QRL?

Not as an account type. Ledger Live installs the QRL app and manages the device; the QRL wallet is what shows balances and builds transactions.

### Do I have to store QRL on a Ledger?

No. The desktop wallet keeps keys in a local file and works without a device. The device adds separation between the keys and the computer.

### Can I use a Nano X from a phone app?

The QRL app runs on the device, but there is no mobile build of the QRL wallet in the current release, so a phone cannot drive the device for QRL. Use a computer.

### Is a Ledger address quantum-proof because it is on a device?

No. The device protects keys from the computer, not from a future quantum attack. QRL's resistance comes from its signature scheme, and the device signs the same scheme.

<!-- answers: Q162, Q193, Q206, Q207, Q208, Q229 -->

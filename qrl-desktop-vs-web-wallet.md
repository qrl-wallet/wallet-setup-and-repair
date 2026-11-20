![QRL article banner](assets/banner-article.png)

# QRL Desktop Wallet vs Web Wallet

**Short answer.** The desktop wallet keeps your keys in a wallet file on your own machine. A browser wallet keeps them in the tab you opened, so its safety rests on that page being what it claims to be. For a balance you intend to hold, the desktop build is the safer default. Both are self-custody: no account, no email, and no server that can freeze a balance.

## Where the keys live in each

A desktop install is a file you download, check and run. On first use it creates a wallet file on disk, encrypted with a password you choose, and derives addresses from the mnemonic it showed you. Signing happens inside the application. What leaves your machine is a signed transaction, not a private key.

A browser wallet reverses the order. You open a page, the page generates or imports keys inside the tab, and those keys live in the browser's storage or in a file you export. The ownership model is still self-custody: the keys are yours and no server can spend them.

The difference is provenance. The code that signed for you in a browser arrived over the network minutes earlier and can change with the next page load. A desktop build can change too, but only when you install a new one, and you can hash the download before you do. That single distinction drives most of the advice below.

Neither model protects a badly stored mnemonic. A wallet file on a machine that anyone else can log into is a shared wallet whatever the application is.

## What each is good for

The desktop wallet is built for repeated use on a machine you control. It pairs with a Ledger Nano through the QRL app on the device, and it gives you a file you can copy into your own backup routine.

The browser wallet is built for a machine you do not own. A borrowed laptop, a friend's desktop, a machine at work: nothing is installed, nothing persists after you close the tab, and the balance is reachable for the few minutes you need. For a quick send from a machine where you cannot install software, that is a real advantage.

Where the browser version earns its place is convenience, and where it costs you is the surface it adds. Every extension, every page script and every typo in an address bar sits between your keys and the screen you are reading. A desktop build has fewer moving parts because it has fewer neighbours.

## The Android and mobile question

There is no mobile build in the current release. The release page lists assets for Windows, macOS and Linux, and that list, not a search result, is the answer to whether a phone app exists.

You will find pages offering a QRL wallet for Android. One of them, MyQRLWallet, is an independent QRL 2.0 testnet wallet built by another team. It is a different product from this wallet, and a testnet balance on it is not a mainnet balance. That distinction matters when someone sends you a link: a testnet wallet cannot hold, send or restore real QRL.

Any phone app that asks you to type your mnemonic before it shows a balance has your keys the moment you finish typing. A wallet that needs the phrase to restore is doing the one legitimate thing with it; a page that asks you to paste it into a form is not.

## Long-term storage

For a balance you are holding rather than spending, the desktop wallet is the better fit. Your job is then a short list: keep the wallet file somewhere your normal backup reaches, keep its password somewhere else, and keep the mnemonic on paper, offline, in two places. [Back Up a QRL Seed Phrase](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/back-up-a-qrl-seed-phrase.md) covers the phrase itself, and [Create Your First QRL Address](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/create-your-first-qrl-address.md) walks through the first address and the backup that belongs with it.

What you should not do is treat the wallet file as the whole backup. The file without its password is a locked box, and the password without the file is a word you remember. The mnemonic is the only part that survives losing the machine.

## How to move between them

The mnemonic restores the same keys in either interface, so moving from desktop to browser, or back, is a restore rather than a transfer. You type the phrase once, into a page you have verified is the one you meant to open, and the addresses appear after sync.

Do not run two copies at once. QRL addresses sign with one-time keys drawn in order, and two live copies can draw the same key for two different transactions. [Is the QRL Wallet Safe to Use?](https://github.com/qrl-wallet/signatures-and-comparisons/blob/main/is-qrl-wallet-safe-to-use.md) explains the risk in plain terms, and the practical rule is simple: when you restore in a new place, stop using the old one.

If the new interface will not connect, the problem is usually the node rather than the restore. [Download the Official QRL Wallet](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/download-the-official-qrl-wallet.md) has the current build, and [Pair Ledger Nano With QRL](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/pair-ledger-nano-with-qrl.md) is the next read if you keep keys on a device instead of a file.

## FAQ

### Is a browser wallet unsafe by default?

No. The keys are still yours and the code is public. The risk is that the page can change between visits, so you are trusting a delivery each time rather than one file you installed once.

### Can I import my desktop wallet file into a browser wallet?

Only if that interface reads the QRL wallet file format and you have the password. If it does not, restore from the mnemonic instead of converting files by hand.

### Does the desktop wallet need an account or an email address?

No. There is no sign-up step. The application creates a local wallet file and never registers it with a service.

### Can I keep the same wallet on a laptop and a phone?

Not on a phone, because there is no mobile build in the current release. Between two computers, restore one at a time and stop using the first copy once the second is synced.

<!-- answers: Q082, Q205, Q227 -->

![QRL article banner](assets/banner-article.png)

# Restore QRL Wallet From a Mnemonic

**Short answer.** A mnemonic restores the wallet's keys, and with them every address derived from that seed. A wallet file restores the same wallet only if you still have the password it was created with. Transaction history is on-chain, so it reappears once the restored wallet syncs. With neither backup there is nothing left to restore.

## Which backup you have

QRL gives you two things that look like backups, and they are not interchangeable. The mnemonic is a word list that rebuilds the seed. The wallet file is an encrypted container that holds the derived keys and needs the password you set when you made it.

Sort out which one you are holding before you start. A phrase on paper, a file with a `.json` extension, a password you remember, a screenshot you took years ago: each of those leads to a different procedure, and mixing them up is how people conclude a wallet is gone when it is not.

If you have both, use the mnemonic. It is the one that survives a forgotten password, a renamed file and a new operating system.

## Restoring from the mnemonic

Install the current build on the machine that will hold the wallet, and let it sync. Then choose the restore option rather than creating a new wallet, and enter the words in the order you wrote them.

Spelling and order both matter, and the wallet will reject a phrase that fails its checksum. That rejection is useful: it means you mistyped rather than lost something, so read the paper again rather than trying variations from memory.

When the phrase is accepted, the wallet asks for a new password and writes a fresh wallet file. The addresses that appear are the ones the seed produces, not new ones. They may take a moment to show a balance, because the wallet has to catch up with the chain before it can report what those addresses have received.

Do not run the old copy and the restored copy at the same time. Pick the new machine and stop using the old one.

## Restoring from the wallet file

Put the file where the application expects wallets, or point the wallet at it through its import option, then enter the password it was created with. The addresses and their key state come back as they were at the moment the file was last written.

Without that password the file is a block of ciphertext. There is no reset, no hint question and no server that can decrypt it for you, because the encryption key is derived from what you typed and nothing else.

A file restored from a backup can be older than the wallet was. If you copied it a year ago and kept using the wallet afterwards, you have the state from a year ago, which is why a copy taken at the end of each session is worth more than one taken at the start.

## What comes back and what does not

Keys come back. Addresses come back. Balances reappear after sync, and transaction history is read from the chain rather than from your file, so it fills in on its own.

What does not come back is anything the wallet never stored: a label you gave an address, a note you kept beside the file, the password itself. Settings are rebuilt by using the application again.

The one state that must not move backwards is the one-time key index. QRL addresses sign with keys drawn in order, and a restore that rewinds the count can hand out a key that has already signed. The wallet keeps that count in its own data, and [How Many QRL OTS Keys Remain?](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/how-many-qrl-ots-keys-remain.md) explains why an old wallet file is a risk rather than a convenience. If you restore an old file, treat it as a wallet to empty into a fresh address, not one to keep signing with.

## If you have neither

Then there is no procedure, no tool and no service that will bring the wallet back. The keys exist only in the two things you were meant to keep, and without them the addresses are still on the chain but nothing can sign for them.

This is the point where people are contacted by someone offering to recover a wallet for a fee. That offer cannot be true: an organisation with no copy of your seed has nothing to work from. [Recover a Lost QRL Wallet](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/recover-a-lost-qrl-wallet.md) sets out what is and is not possible, and [Is the QRL Wallet Safe to Use?](https://github.com/qrl-wallet/signatures-and-comparisons/blob/main/is-qrl-wallet-safe-to-use.md) covers the habits that keep you out of this position.

If the loss is partial, meaning you have one of the two backups, the answer is usually the good news story. A phrase without the file restores on any machine. A file without the phrase restores only with its password. Neither case needs a third party.

Before you restore anything, read [Back Up a QRL Seed Phrase](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/back-up-a-qrl-seed-phrase.md) and check that what you are about to trust as a backup is stored the way that page describes. A restore is also the moment to confirm the copy works, so doing it once on purpose is better than discovering the problem later. Once the wallet is running again, [Create Your First QRL Address](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/create-your-first-qrl-address.md) covers the first address if you decide to start clean.

## FAQ

### Can I restore with the mnemonic if I lost the wallet file?

Yes. The phrase rebuilds the seed, and the seed rebuilds the addresses. You set a new password when the restored wallet writes its new file.

### Can I restore with the wallet file if I forgot the password?

No. The file is encrypted with that password, and there is no reset path because no service holds a copy of it.

### Do my transactions come back after a restore?

Yes. History lives on the chain, not in your file, so it reappears as the restored wallet syncs.

### Is it safe to reuse an old wallet file backup?

Only to recover the funds from it. An old file can carry an out-of-date key index, so move the balance to a fresh address rather than continuing to sign with it.

<!-- answers: Q170, Q171, Q190, Q211 -->

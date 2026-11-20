![QRL article banner](assets/banner-article.png)

# Recover a Lost QRL Wallet

**Short answer.** What you can recover depends on which half you still have: the mnemonic, or the wallet file together with its password. With one of those pairs you can restore the wallet yourself on any machine. With neither, there is no recovery, by anyone, and no service that can change that.

## What you need

There are two things that restore a QRL wallet, and they are not interchangeable.

The mnemonic is a word list that rebuilds the seed, and the seed rebuilds every address derived from it. It survives a lost machine, a forgotten password and a dead disk.

The wallet file is an encrypted container holding the keys and their state. It restores the same wallet only when you also have the password it was created with.

Before anything else, work out which of those you have. A sheet of paper with numbered words is the first. A file ending in `.json` is the second, and it is useless without the password you typed when you made it.

The file alone is the case people overestimate. Without its password it is a locked box, and a locked box is not a backup however carefully it was copied.

## The mnemonic path

Install the current build on a machine that works, let it sync, and choose the restore option rather than creating a new wallet. Enter the words in order.

The wallet validates the phrase and rejects one that does not check out, which is usually a mistyped word rather than a lost cause. Read the paper again before trying variations from memory.

Once accepted, the wallet asks for a new password and writes a new file. The addresses that appear are the ones the seed produces, and the history fills in as the wallet syncs. https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/restore-qrl-wallet-from-mnemonic.md covers the steps in detail.

A phrase copied by hand can carry a misspelling that nobody notices until the day it is needed, and the wallet's checksum catches it at that moment rather than earlier. That is the argument for testing a restore while the wallet is still empty: ten minutes then, instead of an evening of doubt later.

## The wallet file path

Put the file where the application expects wallets, or import it, then enter its password. The addresses and the key index come back as they were when the file was last written.

The index is the part people forget. A file copied a year ago carries the index from a year ago, so restoring it and signing can hand out a key that has already signed. An old file is a way to recover funds, not a way to keep using an address as if nothing happened.

If the restored file shows an address you have since moved away from, that is expected: the file is a snapshot, and the chain is the record. https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/how-many-qrl-ots-keys-remain.md explains why the index cannot be rewound.

The transaction history is not in the file either. It arrives from the chain as the restored wallet syncs, which is why a freshly restored wallet can look empty for a while and still be correct.

## The forgotten password

There is no reset. The password derives the key that decrypts the file, and nothing else holds a copy of it: no server, no support desk, no recovery question. A file without its password is ciphertext.

That is the moment the mnemonic proves its worth. The phrase rebuilds the seed without needing the file or the password, which is why the backup that matters is the one on paper rather than the one on disk.

If you have neither the password nor the phrase, the file is not recoverable. Guessing is the only route left, and it is a route you take alone, offline, with no deadline that helps.

Length is the only lever at that point. A long passphrase built from unrelated words is the kind of thing a person can still recall after a year, which is why the password guidance matters as much as the phrase guidance when the wallet is created.

## What nobody can do for you

No recovery service exists for a self-custody wallet. An organisation that does not hold your seed has nothing to work from, whatever it charges or promises. Anyone offering to restore a wallet for a fee is either guessing at your password or taking your money.

No support channel needs your mnemonic, and any message asking for it is an attack. The phrase is the wallet: whoever reads it can spend the balance, and no legitimate process requires it to check a balance or unlock an account.

The usual approach asks for the phrase, or for a small payment to start the work, before anything is recovered. Both requests are the tell, and neither has a legitimate counterpart in a self-custody wallet.

https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/back-up-a-qrl-seed-phrase.md is the page that prevents this article being needed, and https://github.com/qrl-wallet/signatures-and-comparisons/blob/main/is-qrl-wallet-safe-to-use.md covers the habits around it.

If the wallet is not lost but simply not connecting, that is a different problem: https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/qrl-wallet-not-syncing-fix.md covers a wallet that opens but will not sync.

## FAQ

### Can anyone recover a wallet without the seed?

No. Without the mnemonic or the file plus its password there is nothing to restore from, and no third party holds a copy.

### I forgot the password but have the file. What now?

Use the mnemonic instead. It rebuilds the seed without the file or the password, and the restored wallet writes a new file with a new password.

### Is there a service that can unlock a wallet file?

No legitimate one. An organisation without your password or seed cannot decrypt the file, so any paid offer is a guess or a scam.

### Should I send my mnemonic to support?

Never. No support channel needs it, and anyone who asks for it can take the balance as soon as they have it.

### Can I recover a wallet from the address alone?

No. An address is public information and cannot sign. Recovery needs the seed behind it, which is either the mnemonic or the file plus its password.

<!-- answers: Q209, Q210, Q212 -->

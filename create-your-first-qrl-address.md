![QRL article banner](assets/banner-article.png)

# Create Your First QRL Address

**Short answer.** Creating an address takes one password and no account. The wallet writes a local file, derives an address beginning with Q, and shows you a mnemonic that you store offline before the address receives anything. Sync finishes first, you fund it with a small amount, and the address is ready for real use.

## Before you start

Install the current build and let it finish syncing before you create anything. The release page carries the assets for Windows, macOS and Linux; [Download the Official QRL Wallet](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/download-the-official-qrl-wallet.md) covers the download and the hash check that belongs with it.

Syncing is the slow part. The wallet is downloading and checking the chain, and an address created halfway through sync is not wrong, it is simply not usable until the wallet knows the current state of the network. If the progress bar sits at zero, the application is not reaching a node, and fixing that comes before creating an address.

Decide where the wallet file will live while you are still setting up. A folder inside your normal backup is the easy answer on a desktop, as long as that backup does not sync to a service you would not trust with the file.

## No account, no email

There is no sign-up. No address is registered, no email is collected and no password reset exists, because there is no server holding your account. The wallet is a program that manages a file, and the file is the wallet.

That changes what support can do for you later. Nobody can restore access by looking you up, because there is nothing to look up. The mnemonic is the only path back from a lost machine, which is why the backup step comes before funding rather than after.

It also means an address costs nothing to create. You can make a second wallet for a second purpose without asking anyone, and the two are separate files with separate phrases.

## The password and the file

The password encrypts the wallet file on disk. It is not sent anywhere and it is not checked against a service, so a wrong password produces a failed decrypt rather than a lockout. That is the first thing to understand about it: there is no account behind it, and no way to ask anyone to reset it.

The second is how the file gets attacked. Someone who copies the wallet file does not have to guess the password through the application, which would be slow. They can run a guessing tool against the file directly, as many times as their hardware allows. Length is what defeats that, far more than punctuation. Four or five unrelated words run together beat a short string with a symbol in it, and they are easier to type correctly.

Do not reuse a password from another site. Lists of passwords leaked elsewhere are the first thing a guessing tool tries, and a file protected by a leaked password is unprotected.

Keep the password somewhere a person cannot read it by looking at your desk: a password manager entry, a sealed note in a different room, a phrase you can recall. Store it apart from the wallet file and apart from the mnemonic. If all three sit together, one find is a full compromise, and the encryption has bought nothing.

The file name is not the wallet's identity. Copying it, renaming it or moving it between folders changes nothing, and the address inside stays the same. Deleting it deletes the only encrypted copy of your keys on that machine, which is why the copy in your backup matters.

If the wallet offers a password change, it re-encrypts the file in place. Copy the file somewhere safe before you do it, so a crash halfway through leaves you with a copy rather than a corrupted original.

What the password cannot do is replace the mnemonic. If you lose the file, the phrase restores the wallet on any machine. If you lose the phrase and keep the file plus its password, you still have a working wallet. If you keep the password alone, you have a word.

## Your first address

With sync complete, create the wallet. The application asks for a password, writes the file, and shows an address beginning with Q. That prefix is how you recognise a QRL address when you are checking a withdrawal form, and it is the same across desktop, Linux and macOS builds.

Behind the address are one-time signing keys derived from your seed through a Merkle tree of height 10, which gives 1,024 signatures per address rather than an unlimited number. [How Many QRL OTS Keys Remain?](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/how-many-qrl-ots-keys-remain.md) explains what that means in practice and how the wallet shows the remaining count.

Write the mnemonic down at this point, not later. The screen that shows it is the only time the wallet presents the whole phrase, and the backup is worth more than the address it protects.

## The mnemonic

The phrase is the wallet. Any build that accepts it will derive the same keys, and therefore the same address, on any machine. It is also the one thing an attacker needs, and there is no way to revoke it short of moving funds to a new wallet.

Store it offline before you fund anything: paper, two copies, two places. [Back Up a QRL Seed Phrase](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/back-up-a-qrl-seed-phrase.md) is the full method, including the restore test that proves your copy is readable while the wallet is still empty. [Restore QRL Wallet From a Mnemonic](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/restore-qrl-wallet-from-mnemonic.md) covers the other direction if you are bringing an existing wallet onto this machine.

Do not photograph the screen, do not paste the phrase into a note app, and do not send it to yourself in a message. Each of those creates a copy you no longer control.

## Fund it small first

Send a small amount before you send a large one. The point is not the money, it is the round trip: the address receives, the balance appears after the wallet syncs, and you have seen the whole path work with an amount you would not miss.

Choose the test amount by what a mistake would cost you, not by what looks tidy. An amount you would shrug at is the right size, because the step you are testing is the one where a wrong address or a wrong network turns up.

When you send it, copy the address from the wallet rather than typing it, and check the first and last few characters against the screen. A QRL address begins with Q, and a withdrawal form that produces an address without that prefix is not sending to a QRL address at all. If you are moving funds from an exchange, the withdrawal page is where that mistake happens, and the confirmation screen is the last place it can be caught.

Arrival is not instant in the sense the interface suggests. The transaction has to be included in a block, and the wallet has to be synced to that block before the balance changes. A wallet that is a few blocks behind will show the old balance for a while, which is not a failed send.

Receiving repeatedly at the same address is fine. Receiving does not consume the one-time keys; sending does, which is why the remaining-signature count only moves when you spend. A test spend from the wallet does consume one key, and that is expected rather than a problem.

If nothing appears after the wallet has caught up, check the address characters you sent to and the transaction on a block explorer before assuming the funds are gone. [Receive QRL in Your Wallet](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/receive-qrl-in-your-wallet.md) walks through the receiving side step by step.

Keep the wallet file, its password and the mnemonic in three separate places. That is the whole setup: one file, one password, one phrase, and an address beginning with Q.

## FAQ

### Do I need an account or an email address to create an address?

No. The wallet writes a local file and derives the address from it. Nothing is registered and no email is requested.

### How long should I wait before using a new address?

Until sync completes. An address can be created earlier, but it cannot show an accurate balance or sign against the current chain state.

### What happens after 1,024 signatures?

That address has no keys left to sign with. The wallet tracks the count, and [How Many QRL OTS Keys Remain?](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/how-many-qrl-ots-keys-remain.md) covers when to move funds to a fresh address.

### Can I create more than one wallet?

Yes. Each wallet is its own file with its own password and mnemonic, and they do not interfere with each other.

<!-- answers: Q080, Q159 -->

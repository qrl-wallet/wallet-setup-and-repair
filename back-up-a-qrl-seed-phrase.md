![QRL article banner](assets/banner-article.png)

# Back Up a QRL Seed Phrase

**Short answer.** Write the mnemonic on paper, keep it offline, keep a second copy in a different place, and treat any request for it as an attack. The phrase is the wallet: anyone who reads it can rebuild your keys and move the balance. No support channel, moderator or developer will ever ask you to type it into a form.

## What the mnemonic is

The mnemonic is a list of words that encodes the seed your wallet was built from. From that seed the wallet derives its keys, and from the keys come the addresses. Everything in the wallet descends from those words, which is why they are the backup and the wallet file is not.

It is also not a password. A password can be changed, guessed at slowly and reset by whoever runs the service. A phrase cannot be reset, because there is no service. Losing it means losing the ability to sign for those addresses, permanently and without appeal.

Because the phrase reconstructs the keys, it works in any interface that accepts the QRL mnemonic: another machine, a rebuilt install, a different operating system. That portability is the point of a backup and the reason it has to be guarded like the balance itself.

## Paper, not photographs

Write the words by hand, number them, and check each one as you copy it. Handwriting forces you to read the word rather than glance at it, which catches the near-identical pairs that a quick copy misses.

Do not photograph the screen. A photo lands in a camera roll that syncs to a cloud account, appears in a gallery thumbnail and may be indexed by whatever backup service the phone uses. The same problem applies to a screenshot on a desktop, which tends to end up in a folder that syncs.

If you want a second format, write the words a second time on a different sheet rather than printing or photographing the first. Two handwritten copies made independently catch a mistyped word that one copy would not.

Store the paper somewhere dry and physically secure, and remember that fire and water destroy paper faster than they destroy a metal plate. A stamped metal backup is a reasonable choice for a long-held balance, and a folded sheet in a drawer is a reasonable choice for a small one.

## Two copies, two places

One copy is a single point of failure. Two copies in the same building survive a mistyped word but not a fire, so the second copy belongs somewhere else: a trusted relative's house, a safe deposit box, a second property.

Both copies should be complete and readable without the other. A phrase split across two locations sounds safer and is usually worse, because a single lost half leaves you with nothing you can restore and no way to prove the other half was ever valid.

Keep a note of where each copy is, separate from the copies themselves. The note is not secret; its only job is to stop you forgetting that a third envelope exists in a drawer you no longer open.

Review the locations once a year. A move, a renovation or a change of address is exactly how a backup becomes a thing you remember having rather than a thing you can find.

## What not to store with it

Keep the phrase away from the password and away from the wallet file. If all three sit in one envelope, whoever opens the envelope has the wallet, and the encryption has bought you nothing.

Do not put it in a password manager as the primary copy. A manager is a good place for the password, and it is a copy of the phrase on a device that is online by design. Cloud notes, email drafts, chat messages to yourself and screenshots all have the same shape: a copy you no longer control.

Do not dictate it over a phone call or send it to anyone who says they are helping. No support channel asks for it, no moderator needs it to check a balance, and no giveaway requires it to send you anything. Anyone with the words can spend the balance, so a request for them is either an attack or a mistake.

[Is the QRL Wallet Safe to Use?](https://github.com/qrl-wallet/signatures-and-comparisons/blob/main/is-qrl-wallet-safe-to-use.md) covers the rest of the habits that surround the phrase, and [Recover a Lost QRL Wallet](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/recover-a-lost-qrl-wallet.md) explains why a phrase kept badly is the same as no phrase at all.

## Testing the backup

Test the backup before the wallet holds anything worth losing. Restore from the phrase on a second machine, or in a second profile on the same one, and confirm the same address appears. Then delete that test wallet.

Doing this while the balance is small turns a theory into a checked fact. [Restore QRL Wallet From a Mnemonic](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/restore-qrl-wallet-from-mnemonic.md) walks through the restore, and [Create Your First QRL Address](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/create-your-first-qrl-address.md) covers the address step if you are starting from nothing.

Repeat the test after any change: a new machine, a new copy, a word you rewrote because the ink ran. A backup you have never restored is a hope, and hope is a poor substitute for a verified copy.

Once the phrase is written, stored twice and tested, the wallet file and its password complete the set. [How Many QRL OTS Keys Remain?](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/how-many-qrl-ots-keys-remain.md) is the next thing to understand, because a backup restores keys rather than extending the number of signatures an address can make.

## FAQ

### Can I store the phrase in a password manager?

Not as the primary copy. A manager is a sensible home for the wallet password; the phrase belongs on paper, offline, in two places.

### Is a photograph of the phrase acceptable?

No. A photo lands in a syncing camera roll or gallery, which is an online copy you no longer control.

### How often should I check the backup?

Once a year is enough to confirm the paper is still where you left it and still readable. Restore from it again after moving house or changing machines.

### What do I do if someone asks for my phrase?

Refuse and stop the conversation. No support channel, moderator or developer needs the words, and anyone who asks can spend the balance once they have them.

<!-- answers: none -->

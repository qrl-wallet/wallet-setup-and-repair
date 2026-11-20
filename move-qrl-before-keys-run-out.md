![QRL article banner](assets/banner-article.png)

# Move QRL Before Keys Run Out

**Short answer.** Moving is a normal transfer. Create a fresh address in the same wallet, which restarts the count at 1,024, send the full balance to it while the old address still has a key to sign with, and refresh your backups afterwards. The old address then stays in the wallet as a record.

## When to move

The signal is the remaining count rather than a date. When the wallet reports that an address is down to its last few keys, that is the moment to plan the move.

A wallet used for years of small payments can reach this point sooner than the owner expects. The count falls with every spend and not with the size of the spend, so a hundred small transfers use a hundred keys just as surely as a hundred large ones.

Several is the right number to keep in reserve. One key has to be spent on the transfer itself, and leaving only that one means a single mistake, a rejected fee or a second attempt has no key left to try with, which turns a routine move into a stranded balance.

Moving early costs one fee and one key. Moving late can cost the balance, so the decision is not close.

## Creating the destination

Create a new address in the same wallet rather than a new wallet. A second address in the same file restarts the count at 1,024, derives its own tree, and stays under the same password and the same mnemonic.

That last point matters more than it looks. One wallet with two addresses is one backup to keep, and the mnemonic you already wrote down covers both. A second wallet file is a second backup to store and a second thing to lose.

The new address appears in the same list as the old one, and the wallet shows the remaining count for whichever address is selected, so telling them apart is a matter of reading the label rather than remembering a string.

https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/create-your-first-qrl-address.md covers the creation itself, including the moment the new address appears in the list.

## Order of operations

Do the work in this order and the move stays reversible in the sense that matters: nothing is deleted until the funds have landed.

First, sync fully. A move built on a balance you cannot see clearly might leave a remainder behind.

Second, copy the destination address from the wallet itself. Do not retype it, and do not read it from a message.

Third, send the balance to the new address, minus enough to cover the fee. The fee is charged in addition to the amount, so the total that leaves the old address is the payment plus the fee.

Fourth, wait for confirmation and confirm the new address shows the funds. Only then treat the old address as finished.

## What the move costs

One key and one fee. The key is the signature used to authorise the transfer, drawn from the old address, which is why the move has to happen before the count reaches zero.

The fee is the ordinary network charge for a transaction, shown before you confirm. There is no special charge for moving between your own addresses, and nothing about the destination being yours changes the fee.

If the amount is large, nothing about the move changes either: it is one transaction to one address, exactly like paying anyone else. https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/understanding-qrl-transaction-fees.md covers what that charge is for.

The fee is charged on top of the amount, not taken out of it. A transfer of the whole balance therefore has to leave room for the fee: what leaves your balance is the payment plus the fee, and the new address receives the payment. The confirmation screen shows both figures separately, and that is the moment to compare them.

## After the move

Refresh the backup. The wallet file now contains an address it did not have before, so the copy you took last month is missing it. Re-copy the file, and keep the password and the mnemonic where they were.

Keep the old address in the wallet. It is a record of what the address received and spent, and hiding it only makes the history harder to read later. It cannot sign again once its keys are exhausted, and it should not be given out.

If the interface allows a label, give the new address one that says it is the current one. A future restore will then show two addresses with a clear difference rather than two strings you have to tell apart from memory.

Check the remaining count on the new address once, so you know what you are starting with. Then continue as normal: https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/how-many-qrl-ots-keys-remain.md explains the count, and https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/what-is-tree-height-in-qrl.md explains why each address has the number it does.

Two things to avoid. Do not describe this as moving to a new coin or a new network: the funds stay on QRL and only the signing address changes. And do not send a partial balance and leave a remainder on the old address, because a remainder is a balance that later has no keys to move it.

https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/send-qrl-to-another-address.md covers the sending screen if you have not used it before.

## FAQ

### How many keys should be left before I move?

More than one. The move itself uses a key, and leaving a single key means a failed attempt has nothing left to fall back on.

### Does the new address have 1,024 keys again?

Yes. A new address derives a new tree, and the count restarts at 1,024.

### Do I need a new wallet file for the new address?

No. A second address in the same wallet is covered by the same file and the same mnemonic, though the file should be re-copied to your backup once the address exists.

### Can I keep using the old address to receive?

No. An address near the end of its keys cannot sign, so anything sent to it afterwards would be stranded. Give out the new address instead.

### Can I move only part of the balance?

You can, but a remainder left behind has fewer keys to move it later. Sending the whole balance in one transfer is the simpler choice, and it leaves nothing stranded.

<!-- answers: none -->

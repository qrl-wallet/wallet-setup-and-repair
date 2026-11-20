![QRL article banner](assets/banner-article.png)

# How Many QRL OTS Keys Remain?

**Short answer.** An address starts with 1,024 one-time signatures. The wallet shows how many are left, each spend uses the next one in order, and when the count reaches zero the address cannot sign at all. That is why the balance has to be moved while a key is still available.

## Where the count lives

A QRL address is a Merkle tree of one-time keys, and the tree is fixed when the address is created. The count is simply the number of leaves that have not been used yet.

The wallet keeps that index in its own local state. A desktop wallet carries it alongside the keys, which is one reason a wallet file matters beyond the keys themselves: restoring an old copy restores an old index.

An interface that reads the chain can also work the index out from the signatures already published, which is how a web wallet can pick up an existing address and show the right number. Both routes describe the same thing, and when they disagree it is the chain that is right. If a restored wallet shows a lower count than you remember, that is usually the chain doing its job: every signature ever published from the address has been counted, including the ones you made on another machine.

## Why each spend uses one

QRL signs with one-time keys because the signature scheme is hash-based. Each key is safe for exactly one signature: use it twice and the two signatures together reveal enough to forge with it, which is why the network rejects a repeat rather than accepting it and hoping.

The index moves when you sign, not when a block includes the transaction. A transaction that is signed and then never confirms has still used its key, because the signature exists the moment it is produced. Treat a signed transaction as spent in that sense even while its confirmation is in doubt.

That is also why two live copies of one wallet are dangerous. Both can reach for the same index, and the second spend fails or, worse, produces a signature the network will not accept. The wallet tracks the index for you, and the number in the interface is worth more than your own recollection of it.

## What "at zero" looks like

At zero the address has no leaves left, so it cannot produce another signature. The wallet will not build a transaction from it, and there is nothing to click that would fix it.

The balance does not disappear. It stays visible on the address, and on the explorer, and nobody else can spend it either. What is gone is the ability to authorise a transfer, so a balance left on an exhausted address is stranded: the coins are permanently unspendable.

This is the outcome the count exists to prevent, and it is unrecoverable. The wallet's warning is worth more than it looks. No update refills an address either: the tree was fixed when the address was created, so the only route forward is a new address and a transfer made while the old one can still sign.

## Moving funds in time

The move is an ordinary transaction, not a special procedure. Create a fresh address in the same wallet, which starts a new tree and a new count at 1,024, and send the balance to it.

Do it while several keys remain rather than at the last one. Each send uses a key, so a move made at exactly one remaining signature leaves no room for a fee adjustment or a second attempt.

The old address stays in the wallet after the move, so its history remains readable even though it cannot sign again. That is the useful part of keeping it: a record rather than a destination.

[Move QRL Before Keys Run Out](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/move-qrl-before-keys-run-out.md) walks through the order of operations, and [What Is Tree Height in QRL?](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/what-is-tree-height-in-qrl.md) explains why the tree is the size it is.

## Writing the index down

The documentation recommends noting the index after each use, and the habit pays off in one specific case: a restore from a backup. If the file is older than the last spend, the index it carries is older too.

Writing the number on paper beside your backup gives you something to compare against when a restore looks wrong. It also makes the count visible outside the interface, which is useful when the interface is the thing you are unsure about.

You do not have to do this for every payment. A note taken at the end of a session, or before moving a machine, captures the state that matters.

It is also the quickest way to spot a restore that has gone wrong. A wallet that opens showing a much higher count than you remember is presenting an older state of the tree, which is worth investigating before you sign anything with it.

## What the sender and receiver see

Nothing unusual. An address with three keys left looks exactly like an address with 1,020, and a payment into it arrives normally. Receiving does not consume keys; only spending does.

The count is your concern rather than the network's. Someone paying you has no way to know how close the address is to the end, which is why handing out an address that is nearly exhausted is a mistake: the next payment lands somewhere that cannot be spent from.

[Send QRL to Another Address](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/send-qrl-to-another-address.md) covers spending, [Recover a Lost QRL Wallet](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/recover-a-lost-qrl-wallet.md) covers what happens when a backup is the only thing you have, and [Why Stateful Signatures Matter in QRL](https://github.com/qrl-wallet/signatures-and-comparisons/blob/main/why-stateful-signatures-matter-in-qrl.md) explains why the order is not optional.

## FAQ

### Where do I see how many keys are left?

The wallet shows the remaining count for the selected address. An interface reading the chain can derive it from the signatures already published.

### Does receiving a payment use a key?

No. Only signing uses a key, so an address can receive indefinitely and still have its full count available.

### Why does the address start at 1,024?

Because the default tree height is 10, and a tree of that height has 1,024 leaves. A taller tree would give more, at a cost in setup.

### What happens if I reach zero with a balance still there?

The address can no longer sign, and the balance cannot be moved. The count has to be acted on before that point, not after it.

<!-- answers: Q168, Q169, Q183, Q214, Q218, Q219, Q223 -->

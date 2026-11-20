![QRL article banner](assets/banner-article.png)

# Send QRL to Another Address

**Short answer.** Sending is one confirmation. Paste an address beginning with Q, check the first and last few characters, confirm the fee, and approve. The signature you spend is gone for good, the transaction cannot be recalled once it is in a block, and there is no note field to attach to it.

## Before you send

The wallet has to be synced before it can build a sensible transaction. A wallet that is behind does not know the current balance or the current fee, and a payment built on old state is a payment you did not intend.

Have the destination address in a form you can copy rather than retype. Ask the recipient to send it as text, not as a photograph of a screen: a picture invites transcription errors, and an address has no checksum you can see with your eyes.

Decide the amount with the fee in mind. The fee is added to the total that leaves your balance, and it is shown on the confirmation screen, so you can see the real cost before you approve rather than after.

## Checking the address

Every QRL address begins with Q. That prefix is the one check you can make without any tools, and it is the check that catches a payment aimed at a different network entirely.

Then read the first and last few characters against the original. Addresses are long and generated, so the middle is where human attention fails; the ends are where a copied address from the wrong source tends to differ.

Copy and paste rather than typing. A single wrong character produces an address that is either invalid or belongs to someone else, and the wallet cannot tell you which. If the form will not accept the string, you have caught the mistake at the cheap stage.

Treat a changed address as an attack until proven otherwise. If a recipient sends an address, then sends a correction, confirm the correction through a channel that is not the one that delivered it.

## The fee

The fee appears before you confirm, separate from the amount. It is a network charge per transaction rather than a percentage, and the wallet takes no part of it.

Check the total, which is the amount plus the fee, against what you meant to spend. The screen is the place to notice that a payment is larger than intended, and it is the last place where noticing changes anything.

[Understanding QRL Transaction Fees](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/understanding-qrl-transaction-fees.md) explains what the fee pays for, and why a large transfer and a small one cost the same in fees.

## Confirming

Approve the transaction and it is signed on your machine and broadcast to a node. From that moment it is public, and anyone watching the network can see the amount and the destination.

Inclusion in a block is the point at which it becomes final in practice. Until then it is a pending transaction, and the wallet shows it that way. Waiting is normal: blocks take time, and a payment that appears stuck is usually just early.

Once included, there is no undo. Nobody can reverse a QRL transaction, no support channel can cancel one, and asking for a refund is a request to the recipient rather than an action on the network.

## What the one-time key means for you

Each address can sign 1,024 times, because QRL addresses are built from a Merkle tree of one-time keys. Every spend uses one of them, in order, and the count moves forward when you sign rather than when the transaction confirms.

That has two consequences worth holding on to. The first is that a signed transaction consumes a key even if it never confirms, which is why reusing an address after a failed attempt needs care. The second is that the count is finite: [How Many QRL OTS Keys Remain?](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/how-many-qrl-ots-keys-remain.md) covers what to do as it runs down.

Running two copies of the same wallet is the failure this model punishes. Two copies can draw the same key for two different transactions, and a key that has signed twice is rejected, so one of the two spends fails. Move between machines by restoring, and stop using the old copy.

## Limits per transaction

The send form takes one recipient, one amount and a fee. There is no memo field, so a payment made here is an address and a value, and any reference number or invoice note has to travel through a separate channel. Do not put a note in the amount or split a payment to encode one.

Paying several people therefore means several sends, each with its own fee and its own one-time key. Nothing in the form groups them into one action.

The limit that does accumulate is the signature count. Each address can sign 1,024 times, so an address that has sent a thousand payments is near the end of its life even though its balance may be unchanged. That is a limit on how often you can spend from an address rather than on how much you can hold. [Create Your First QRL Address](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/create-your-first-qrl-address.md) covers creating the destination if you are moving funds between your own addresses, and [QRL Pending Transaction Stuck](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/qrl-pending-transaction-stuck.md) covers a payment that has not confirmed. [Receive QRL in Your Wallet](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/receive-qrl-in-your-wallet.md) is the other side of the same flow.

## FAQ

### Can I cancel a transaction after sending?

No. Once it is signed and broadcast it cannot be withdrawn, and once it is in a block it cannot be reversed by anyone.

### Is there a memo field for a reference number?

No. A QRL payment carries an amount and a destination only, so any reference has to be sent separately.

### What happens if I send to an address on another network?

The prefix check is your guard. A QRL address begins with Q, and a string that does not is not a QRL address to send to.

### Does sending cost one of my 1,024 signatures?

Yes. Each spend uses one one-time key, and the count decreases when you sign, whether or not the transaction confirms.

<!-- answers: Q213 -->

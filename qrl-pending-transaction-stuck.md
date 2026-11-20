![QRL article banner](assets/banner-article.png)

# QRL Pending Transaction Stuck

**Short answer.** A pending transaction has not been included in a block yet. It is usually waiting on a node that has not seen it propagate, or on a fee the network will not take into a block. Check the explorer first, then your node and sync state. Until you know the outcome, do not sign another transaction from the same address with the same key index.

## Pending versus failed

Pending and failed look similar in a wallet and mean different things. Pending means the transaction exists and is waiting. Failed means the network considered it and would not accept it, or the wallet could not build it in the first place.

A pending transaction has not moved anything yet. The balance change is not final until a block includes it, and a payment that sits for an hour has not been lost in that hour.

A transaction that is never included in a block is not charged a fee, because there is no block to charge it in. What it does cost is a key: the signature was made when the transaction was built, and a key that has signed cannot safely sign again.

That asymmetry explains most of the confusion around a stuck payment. The money is safe and the key is spent, which is the opposite of what people assume.

Interfaces do not always help. A pending transaction is sometimes shown with the same styling as a completed one, with a small grey label as the only difference, which is why the explorer is worth the extra click before you react.

## What the explorer shows

The explorer is the reference. Look the transaction up there rather than trusting the wallet's view, because the wallet only knows what its node has told it.

If the explorer shows the transaction with no block, it is pending and the network has at least seen it. If the explorer has nothing at all, the transaction may never have reached a node, and the wallet is showing a local record of something the network does not know about.

The explorer also shows the fee and the addresses involved, which is how you confirm that the transaction is the one you meant to send rather than a duplicate or an earlier attempt.

If the explorer shows the transaction in a block, the payment is finished and the wallet is simply behind. Syncing will bring the balance into line, and nothing needs rebroadcasting.

## Node and sync causes

A wallet that is behind does not know the current state, and a transaction built on old state can be rejected or can sit unused. Syncing fully is the first thing to check, and [QRL Wallet Not Syncing Fix](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/qrl-wallet-not-syncing-fix.md) covers a wallet that will not catch up.

A node that is unreachable produces the other version of the same story: the wallet holds a signed transaction it could not broadcast. [Fix QRL Wallet Connection Error](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/fix-qrl-wallet-connection-error.md) covers that case, including the node setting and the firewall.

A fee below what the network will accept leaves the transaction waiting indefinitely, since nodes are free to ignore anything under their floor. The confirmation screen is where the fee was shown, and it is worth comparing with what you approved.

A node that is running but not fully synced is a subtler version of the same problem. It accepts the transaction, never relays it onward, and the wallet reports it as sent while the rest of the network has never heard of it. Checking which node the wallet is pointed at is part of reading the situation accurately.

## Rebroadcasting

If the transaction is signed and valid but the network never saw it, sending the same signed transaction again is the safe move. The signature exists already; rebroadcasting it does not create a second signature or use a second key.

That is different from building a new transaction for the same payment. A new build draws a fresh key, and if the first transaction later confirms you have paid twice from an address that has now signed twice.

So: rebroadcast the existing bytes, do not re-sign. If the interface offers no way to rebroadcast, wait for the node to catch up rather than creating a replacement.

Waiting is often the right answer regardless. Most pending transactions confirm once their node catches up, and impatience is what produces duplicate payments and wasted keys.

## Why you should not double-spend the same address

QRL keys sign once. A second signature with the same key is rejected by the network, so an attempt to replace a pending transaction with another one from the same key index does not behave like a fee bump on other chains: it produces a conflict rather than a replacement.

The practical rule is to wait for a definite answer before touching the address again. Either the transaction confirms and the key is legitimately spent, or it never reaches a block and the key is spent anyway, because the signature was already made.

If you must move funds urgently, do it from a different address in the same wallet, which has its own keys and its own index. [Send QRL to Another Address](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/send-qrl-to-another-address.md) covers sending, [How Many QRL OTS Keys Remain?](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/how-many-qrl-ots-keys-remain.md) explains why the index matters here, and [Understanding QRL Transaction Fees](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/understanding-qrl-transaction-fees.md) covers the fee the network will accept.

The explorer settles the question either way. Once the original transaction appears in a block, the address is in a known state and you can plan the next step from facts rather than from an empty screen in the wallet.

## FAQ

### How long can a transaction stay pending?

There is no fixed limit. It stays pending until a block includes it, and a fee below the network floor can leave it waiting indefinitely.

### Is my money gone while the transaction is pending?

No. Nothing has moved until a block includes the transaction, so the balance is unchanged until then.

### Can I cancel a pending transaction?

No. There is no cancel, and signing another transaction with the same key index does not replace the first one.

### Should I resend the payment with a higher fee?

Not by signing again from the same address. Rebroadcast the signed transaction, or send from a different address with its own keys.

### Am I charged the fee twice if I rebroadcast?

No. Rebroadcasting sends the same signed transaction, and the fee is paid once, when a block includes it.

<!-- answers: none -->

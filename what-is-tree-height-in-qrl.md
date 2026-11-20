![QRL article banner](assets/banner-article.png)

# What Is Tree Height in QRL?

**Short answer.** Tree height sets how many one-time signatures an address can make. Height 10 gives 1,024 signatures, because the tree has that many leaves. A larger tree would move the limit rather than remove it, and it would cost memory and setup time to do so.

## The Merkle tree in one paragraph

A QRL address is not a single public key. It is the root of a Merkle tree whose leaves are one-time signing keys, each generated in advance from your seed. The root is what the network sees as your address; the leaves are what you spend, one per transaction, in order.

When you send, the wallet reveals one leaf's public key along with the short path of hashes that connects it to the root. A verifier can check that path and be satisfied the key belongs to the address. Nothing else about the tree is revealed, and the other leaves stay secret.

That structure is what makes the scheme hash-based, and it is also why the number of leaves matters. The tree is fixed when the address is created, so the count of signatures is fixed at the same moment.

The path is also the reason a spend carries more than a signature. Its length grows with the height of the tree, so a taller tree makes every transaction slightly heavier for the network to check. That cost is small, but it is paid on every send rather than once at setup.

## Height to signature count

The height is the number of levels in the tree, and the leaf count doubles with each level. Height 10 gives 1,024 leaves and therefore 1,024 signatures.

Height 11 would give 2,048, height 12 would give 4,096, and so on. The relationship is exact and easy to state, which is why the question usually arrives as "why not simply choose a bigger number".

Each spend uses the next leaf in sequence. The sequence is not a queue the network enforces; it is a rule the wallet follows, because reusing a leaf would reveal two signatures under one key, which is exactly the situation the scheme cannot tolerate.

## Why the default is 10

The default is a balance between capacity and cost. A thousand signatures is far more than most addresses ever use, and the tree is small enough to generate quickly and to keep track of without effort.

It is also a number the interface can show honestly. A count that starts at 1,024 is a count a person can watch go down and act on; a count that starts at a million invites the assumption that it will never matter.

The choice belongs to the address, not to the wallet session. Creating a new address creates a new tree and restarts the count.

## What happens at the limit

When the leaves are exhausted, the address cannot sign again. The coins stay visible on the chain, but nothing can authorise a spend from them: a balance left on an exhausted address is permanently unspendable.

That is why the move has to happen before the last key is used. Create a fresh address in good time, which restarts the count at 1,024, and send the balance across while the old address still has a signature left. That is an ordinary transaction, with an ordinary fee, and it is the same operation as paying anyone else.

Do not hand out an address that is close to its limit as a destination for new funds, and do not wait for a warning before acting on the count. The wallet shows the number falling, and the decision belongs to you while a key is still available.

The wallet tracks the index as you go, which is why it can warn you before the end rather than after it. https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/how-many-qrl-ots-keys-remain.md covers reading that number, and https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/move-qrl-before-keys-run-out.md covers the move itself.

## Why "just use a huge tree" is not free

A taller tree costs memory and setup. Every leaf has to be generated from the seed before the address can sign, so a tree with a million leaves takes proportionally longer to build and more space to hold. On a wallet that runs on a laptop, that is a visible delay at creation and a larger amount of state to store.

It also costs verification work on the other side. The proof that a leaf belongs to the root grows with the height, so every transaction carries a slightly larger proof for the network to check.

And it does not change the nature of the limit. A tree of any height ends, and an address that has spent its last leaf is in the same position as one with a smaller tree. A bigger tree buys time between moves, not immunity from them.

What a taller tree would change is the consequence of losing track of the index. A wallet that has fallen behind on a large tree has more state to reconstruct, which makes a sloppy backup more expensive rather than less.

None of this makes the default a safety feature, and a larger height is not an upgrade to security. The security comes from the hash-based signatures; the height only decides how many of them exist. https://github.com/qrl-wallet/signatures-and-comparisons/blob/main/why-qrl-uses-a-merkle-tree.md explains the structure, https://github.com/qrl-wallet/signatures-and-comparisons/blob/main/why-stateful-signatures-matter-in-qrl.md explains why the order matters, and https://github.com/qrl-wallet/signatures-and-comparisons/blob/main/how-qrl-xmss-signatures-work.md covers the signing itself.

## FAQ

### How many signatures does height 10 give?

1,024, one per leaf in the tree. The count is fixed when the address is created.

### Does a bigger tree make a wallet safer?

No. It changes how many signatures are available, not how strong each one is.

### What happens when the signatures run out?

The address can no longer sign, and a balance left on it cannot be moved. That is why the count is watched and the funds are moved before the last key is used.

### Is the tree height something I choose?

It is set when the wallet is created, and the default gives 1,024 signatures. It is not changed for an address that already exists.

<!-- answers: Q184, Q220 -->

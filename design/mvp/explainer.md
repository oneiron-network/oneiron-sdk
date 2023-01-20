
# What is Oneiron SDK

Oneiron SDK enables developers to quickly create their own Cardano sidechains.

A sidechain is a L2 (Layer 2) blockchain that builds on security of a L1 (Layer 1) blockchain, in our case -- Cardano.

Sidechains can be very different in:
- accounting / transaction model they use,
- how they interact with the L1 blockchain,
- smart contract support,
- consensus protocols,
- etc.

We are not trying to cover all possible cases. Instead, we are focusing on enabling developers already familiar with mainstream enterprise/web technologies to get started quickly with their apps and their own sidechains (if needed).

Oneiron sidechains use JVM technology to run smart contracts. More specifically, [GraalVM](https://www.graalvm.org), which powers our smart contract runtime environment for a variety of languages: Java, Scala, Kotlin, Clojure, Python, Ruby, JavaScript.

Oneiron sidechains are designed to be compatible with Cardano, by using the same Extended UTXO accounting model and the same address and transaction format.

Interoperability with Cardano is 2-way: assets can be transferred from Cardano (L1) to a sidechain (L2) and back. Even transferred to the sidechain, assets continue to be fully controlled by their owner. In Oneiron sidechains, the user's sidechain address is the same as their Cardano address. Existing Cardano wallets (at least, some of them) will be compatible with Oneiron sidechains.

## Sidechain Gate Scripts

To provide the "entry point" for Oneiron sidechains, a _gate script_ is used. Each Oneiron sidechain has its own unique gate script, created as a reference script at the time of sidechain creation.

When a user wants to make some assets available on the sidechain, they send these assets to their personal _gate script address_, which is a Shelley address of Type 1 and has two parts:
- the payment part is the **gate script hash**,
- delegation part is the **user's stake key hash** (to ensure that funds sent to the sidechain continue being staked for the benefit of the user).

Outputs sent to the gate script **must** also have the **user's payment key hash** in the _datum_. This is needed for the user to **control their assets** at the gate script address, enabling them to:

- put assets into the sidechain (while **logically** still remaining in their custody),
- receive assets via the sidechain,
- take settled assets out of the sidechain **at any time** (more on this below).

As soon as outputs are available at a sidechain gate script address, assets from these outputs can be transacted on the sidechain.

Transactions on Cardano L1 putting tokens to the gate script address translate to transactions on L2 minting these tokens and putting them into the user's wallet address on L2. Symmetrically, transactions on L1 removing tokens from the gate script address translate to transactions on L2 removing these tokens from the user's wallet on L2 and burning them. **Only the owner** of an output (as per the payment key hash in the datum) can move it from the gate script address.

Oneiron sidechains use [optimistic concurrency control](https://en.wikipedia.org/wiki/Optimistic_concurrency_control): the **user can withdraw** their assets from the gate script address **on Cardano (L1) at any time**, thereby canceling any unsettled transactions on the sidechain involving these assets.

The only L1 transactions, sidechain nodes can make, are _summary transactions_ (a.k.a. _settlement transactions_). These transactions transfer assets on L1 **within the same sidechain** _gate script address_ space.

## Sidechain Transaction Settlement: Summary Transactions

See [Summary Transactions](./summary-transactions.md).

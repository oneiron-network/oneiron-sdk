
# What is Oneiron SDK

Oneiron SDK enables developers to quickly create their own Cardano sidechains.

A sidechain is a L2 (Layer 2) blockchain that builds on security of a L1 (Layer 1) blockchain, in our case -- Cardano.

Sidechains can be very different:
- what accounting / transaction model they use,
- how they interact with the L1 blockchain,
- smart contract support,
- etc.

Oneiron sidechains use JVM technology to run smart contracts. More specifically, [GraalVM](https://www.graalvm.org), which powers our smart contract runtime environment for a variety of languages: Java, Scala, Kotlin, Clojure, Python, Ruby, JavaScript.

Oneiron sidechains are designed to be compatible with Cardano, by using the same Extended UTXO accounting model and the same address and transaction format.

Interoperability with Cardano is 2-way: assets can be transferred from Cardano (L1) to a sidechain (L2) and back.

## Sidechain Gate Scripts

For this purpose, a _gate script_ is used. Each Oneiron sidechain has its own unique gate script, created as a reference script at the time of sidechain creation.

When a user wants to make some assets available for transactions on the sidechain, they send the assets to their personal _gate script address_, which is a Shelley address of Type 1 and has two parts:
- the payment part is the gate script hash,
- delegation part is the user's wallet stake key hash.

Outputs sent to the gate script must also have the user's payment key hash in the datum. This is needed for the user to control the assets at the gate script:
- put assets into the sidechain,
- receive assets via the sidechain,
- take settled assets out of the sidechain at any time (more on this later).

Oneiron sidechains use [optimistic concurrency control](https://en.wikipedia.org/wiki/Optimistic_concurrency_control): the user can take their assets out at any time, thereby canceling any unsettled transactions on the sidechain involving these assets.

As soon as the outputs are available to the sidechain gate script, assets from these outputs can be transacted on the sidechain.

A transaction on L1 putting tokens to the gate address translates to a transaction on L2 minting these tokens and putting them into the user's wallet address on L2 (consisting of the user's payment key and stake key hashes -- same as on Cardano L1).

## Sidechain Transaction Settlement: Summary Transactions

See [Summary Transactions](./summary-transactions.md).

## Open Questions

### Rewarding Node Operators

TODO

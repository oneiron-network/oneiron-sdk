
# Oneiron SDK Use Cases

## Initial (MVP)

This section describes a set of use cases for the MVP phase of the Oneiron SDK development.

The end result is:
- A developer can use a CLI tool to create and register a sidechain on Cardano.
- A developer can run the created sidechain using a ready to use Oneiron node software (as a single node sidechain).
- A developer can build and deploy dapps on their own sidechain.

### Create a sidechain

A sidechain is defined by a set of properties, like its reward and fee token, transaction fees, reward distribution, epoch duration, permissionless or authorized nodes, etc.

Useful defaults should be provided for all of these, allowing to configure specific ones.

With a CLI tool (and/or a library, depending on a context) provided by Oneiron SDK, developers will easily create and maintain Cardano sidechains to build and deploy their applications.

### Run a sidechain

To be able to build applications, there needs to be an easy to use runtime environment. For dapps, it is a smart contract capable blockchain.

With node software provided by Oneiron SDK, developers will be able to run a single-node (for the MVP) sidechain on Cardano testnet or mainnet.

### Build applications

Most enterprise/web software developers (at the time of writing) are largely unfamiliar with Haskell (the programming language of the Cardano blockchain), and pretty well versed in JVM-based languages as well as Python and JavaScript.

With the framework and libraries provided by Oneiron SDK, developers will be able to easily code and test smart contracts in JVM-based languages (Java, Scala, Kotlin, Clojure, etc), as well as JavaScript. Support for more languages (Python and Ruby) may be added post-MVP.

## Post-MVP

This section describes use cases for production use of sidechains and applications built on top of them. This entails multi-node sidechains.

The end result is:
- A node operator can run the Oneiron node software and join an existing Oneiron Cardano sidechain.
- Sidechain protocol update can be performed similar to how hard-fork combinator works in Cardano.
- Apps built using the MVP version of Oneiron SDK should run with no changes on Post-MVP multi-node Oneiron Cardano sidechains.

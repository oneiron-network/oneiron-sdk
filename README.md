
# Oneiron: Cardano Sidechain Development Kit

## Vision

We’re building Oneiron SDK — open-source JVM-based [Cardano](https://cardano.org) Sidechain Development Kit. Our goal is to
enable developers, already familiar with enterprise/web technologies, to create
Cardano [sidechains](https://eprint.iacr.org/2018/1239.pdf) and applications quickly and easily.

“Oneiron” (Ancient Greek) — “Dream”. Our dream is to bring millions of developers to Cardano.

With Oneiron SDK, _anyone_ will be able to create a sidechain node with a simple CLI command. Oneiron-built node will be
able to join an existing sidechain (built with Oneiron SDK) or to create an entirely new Cardano sidechain.

We’re also aiming to create **Oneiron Network** — a Cardano sidechain built with our SDK, enabling developers to start
building apps _immediately_ (without necessarily running their own nodes), with a variety of programming languages.

The language runtime choice is designed to primarily target the massive enterprise/web developer audience.

The Oneiron smart-contract runtime will be [JVM-based](https://www.graalvm.org), so it will support languages like Java,
Kotlin, Scala, Clojure, etc., as well as JavaScript, Python, Ruby. We also aim to include support
for [Wasm](https://webassembly.org) and [PlutusCore](https://docs.cardano.org/plutus/learn-about-plutus) in the future.

Oneiron Network will use the Cardano [eUTXO](https://docs.cardano.org/plutus/eutxo-explainer) accounting model
and [Ouroboros](https://docs.cardano.org/core-concepts/ouroboros-overview) consensus protocol.

In the future, we also aim to include support for [IBC Protocol](https://ibcprotocol.org) to enable interoperability
with the [Cosmos Network](https://cosmos.network) and blockchains in the Cosmos ecosystem.

## Current Scope

The scope of the current phase is to build the first approximation of our sidechain SDK, capable of creating 
_single-node_ Cardano sidechains. Users will still be able to:

- easily install the SDK,
- create their own (single-node, but still real) Cardano sidechain, capable of running smart-contracts on a JVM-based
  language runtime,
- begin development in the language of their choice and run their apps on the sidechain.

Creating and/or joining multi-node sidechains will be a subject of a future development phase.

## Design

See [Design](./design).

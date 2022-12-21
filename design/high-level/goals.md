
# Oneiron SDK High-Level Goals

Lower entry barriers for developers: Oneiron SDK aims to enable developers familiar with enterprise/web software technologies to create Cardano sidechains and applications quickly and easily. To that end, the goals are:

1. Provide a framework for development and execution of smart contracts in JVM-based languages. 
2. Provide node software for Oneiron sidechains.
3. Provide a CLI tool (and a library) for easy deployment of Oneiron sidechains. 

Interoperability: Oneiron sidechains will strive to be as interoperable with the Cardano blockchain as possible. To that end, the goals are:
1. Valid wallet addresses on Cardano should be valid wallet addresses in Oneiron sidechains.
2. eUTxO accounting model (the same as on Cardano) should be used in Oneiron sidechains.
3. API compatibility, so that existing Cardano wallets would be usable with Oneiron sidechains. 

Remove friction for end-users as much as possible. To that end:
1. Enable easy movement of user assets to and from Oneiron sidechains (and between Oneiron sidechains).
2. Make sure that users can always withdraw their assets from an Oneiron sidechain.  

## Future Goals (Post-MVP)

Scalability: Oneiron sidechains should enable creation of end-user applications that could handle millions of users.

## Non-Goals

1. Don't attempt to enable creation of all kinds of Cardano sidechains and applications. Oneiron SDK is an opinionated framework enabling the above goals.

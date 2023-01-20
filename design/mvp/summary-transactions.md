
# Summary Transactions

A sidechain node accepts transactions from users and validates them.

If an incoming transaction is consistent with validation rules and the current state of the sidechain, it contributes to a summary transaction being built by the sidechain node.

_Connected_ (or _dependent_) transactions happening on the sidechain incrementally contribute to (or build) a summary transaction, which is eventually posted on Cardano L1 to certify the results of the interaction.

> Note: Dependent transactions are, of course, connected via UTXOs: a spending transaction refers to outputs of previous transactions.

Summary transactions are built until they reach Cardano max tx size or within a time interval of the sidechain "epoch".

For efficiency, summary transactions can be bundled together, up to the max tx size on Cardano, when being submitted to L1.

## Summary Transaction Validation

### Proof

zk-SNARK proofs are produced for summary transactions by sidechain nodes. This is computationally intensive process, so verified valid proofs (i.e. successfully submitted and verified by the gate script on L1) are rewarded with the sidechain utility token.

### Verification

Any participant may submit summary transactions, and they may be batched (up to tx size limit).

A zk-SNARK proof of validity is submitted for each summary transaction (as a redeemer) along with the summary transactions. 

A summary transaction is valid if its inputs are unspent on the L1 and its hash is verified by the provided SNARK proof.

### zk-SNARK Algorithm Used

This is currently the subject of focus of the project founder. Considered candidates are:

- PLONK
- Marlin
- Groth16

The most important requirement is feasibility of implementation in Plutus, which implies the proof size must be small, and verification must be very fast.

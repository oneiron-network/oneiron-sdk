
# Summary Transactions

A sidechain node accepts transactions from users and validates them.

If an incoming transaction is consistent with validation rules and the current state of the sidechain, it contributes to a summary transaction being built by the sidechain node.

_Connected_ (or _dependent_) transactions happening on the sidechain incrementally contribute to (or build) a summary transaction, which is eventually posted on Cardano L1 to certify the results of the interaction.

> Note: Dependent transactions are, of course, connected via UTXOs: a spending transaction refers to outputs of previous transactions.

The summary transaction is built until it reaches Cardano max tx size or certain time duration elapses.

Summary transactions can be bundled together up to the max tx size on Cardano.

## Summary Transaction Validation

### Certification Phase

Summary transaction hash set is published by a sidechain node on L1, as a datum in an output locking the sidechain nodes' stakes until all summary transactions in the set are posted to L1 or canceled (by users withdrawing their assets from the gate script).

This certification tx is built off-chain by running a consensus among the sidechain nodes, each of them contributing their data to the tx: inputs and locked output, as well as signature.

Only one such certified summary tx set is possible per sidechain "epoch".

If a node wants to replace the summary tx set, it needs to lock equal or larger stake, making it too expensive for a malicious node to succeed (as it will have to lock more than all honest participants).

### Commit Phase

Any participant may submit summary transactions, and they may be batched (up to tx size limit).
A summary transaction is valid if its inputs are unspent and its hash is included in the summary tx hash set posted by the certification tx.

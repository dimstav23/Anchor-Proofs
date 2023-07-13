# Remote Attestation Analysis

The analysis in `anchor_attestation.spthy` relies on some properties proven by `tls.spthy`. In particular, it relies on the fact that the TLS handshake establishes an authentic session between to agents, that includes a secret symmetric key which can be used for further communication.

## Assumptions

- All the assumptions of the symbolic model
- The Intel attestation service only approves genuine quotation engines running on genuine hardware.
- The client has a way to securely verify the report of the quotation engine using Intel's attestation service

## Process

- The attestation process is modeled according to Figure 3 of the Anchor's revised SIGMOD paper version.
- This model is checked for correctness through a number of control lemmas that guarantee that certain valid states are reachable.
- The model is used to prove the desired security properties. In this case, an application attestation lemma that holds if: Once a client trusts an Anchor app, this Anchor app is in a valid, expected state.

## Results

- Tamarin was able to verify the lemmas mentioned above, by finding at least one valid trace (series of state transitions) for the required states and by showing that there is no trace for the invalid states.

- In this way, Tamarin found at least one trace for all control lemmas and has proven that there is no trace leading to any state in which the Anchor app attestation lemma would be violated.

- Thus, the Anchor app attestation lemma holds for our model. The proof artifacts can be found in the `proofs` folder. 

- It is recommended to also verify the results by running `tamarin-prover interactive .`, where you can interactively evaluate the results.

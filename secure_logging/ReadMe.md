# Secure Logging Analysis

This proof uses the timestamp of action facts to model counter values. It fits our use case as the counters are strictly increasing and the 
only requirement is that they are comparable, which holds.

## Assumptions

- All the assumptions of the symbolic model
- Counters are strictly, deterministically increasing as well as unique

## Process

- The secure logging protocol is modeled according to Figure 2 of the Anchor's revised SIGMOD paper version.

- This model is checked for correctness through a number of control lemmas that guarantee that certain valid states are reachable.

- The model is used to prove the desired security properties. In particular, we prove the following two lemmas:
    1. At the moment that the log is successfully verified, there is no modification that was stabilized before the last counter set stabilization (HW counter increase), but is no longer in the log, i.e., no entries are missing.
    2. At the moment that the log is successfully verified, it holds that up to the last counter set stabilization (HW counter increase), all entries are valid and from a genuine source, i.e., no entries are invalid. 

## Outcome

- Tamarin was able to verify the lemmas mentioned above, by finding at least one valid trace (series of state transitions) for the required states and by showing that there is no trace for the invalid states.

- In this way, Tamarin found at least one trace for all control lemmas and has proven that there is no trace leading to any state in which the secure logging protocol lemmas would be violated.

- Thus, the Anchor's secure logging lemmas hold for our model. The proof artifacts can be found in the `proofs` folder. These were generated on a AMD EPYC 7713P 64-Core Processor with 500 GB of RAM.

- It is recommended to also verify the results by running `tamarin-prover interactive .`, where you can interactively evaluate the results.

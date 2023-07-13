# Anchor: Formal Verification of Security Protocols

This repository contains the models that were used to formally prove:
1. Anchor's remote attestation protocol and
2. Anchor's secure logging protocol

To achieve this, we use the [Tamarin prover](https://tamarin-prover.github.io/).

The repository consists of the following 2 folders:
- [`remote_attestation`](./remote_attestation/) : contains the model and the proofs of the remote attestation protocol
- [`secure_logging`](./secure_logging/) : contains the model and the proofs of the secure logging protocol
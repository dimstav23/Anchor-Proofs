
default: all

all: proofs/tls_analyzed.spthy proofs/anchor_attestation_analyzed.spthy

proofs/tls_analyzed.spthy: tls.spthy 
	tamarin-prover --prove tls.spthy -O=proofs > proofs/tls_summary.txt

proofs/anchor_attestation_analyzed.spthy: anchor_attestation.spthy
	tamarin-prover --prove anchor_attestation.spthy -O=proofs > proofs/anchor_attestation_summary.txt

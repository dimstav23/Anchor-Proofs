
default: all

all: proofs/secure_log_analyzed.spthy

proofs/secure_log_analyzed.spthy: secure_log.spthy
	tamarin-prover --prove secure_log.spthy -O=proofs > proofs/secure_log_summary.txt

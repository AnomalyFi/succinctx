# Final stage
FROM --platform=x86_64 ubuntu:20.04

# Install only necessary packages
RUN apt-get update -qq -y \
    && apt-get upgrade -qq -y --no-install-recommends \
    && apt-get install -qq -y --no-install-recommends \
    bash ca-certificates curl gnupg2 \
    pkg-config libssl1.1 libssl-dev build-essential \
    libgmp-dev libsodium-dev nasm libc++1 gcc gfortran \
    && apt-get clean \
    && rm -rf /var/lib/apt/* /var/cache/apt/archives/

# Run the local prover
CMD RUST_LOG=info PROVER=local ./build/$PROVE_FILE prove $INPUT_FILE && mv output.json /proofs/output.json && mv proof_raw.bin /proofs/proof.bin && mv public_witness.bin /proofs/public_witness.bin && mv proof_plonk.bin /proofs/proof_plonk.bin

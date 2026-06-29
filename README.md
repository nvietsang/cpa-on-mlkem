# Simulated CPA attack on ML-KEM

This repository contains code for simulating CPA attacks on the reference implementation of ML-KEM. Power traces are simulated by hooking elementary operations such as multiplication (`*`) and addition (`+`), then recording the Hamming weight of the operands and results.

## Attack point

The attack point is the multiplication between the secret key and the ciphertext during decapsulation.

## Trace collection

    python3 tracing.py --n-traces 50 --path-to-data data

## Key recovery

Run the notebook `recover.ipynb`.

## Open problem (TODO)

When using the output of the `base_case_multiply` function as the intermediate value, the recovery algorithm must guess 2 coefficients at a time, resulting in $3329^2$ possibilities. This approach is impractical on a classical computer.

To reduce the complexity, we instead target the multiplication operation `a_0 * b_0` within the `base_case_multiply` function. In this case, only a single coefficient needs to be guessed. However, this introduces a new issue: multiple key guesses produce the same correlation with the power traces. As a result, an additional post-processing step is required to resolve these ambiguities.

## References

`fips203.py` is from [https://github.com/mjosaarinen/py-acvp-pqc](https://github.com/mjosaarinen/py-acvp-pqc)
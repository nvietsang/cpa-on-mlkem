# Simulated CPA attack on ML-KEM

This repository contains code for simulating CPA attacks on the reference implementation of ML-KEM. Power traces are simulated by hooking elementary operations such as multiplication (`*`) and addition (`+`), then recording the Hamming weight of the operands and results.

## Attack point

The attack point is the multiplication between the secret key and the ciphertext during decapsulation.

## Trace collection

    python3 tracing.py --n-traces 50 --path-to-data data

## Key recovery

Run the notebook `recover.ipynb`.

## References

`fips203.py` is from [https://github.com/mjosaarinen/py-acvp-pqc](https://github.com/mjosaarinen/py-acvp-pqc)
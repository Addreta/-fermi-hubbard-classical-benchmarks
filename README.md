# 1D Fermi-Hubbard: Classical Simulation Benchmarks
## Trotter | MPS-TDVP | Pauli Path

Classical simulation pipeline benchmarking three methods for  
the 1D Fermi-Hubbard Neel dynamics.

## Motivation
- Chowdhury et al. (Applied Physics Reviews, 2026): quantum 
  simulation of 1D FHM on IBM hardware using Trotterization, 
  benchmarked with MPS-TDVP
- Lin, Gharibyan & Su (2024): Pauli path simulation for 
  utility-scale quantum state preparation
- This work applies Pauli path to *time evolution* benchmarking 
  of the FHM, connecting both approaches

## Methods
1. Exact diagonalization (QuSpin) — ground truth
2. 1st and 2nd order Trotterization (Qiskit)
3. MPS-TDVP (TeNPy) — bond dimension χ=1 to 32
4. Pauli path (from scratch) — truncation ε=1e-1 to 1e-5

## Key Finding
All three classical methods struggle at large U/t, each 
controlled by a different parameter (δt, χ, ε) — suggesting 
a unified picture of classical simulability of the FHM.

## Requirements
pip install quspin openfermion qiskit qiskit-aer physics-tenpy

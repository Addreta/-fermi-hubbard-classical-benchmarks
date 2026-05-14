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
# 1D Fermi-Hubbard Model: Classical Simulation Benchmarks
### Trotter | MPS-TDVP | Pauli Path

A systematic benchmarking study of three classical simulation 
methods for real-time Néel dynamics in the 1D Fermi-Hubbard model.

## Motivation

This work is motivated by two recent papers:

- **Chowdhury et al.** (Applied Physics Reviews, 2026): quantum 
  simulation of 1D FHM real-time dynamics on IBM hardware using 
  Trotterization, benchmarked classically with MPS-TDVP

- **Lin, Gharibyan & Su** (2024): Pauli path simulation for 
  utility-scale quantum state preparation at 100+ qubits

This study applies all three classical methods to the same 
observable (Néel order parameter) on the same Hamiltonian (1D FHM, 
L=4, half-filling), enabling direct comparison.

## Methods

| Method | Tool | Control parameter |
|--------|------|------------------|
| Exact diagonalization | QuSpin | — |
| 1st & 2nd order Trotterization | Qiskit | step size δt |
| MPS-TDVP | TeNPy | bond dimension χ |
| Pauli path | from scratch | truncation threshold ε |

## Key Results

- Trotter at δt=0.1 (2nd order) is essentially exact for L=4
- TDVP requires χ≥16 for accuracy at t=4 — sharp threshold 
  corresponding to entanglement growth
- Pauli path converges systematically: ε=1e-5 gives error <0.001
- All three methods struggle at large U/t — controlled by the 
  commutator norm ||[H_hop, H_int]|| ∝ U

## Notebooks

- `01_trotter_tdvp_comparison.ipynb` — Trotter vs TDVP vs exact
- `02_pauli_path.ipynb` — Pauli path implementation and benchmarking

## Requirements
# 1D Fermi-Hubbard Model: Classical Simulation Benchmarks
### Trotter | MPS-TDVP | Pauli Path

A systematic benchmarking study of three classical simulation 
methods for real-time Néel dynamics in the 1D Fermi-Hubbard model.

## Motivation

This work is motivated by two recent papers:

- **Chowdhury et al.** (Applied Physics Reviews, 2026): quantum 
  simulation of 1D FHM real-time dynamics on IBM hardware using 
  Trotterization, benchmarked classically with MPS-TDVP

- **Lin, Gharibyan & Su** (2024): Pauli path simulation for 
  utility-scale quantum state preparation at 100+ qubits

This study applies all three classical methods to the same 
observable (Néel order parameter) on the same Hamiltonian (1D FHM, 
L=4, half-filling), enabling direct comparison.

## Methods

| Method | Tool | Control parameter |
|--------|------|------------------|
| Exact diagonalization | QuSpin | — |
| 1st & 2nd order Trotterization | Qiskit | step size δt |
| MPS-TDVP | TeNPy | bond dimension χ |
| Pauli path | from scratch | truncation threshold ε |

## Key Results

- Trotter at δt=0.1 (2nd order) is essentially exact for L=4
- TDVP requires χ≥16 for accuracy at t=4 — sharp threshold 
  corresponding to entanglement growth
- Pauli path converges systematically: ε=1e-5 gives error <0.001
- All three methods struggle at large U/t — controlled by the 
  commutator norm ||[H_hop, H_int]|| ∝ U

## Notebooks

- `01_trotter_tdvp_comparison.ipynb` — Trotter vs TDVP vs exact
- `02_pauli_path.ipynb` — Pauli path implementation and benchmarking

## Requirements

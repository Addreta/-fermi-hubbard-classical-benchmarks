
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

- Trotter at δt=0.1 (2nd order) is essentially exact at U/t=2 for L=4: Néel error ≤ 3.4×10⁻³ for t ≤ 6
- TDVP matches the exact result (to within ~10⁻⁵ at t=4) only at χ=16, the full bond dimension for L=4; below that the error falls slowly (0.67 → 0.10 from χ=1 to 8)
- Pauli path converges systematically for ε ≤ 10⁻²: the error at t=3 falls from 0.36 to ~4×10⁻⁴ (ε=10⁻² → 10⁻⁵)
- Only the Trotter error was swept over U/t. It grows with U/t, as does the commutator norm ‖[H_hop, H_int]‖ ∝ U; TDVP and Pauli path were run at U/t=2 only

## Notebooks

- `01_trotter_tdvp_comparison.ipynb` — Trotter vs TDVP vs exact
- `02_pauli_path.ipynb` — Pauli path implementation and benchmarking

## Requirements
pip install quspin openfermion qiskit qiskit-aer physics-tenpy
## References

1. Chowdhury et al., Applied Physics Reviews (2026)
2. Lin, Gharibyan & Su (2024)
3. Alam et al., Phasecraft (2025)

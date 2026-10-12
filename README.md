# MoleCompare

**MoleCompare** is a Qiskit-based quantum molecular screening workflow that estimates, validates, and compares the ground-state energies of small molecules using the Variational Quantum Eigensolver (VQE).

> Existing tools calculate molecular energy; MoleCompare turns VQE results into a validated, reproducible comparison report that helps researchers shortlist molecules for deeper study.

---

## Problem

Researchers often need to compare candidate molecules before spending time and money on detailed high-accuracy simulations or laboratory experiments.

Many basic quantum-chemistry demos calculate the energy of only one molecule. They do not provide a complete workflow for:

- Comparing multiple molecules
- Validating quantum results against reference values
- Reporting error and convergence
- Reproducing the experiment
- Shortlisting promising candidates

## Our Solution

MoleCompare provides a reproducible quantum molecular screening workflow:

```text
Select molecule
      ↓
Build molecular Hamiltonian
      ↓
Map problem to qubits
      ↓
Run VQE
      ↓
Estimate ground-state energy
      ↓
Validate against reference energy
      ↓
Compare molecular stability
      ↓
Shortlist candidate for deeper study
```

## Quantum Approach

Molecules and electrons obey quantum mechanics. Therefore, quantum computers can naturally represent molecular quantum states using qubits.

We use the **Variational Quantum Eigensolver (VQE)**, a hybrid quantum-classical algorithm:

1. Build the molecular electronic Hamiltonian.
2. Map the fermionic problem to qubits using Jordan-Wigner mapping.
3. Prepare a trial quantum state using an ansatz.
4. Measure the energy.
5. Use a classical optimizer to update ansatz parameters.
6. Repeat until the lowest-energy state is found.

The final result estimates the molecule’s ground-state energy.

## Qiskit Implementation

This project uses:

- **Qiskit**
- **Qiskit Nature**
- **PySCF** through `qiskit-nature-pyscf`
- **Jordan-Wigner mapping**
- **UCCSD / EfficientSU2 ansatz**
- **SLSQP / COBYLA optimizer**
- **StatevectorEstimator / Qiskit Aer simulator**

## Molecules Used

| Molecule | Purpose |
|---|---|
| H₂ | Simple baseline molecule for VQE validation |
| LiH | Slightly larger molecule for comparison |

## Scientific Validation

We do not show only a VQE energy value.

For each molecule, we report:

- VQE ground-state energy
- Exact diagonalization / FCI reference energy
- Absolute error
- Chemical-accuracy status
- Convergence plot
- Optimizer iterations
- Number of shots
- Basis set, ansatz, optimizer, and random seed

Chemical accuracy is defined as an energy error below approximately **1.6 milli-Hartree**.

## Results

| Molecule | VQE Energy | Reference Energy | Absolute Error | Chemical Accuracy |
|---|---:|---:|---:|---|
| H₂ | To be added | To be added | To be added | To be added |
| LiH | To be added | To be added | To be added | To be added |

Result charts and comparison tables will be added in the `results/` folder.

## How to Run

### 1. Clone the repository

```bash
git clone [https://github.com/](https://github.com/)<your-username>/molecompare-qiskit.git
cd molecompare-qiskit
```

### 2. Create a virtual environment

```bash
python -m venv venv
```

Activate it:

```bash
# Windows
venv\Scripts\activate

# macOS/Linux
source venv/bin/activate
```

### 3. Install requirements

```bash
pip install -r requirements.txt
```

### 4. Run the H₂ notebook

Open:

```text
notebooks/01_H2_VQE.ipynb
```

Run all cells.

### 5. Run the LiH notebook

Open:

```text
notebooks/02_LiH_VQE.ipynb
```

Run all cells.

## Repository Structure

```text
molecompare-qiskit/
├── README.md
├── requirements.txt
├── notebooks/
│   ├── 01_H2_VQE.ipynb
│   └── 02_LiH_VQE.ipynb
├── src/
│   ├── molecule_setup.py
│   ├── vqe_runner.py
│   ├── validation.py
│   └── comparison.py
├── results/
├── demo/
├── docs/
└── presentation/
```

## Limitations

- This is a proof of concept, not a drug-discovery platform.
- We simulate only small molecules such as H₂ and LiH.
- Current quantum hardware has limited qubits and noise.
- Classical methods can already solve small molecules accurately.
- Results depend on basis set, active space, ansatz, optimizer, and measurement shots.
- Scaling VQE to drug-sized molecules remains an open challenge.
- Main results use a quantum simulator.

## Future Scope

- Add more molecules and larger active spaces.
- Use noise mitigation and error-suppression methods.
- Test selected circuits on real IBM Quantum hardware.
- Add bond-distance scanning and geometry optimization.
- Integrate with molecular docking and molecular-dynamics workflows.
- Build a complete molecular-screening dashboard.

## Team

| Name | Role |
|---|---|
| Your Name | Quantum Implementation |
| Teammate Name | Research and Validation |
| Teammate Name | Demo and Presentation |

## References

- Qiskit Documentation
- Qiskit Nature Documentation
- Qiskit Algorithms Documentation
- PySCF Documentation

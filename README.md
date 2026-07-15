# O₂ Quantum Coherence Workflow with PySCF and TENSO

A reproducible computational workflow for studying electronic coherence in molecular oxygen by combining **first-principles multireference electronic structure calculations** with **open quantum system dynamics**.

Developed as a mini-project for the **CyberTraining Summer Workshop**.

---

## Overview

This project demonstrates a complete computational pipeline that bridges **electronic structure theory** and **quantum dynamics**.

Electronic structure calculations are performed with **PySCF** to obtain physically meaningful parameters that are subsequently used to parameterize **Hierarchical Equations of Motion (HEOM)** simulations performed with **TENSO**.

Rather than treating model parameters as adjustable quantities, this workflow derives them directly from first-principles calculations, providing a reproducible route from quantum chemistry to quantum dynamics.

---

## Scientific Motivation

Electronic coherence plays an important role in ultrafast molecular processes, including photochemistry, energy transport, and spin-dependent phenomena.

Molecular oxygen (O₂) provides an excellent model system because its **triplet ground state** requires a multireference electronic description, making it a useful benchmark for connecting electronic structure methods with quantum dynamical simulations.

This project investigates how

- vibronic coupling,
- temperature,
- and environmental damping

influence electronic coherence using a physically motivated two-level model derived from ab initio calculations.

---

# Workflow

```
ROHF (PySCF)
        │
        ▼
CASCI Electronic Structure
        │
        ▼
Potential Energy Curves
        │
        ▼
Parameter Extraction
  • Singlet–triplet gap
  • Vibrational frequency
  • Force constant
  • Reorganization energy
        │
        ▼
TENSO HEOM Dynamics
        │
        ▼
Electronic Coherence Analysis
```

---

# Repository Structure

```
o2-pyscf-tenso/

├── notebooks/
│   └── o2_tenso_dynamics.ipynb
│
├── scripts/
│   ├── test_o2.py
│   ├── inspect_o2_orbitals.py
│   ├── o2_cas22_test.py
│   ├── o2_cas64_test.py
│   ├── o2_cas22_scan.py
│   ├── o2_cas64_scan.py
│   ├── plot_o2_scan.py
│   └── plot_o2_cas64_scan.py
│
├── figures/
│
├── data/
│
├── docs/
│
└── README.md
```

---

# Methods

## Electronic Structure

Electronic structure calculations were performed using **PySCF**.

Methods include

- Restricted Open-Shell Hartree–Fock (ROHF)
- CASCI
- CAS(2,2)
- CAS(6,4)
- cc-pVDZ basis set

Bond-length scans were used to determine

- equilibrium geometry
- harmonic vibrational frequency
- singlet–triplet energy gap
- vibronic coupling parameters

---

## Quantum Dynamics

Open quantum system simulations were performed using **TENSO**.

The electronic system was represented as a two-level Hamiltonian coupled to a Brownian oscillator bath and propagated using the Hierarchical Equations of Motion (HEOM).

The effects of

- temperature,
- vibronic coupling strength,
- and bath damping

were investigated through parameter studies.

---

# Key Results

## CAS(6,4) Electronic Structure

| Quantity | Value |
|-----------|------:|
| Equilibrium bond length | 1.183 Å |
| Harmonic frequency | 1786 cm⁻¹ |
| Singlet–triplet gap | 0.813 eV |
| Reorganization energy | 65.8 cm⁻¹ |

---

## Quantum Dynamics

Three parameter studies were performed:

### Temperature

77 K

150 K

300 K

Electronic coherence exhibited only weak temperature dependence during the first 60 fs.

---

### Vibronic Coupling

0.25 λ

1.0 λ

2.0 λ

Increasing vibronic coupling produced progressively faster coherence loss, demonstrating that electron–phonon coupling is the dominant mechanism governing decoherence in the present model.

---

### Bath Width

20 cm⁻¹

50 cm⁻¹

100 cm⁻¹

Increasing the Brownian oscillator damping width produced modest reductions in long-time coherence while leaving the initial coherence minimum nearly unchanged.

---

# Conclusions

This project demonstrates a reproducible workflow connecting first-principles electronic structure calculations with open quantum system dynamics.

The results indicate that

- vibronic coupling strength is the primary driver of electronic decoherence,
- bath damping produces comparatively modest effects,
- and temperature has little influence over the simulated ultrafast timescale.

The workflow provides a framework for studying quantum coherence in molecular systems using parameters derived directly from ab initio calculations.

---

# Software

- Python
- PySCF
- NumPy
- SciPy
- Matplotlib
- Pandas
- TENSO

---

# Reproducibility

1. Perform the PySCF calculations.
2. Extract vibronic parameters from the bond-length scan.
3. Use the extracted parameters to construct the HEOM model.
4. Run TENSO dynamics.
5. Reproduce all figures contained in this repository.

---

# Acknowledgments

This project was developed as part of the **CyberTraining Summer Workshop**, with the goal of demonstrating reproducible scientific workflows that integrate electronic structure theory and quantum dynamics using modern open-source computational chemistry software.

---

# References

1. Sun, Q. *et al.* PySCF: The Python-based Simulations of Chemistry Framework.

2. TENSO Documentation and Source Code.

3. Tanimura, Y. Numerical approaches to open quantum systems using the Hierarchical Equations of Motion.

4. Szabo, A.; Ostlund, N. S. *Modern Quantum Chemistry.*

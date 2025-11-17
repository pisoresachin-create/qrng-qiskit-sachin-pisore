# qrng-qiskit-sachin-pisore
This project generates truly unpredictable random numbers using quantum superposition and measurement with Qiskit. Unlike classical pseudo-random methods, this QRNG leverages quantum states to ensure secure randomness suitable for cryptography, simulations, and secure key generation.
# Quantum Random Number Generator (QRNG) – Hackathon 2025

Overview

This project is my submission for the Qiskit Hackathon 2025.  
It implements a simple **Quantum Random Number Generator (QRNG)** using Qiskit, based on the idea of preparing qubits in superposition and using measurement to obtain truly random outcomes.

Classical random number generators are pseudo-random, because they are based on deterministic algorithms. In contrast, a quantum system prepared in superposition and then measured produces outcomes that are fundamentally unpredictable.

---

Goal

- Create a quantum circuit that generates random numbers.
- Decide the number of qubits and corresponding possible outcomes.
- Use **Hadamard gates** to prepare an equal superposition.
- Measure the qubits and map the observed bit string to an integer.
- Ensure that the final random number is obtained **directly from the quantum measurement**, not from a classical random function.

---

##  Method

1. **Circuit preparation**
   - Start with `n` qubits initialized in \|0⟩.
   - Apply a Hadamard gate `H` to each qubit.
   - This creates a uniform superposition over `2^n` basis states.

2. **Measurement**
   - Measure all qubits in the computational basis.
   - For a single shot, the backend returns one bit string (e.g. `"010"`).

3. **Mapping to integer**
   - Convert the bit string to an integer using binary → decimal.
   - Example: `"010"` → `2`.

4. **Single-shot vs multi-shot**
   - **Single shot**: generate one quantum random integer.
   - **Multiple shots**: collect many outcomes and visualize their distribution to check fairness and study noise.

---

##  Usage Example

```python
from qrng.runner import run_qrng

# Generate one random number using 3 qubits
value = run_qrng(num_qubits=3)
print("Quantum random number:", value)

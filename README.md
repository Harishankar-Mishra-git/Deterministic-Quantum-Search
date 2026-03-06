# Deterministic Quantum Search (DQS)

This repository contains the Qiskit implementation of the **Deterministic Quantum Search** algorithm, as proposed in the paper: *"Deterministic Quantum Search for Arbitrary Initial Success Probabilities"*.

## Overview

Unstructured search is a fundamental problem in computer science. While Grover's algorithm and Quantum Amplitude Amplification provide a quadratic speedup over classical methods, they are inherently probabilistic. Furthermore, they offer no quantum advantage when the initial success probability of finding a target state exceeds 50%.

This project provides a deterministic alternative. By initializing ancilla qubit and applying the oracle and diffusion operators to search for a redefined target states, this algorithm guarantees a **100% success rate** for unstructured search problems across **arbitrary initial success probabilities** (even those > 50%), requiring at most one additional iteration compared to the standard probabilistic search algorithms.

## Features
* **Deterministic Outcome:** Guarantees the measurement of a target state with certainty (Probability = 1).
* **High Initial Probability Handling:** Operates effectively even when the initial success probability exceeds 0.5, a domain where standard Grover's algorithm fails to provide an advantage.
* **Bounded Steps:** Maintains the $O(\sqrt{N/M})$ query complexity characteristic of quantum search algorithms.

## Requirements

To run the Jupyter Notebook, you will need the following Python libraries installed:

* `qiskit`
* `qiskit-aer`
* `numpy`
* `matplotlib` (for circuit and histogram plotting)

You can install these dependencies using pip:
`pip install qiskit qiskit-aer numpy matplotlib`

## Usage

The core implementation is provided in `dqs.ipynb`. You can run the notebook directly to see the algorithm in action.

### Quick Start Example
The main function is `det_Grover(n, targets)`, where `n` is the number of data qubits and `targets` is a list of target state strings.

`from qiskit import QuantumCircuit, QuantumRegister, ClassicalRegister`
`from qiskit_aer import Aer`
`# ... (import other necessary functions from the notebook)`

`# Define a 3-qubit search space with two target states`
`n = 3`
`targets = ['111', '000']`

`# Run the Deterministic Quantum Search`
`det_Grover(n, targets)`

Output will display the generated quantum circuit and the measurement counts. Because the algorithm is deterministic, 1000 shots will yield exactly 1000 measurements distributed only among your target states.

## Repository Structure
* `dqs.ipynb`: The main Jupyter Notebook containing the algorithm functions (`get_theta`, `oracle`, `diffuser`, `det_Grover`) and execution examples.

## Citation
If you use this code in your research, please cite our paper:
> Harishankar Mishra, Asvija Balasubramanyam, Gudapati Naresh Raghava. "Deterministic Quantum Search for Arbitrary Initial Success Probabilities", 2026.

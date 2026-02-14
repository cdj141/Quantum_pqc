# Big Quantum Circuits on Small Quantum Computers

Study of parameterized quantum circuits (PQCs) for binary classification
and approximation of large quantum circuits using ensembles of smaller
circuits.

## Overview

This project investigates two core questions in near-term quantum
machine learning:

1.  How stable are shallow PQC classifiers during training?
2.  Can the behavior of a larger quantum circuit be approximated using
    multiple smaller circuits?

Experiments are conducted using noiseless state-vector simulation.

## Part 1: PQC Classifier

Architecture:

-   3 qubits
-   Input encoding via RX(x0) and RY(x1)
-   Trainable RY layers
-   Nearest-neighbor CNOT entanglement
-   Output: expectation value of Z ⊗ n

Loss function: Mean Squared Error (MSE)

Optimizer: Adam (learning rate 0.02, 30 epochs)

Dataset: - Two-moons synthetic dataset (200 samples) - Noise = 0.1 -
70/30 train-test split - Labels mapped to {-1, +1}

### Results

-   Strong sensitivity to random initialization
-   Training loss rapidly saturates
-   Test accuracy range: 0.17 -- 0.77
-   Mean accuracy: 0.49 (σ = 0.22)

Observation: Shallow PQCs suffer from unstable optimization and early
plateaus.

## Part 2: Large Circuit Approximation

Big circuit: - 6 qubits

Small circuit: - 3 qubits

Goal: Approximate 6-qubit output using an ensemble of M small circuits.

Ensemble prediction: Average or weighted average of small circuit
outputs.

Evaluation metric: Mean Squared Error (MSE)

### Results

For M = 4: MSE = 0.1393

Best observed configuration: M = 8 with weighted averaging MSE = 0.0297

Key findings:

-   Approximation error is non-negligible
-   Error does not decrease monotonically with ensemble size
-   Weighted averaging does not consistently outperform simple averaging
-   Limited qubit count restricts expressivity and entanglement

## Limitations

-   Randomly initialized circuits (no distillation training)
-   No hardware noise simulation
-   Shallow architectures only
-   Global observable comparison only

## Future Work

-   Train small circuits to mimic large circuit outputs
-   Explore circuit-cutting strategies
-   Extend to noisy simulation
-   Analyze deeper architectures


## Run

pip install pennylane numpy matplotlib scikit-learn

Run notebooks or scripts directly in Jupyter.

## Technologies

Python\
PennyLane\
NumPy\
scikit-learn\
Matplotlib

## Author

Dongjie Chen\
MSc Computer Science (Data Science), Leiden University

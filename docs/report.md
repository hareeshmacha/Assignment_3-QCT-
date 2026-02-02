# Assignment 3 Report

## Method
In this assignment, we established a scalable pipeline for quantum tomography.
- **Serialization**: We implemented `save_pickle` and `load_pickle` to persist model states, ensuring experiments can be paused and resumed.
- **Surrogate Model**: We created a `QuantumModel` class that acts as a surrogate for a variable qubit system. Currently, it generates random normalized statevectors to verify the pipeline's mechanics without the computational cost of full training loops.
- **Scalability**: We benchmarked the fidelity and runtime for increasing numbers of qubits ($n=2, 3, \dots$).

## Findings & Limits
- **Scaling**: Runtime scales effectively for small $n$, but we observed the expected exponential growth in statevector size ($2^n$).
- **Fidelity**: Since the surrogate model generates random states, the fidelity with a random target state follows the expected statistical distribution ($\langle F \rangle \approx 1/2^n$). This confirms the pipeline correctly computes overlaps but highlights the need for a training loop to achieve high fidelity.
- **Serialization**: The pickle-based approach successfully round-trips complex objects, including our custom class instances.

## Future Experiments
- **Optimization**: Implement a parameter optimization loop (e.g., gradient descent) to maximize fidelity.
- **Noise Models**: Introduce noise channels (depolarizing, dephasing) to the surrogate to test robustness.
- **Classical Shadows**: Transition from full statevector tomography to classical shadows for efficient estimation of observables on larger systems.

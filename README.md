### Team Name:

Penn Ave Fish Company

### Project Description:

A prerequisite for quantum algorithms to outperform their classical counterparts lies in the ability to efficiently load the classical input of the algorithms into quantum states. However, to prepare a generic quantum state exactly requires O(2^n) gates [[1](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.85.1334)], which can impede the power of quantum algorithms before they come into play. For practical purposes, Quantum Machine Learning (QML) can be adopted to approximate the desired loading channel via training. Quantum Generative Adversarial Network (qGAN) in particular has shown great promise in accomplishing the task with O(poly(n)) gates [[2](https://www.nature.com/articles/s41534-019-0223-2)]. Similar to its classical counterpart, qGAN consists of both a generator for synthesizing data to match the real data and a discriminator for discerning real data from the product of the generator. The difference between the two is that qGAN has a quantum generator for approximating the quantum state, and the discriminator can be either classical or quantum depending on whether the input data is classical or quantum [[3](https://pennylane.ai/qml/demos/tutorial_QGAN.html)]. Generally, the qGAN trains its generator and discriminator alternatively in the form of a zero-sum game, and ends the training when the relative entropy (i.e. the difference between the real data and the synthesized one, one measure of the training performance) converges to ~0 [[2](https://www.nature.com/articles/s41534-019-0223-2)].

For our project, we aim to use the quantum advantage of qGAN to demonstrate the efficient loading of multi-dimensional classical distribution with a classical discriminator. We will use PennyLane and its Cirq plug-in to construct the quantum circuit for the task. The simulation and training will be carried out using the Floq simulator and Tensorflow respectively. In the first stage of the project, we will complete a working code for our goal. Then, we will focus on the optimization on of the rate of convergence. The ideas under development include – 1) optimize the starting distribution for learning; 2) look into structural variation between the generator and the discriminator. More specifically, to learn a set of randomly IID generated distributions from another distribution consecutively, one may take the windowed average of the convergence values as input for the next sample. On the other hand, one may employ stochastic gradient decent (SGD) on the generator and discriminator alternatively to optimize the structure. The optimization ideas are not set and will be finished given the time condition. Finally, we will benchmark the convergence performance and the fidelity from our qGAN on the IonQ Q11 and TN1 simulators, showing the improvements from optimization.

### Source code:

https://github.com/Allenator/variational-structure-qgan-draft/

### Resource Estimate:

The initial testing will be carried out on Floq, which offers free access. Therefore, we only need to spend on simulations for testing the final results. Due to potential issues with the lackluster connectivity of Rigetti Aspen-9, we choose IonQ Q11 for final testing. IonQ Q11 costs:

- $0.30 per task + $0.01 per shot

And we will need ~10^4 shots are needed to study distribution spread across O(2^n) states, which gives us:

- $10.3 per task

~400 tasks are required for the study of variational structures, which gives us in total:

- ~$4000 cost

We also plan to use TN1 for cross checks, but given that TN1 costs $0.275/min and we require <= 50 qubits and <= 100 gate depth, then with parallelism of five 10-qubit circuit running for ~18 hours, we will only arrive at ~$250. This is modest compared to the IonQ cost, and can be covered with our previous AWS credit from challenge.

### Reference:

[1] Grover, L. K. Synthesis of quantum superpositions by quantum computation.
Phys. Rev. Lett. 85, 1334–1337 (2000).
[2] Zoufal, C., Lucchi, A. & Woerner, S. Quantum Generative Adversarial Networks for learning and loading random distributions. npj Quantum Inf 5, 103 (2019).
[3] PennyLane dev team, Quantum Generative Adversarial Networks with Cirq + TensorFlow (2021).
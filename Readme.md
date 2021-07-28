## Introduction to Quantum Deep Learning

This repository contains the details for the [EuroPython Talk](https://ep2021.europython.eu/talks/7QW9AdF-introduction-to-quantum-deep-learning/). This includes resources, and implementations of the useage of Quantum Variational Circuits and Hybrid Classical-Quantum Circuits for deep learning based applications. The platform used for the notebooks are [Tensorflow](https://www.tensorflow.org/) and [Pennylane](https://pennylane.ai/). [Video](https://youtu.be/V92trw5bK34)  Following are the different parts of the repository:

### Quantum Gates

This colab notebook provides a gentle introduction to Quantum Circuits(pure) which comprises of randomized gates (Hadamard/Rx/Pauliz) and also the steps to optimize a cost function with the help of qubits. The notebook also contains the details of plotting the raw expectations from a Quantum Circuit in a Bloch Sphere with the help of [Qiskit](https://qiskit.org/)

![image](https://user-images.githubusercontent.com/30946547/127304885-566d9107-739b-4351-9718-e034cdfe0178.png)

### Quantum Gradients 

This notebook provides an outline how to optimize a cost function based on a qubit rotations with the help of Tensorflow platform. In this case, we will be looking at how to apply classical autodifferentiation libraries like Tensorflow on quantum circuits for gradient convergence. To optimize your hybrid classical-quantum model using the TensorFlow eager interface, we have to make use of the TensorFlow optimizers provided in the tf.train module, or your own custom TensorFlow optimizer. Here we will be having 2 wires and associated angles (phi and theta). We will be applying the RX ,RY gates followed by a CNOT and a PauliZ gate. The cost function will try to match the qubit’s state — the direction it points on the Bloch sphere — to a target value, initially at the south pole. Using PennyLane’s automatic differentiation features and the built-in Tensorflow optimizers, we can adjust the circuit’s parameters until the qubit matches the target.

![image](https://user-images.githubusercontent.com/30946547/127305143-d14b5f33-735a-4bba-8ec4-d3f9d74c259a.png)

### Quantum Embeddings and CQC Hybrid Circuits

This notebook contains details about Quantum Embeddings and how data is encoded in Hilbert space. Basis,Amplitude and Angle Embeddings have been discussed in details in this notebook. This notebook also contains details of implementing a classical Quantum Hybrid circuit for MNIST digit classification with help of Tensorflow. The circuit diagram adapted from Pennylane: ![image](https://user-images.githubusercontent.com/30946547/127305560-b1e22596-924e-4472-bb8e-4b622254c021.png)

One of the major drawbacks of randomized quantum circuits is its susceptibility to Barren Plateaus where learning becomes stagnant.While starting from a parameterized random quantum circuit seems like a good unbiased choice if we do not know the problem structure, McClean et al. (2018) show that “for a wide class of reasonable parameterized quantum circuits, the probability that the gradient along any reasonable direction is non-zero to some fixed precision is exponentially small as a function of the number of qubits.”
We also see how to resolve the Barren Plateaus using Increasing the Layer depth of QNNs. 
![image](https://user-images.githubusercontent.com/30946547/127305776-97d24ba7-0754-43cc-8c50-84815547d10d.png)


### QuanConvolution Network

In this notebook, we we will be analysing the QuanConvolution Network which is a variant of QHC and includes quantum encoding the MNIST dataset before passing it into a classical network for digit classification. This segment has been abstracted from PennyLane's [official sample](https://pennylane.ai/qml/demos/tutorial_quanvolution.html). The [paper](https://arxiv.org/abs/1904.04767) contains the details of the approach. ![image](https://user-images.githubusercontent.com/30946547/127305957-09540af4-cb26-4756-b600-868961e27c80.png)

The idea behind Quanconvolution Circuits are :

- A small region of the input image, in our example a 2×2 square, is embedded into a quantum circuit. In this demo, this is achieved with parametrized rotations applied to the qubits initialized in the ground state.

- A quantum computation, associated to a unitary U, is performed on the system. The unitary could be generated by a variational quantum circuit or, more simply, by a random circuit.

- The quantum system is finally measured, obtaining a list of classical expectation values. The measurement results could also be classically post-processed as proposed in the paper. But, for simplicity, in this demo we directly use the raw expectation values.

- Analogously to a classical convolution layer, each expectation value is mapped to a different channel of a single output pixel.

- Iterating the same procedure over different regions, one can scan the full input image, producing an output object which will be structured as a multi-channel image.

- The quantum convolution can be followed by further quantum layers or by classical layers.

- The main difference with respect to a classical convolution is that a quantum circuit can generate highly complex kernels whose computation could be, at least in principle, classically intractable.


### Quantum On Policy RL

This notebook contains the implementation of deep on policy algorithms such as TRPO/PPO on quantum control. Reinforcement Learning as [quantum control](https://arxiv.org/pdf/1802.04063.pdf) leverages QHC for creating optimizations for on policy networks for Deep RL. Policy-gradient-based reinforcement learning (RL) algorithms are well suited for optimizing the variational parameters of QAOA in a noise-robust fashion, opening up the way for developing RL techniques for continuous quantum control. This is advantageous to help mitigate and monitor the potentially unknown sources of errors in modern quantum simulators.

![image](https://user-images.githubusercontent.com/30946547/127306307-492184f3-a01b-46e4-a42a-6d10e320bb38.png)

### Quantum GAN

This demo constructs a Quantum Generative Adversarial Network (QGAN) [(Lloyd and Weedbrook (2018), Dallaire-Demers and Killoran (2018))](https://journals.aps.org/pra/abstract/10.1103/PhysRevA.98.012324) using two subcircuits, a generator and a discriminator. The generator attempts to generate synthetic quantum data to match a pattern of “real” data, while the discriminator tries to discern real data from fake data (see image below). The gradient of the discriminator’s output provides a training signal for the generator to improve its fake generated data.
The Generator circuit appears as follows:

![image](https://user-images.githubusercontent.com/30946547/127306624-66f96702-f334-4c1e-8bea-6117d247e0dc.png)


The Discriminator Circuit appears as follows:

![image](https://user-images.githubusercontent.com/30946547/127306664-24b0932f-dc42-4c7e-b4bc-f8bf99519892.png)


### Quantum GRNN

This notebook has been taken from [Pennylane](https://pennylane.ai/qml/demos/tutorial_qgrnn.html) and it provides an outline how to use QGRNN for Ising model.


![image](https://user-images.githubusercontent.com/30946547/127309425-a0b26031-3c57-49d1-946f-8a7eaa5e8685.png)


## Resources:

The resources for Quantum Variational Circuits for different platforms such as Tensorflow Quantum and Qiskit are provided below:

- [Cirq](https://quantumai.google/cirq/tutorials/variational_algorithm)
- [Qiskit](https://qiskit.org/documentation/machine-learning/tutorials/01_neural_networks.html)
- [Pennylane](https://pennylane.ai/qml/demos_research.html)

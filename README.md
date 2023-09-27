# inferring effective couplings with RBMs

![Static Badge](https://img.shields.io/badge/arXiv%3A2309.02292-Inferring%20effective%20couplings%20with%20Restricted%20Boltzmann%20Machines)

Code for implementing the mapping between a Restricted Boltzmann Machines and Generalized Ising model introduced in the paper *Inferring effective couplings with Restricted Boltzmann Machines* by Aurélien Decelle, Cyril Furtlehner, Beatriz Seoane, and Alfonso Navas. 

<p align="center">
  <img src=https://github.com/alfonso-navas/inferring_effective_couplings_with_RBMs/blob/main/RBM_inference_figure.png?raw=true
</p>

## Introduction

In recent years, generative models have gained significant popularity in the field of *Machine Learning* (ML). These models can learn intricate statistical patterns from diverse data sources and produce new data that closely mimics the original. Among the different techniques for generative modeling, *energy-based models* (EBMs) are noteworthy for their distinct capability to offer an effective representation of the data. One such example is the *Restricted Boltzmann Machine* (RBM), which operates as an undirected stochastic neural network defined on a bipartite graph consisting of two layers of variables (or units): 
* the *visible* variables $\boldsymbol{v}$, that represents the configurations of the data, and
* the *hidden* nodes $\boldsymbol{h}$, on which the latent representations of the data are carried.

Thus, the joint probability distribution of a given configuration $\boldsymbol{v}, \boldsymbol{h}$ is given by the Boltzmann distribution:

$$
p(\boldsymbol{v}, \boldsymbol{h}) = \frac{1}{\mathcal{Z}} e^{-\mathcal{H}(\boldsymbol{v}, \boldsymbol{h})}, \ \mathrm{with} \ \mathcal{Z}=\sum_{\boldsymbol{v}, \boldsymbol{h}} e^{-\mathcal{H}(\boldsymbol{v}, \boldsymbol{h})}.
$$

Where, $\mathcal{H}$ is the so called *energy function* or *Hamiltonian* of the RBM:

$$
 \mathcal{H}(\boldsymbol{v}, \boldsymbol{h}) = - \sum_{i=1}^{N_h} c_i h_i  - \sum_{j=1}^{N_v} b_j v_j - \sum_{j=1}^{N_v} \sum_{i=1}^{N_h}  h_i W_{ij} v_j
$$

In the [paper](https://arxiv.org/abs/2309.02292), we showed that the effective Hamiltonian that describes the equilibrium statistics of visible variables can be expanded as a Generalized Ising Model (GIM) Hamiltonian, which also accounts for higher-order interactions.

$$ 
\mathcal{H}(\boldsymbol{\sigma}) = - \sum_{j} H_j \sigma_j - \sum_{j_1 > j_2} J_{j_1 j_2}^{(2)} \sigma_{j_1} \sigma_{j_2} + \dots + \sum_{j_1 > \cdots > j_n} J_{j_1 \cdots j_n}^{(n)} \sigma_{j_1} \cdots \sigma_{j_n} + \dots 
$$

In this repo, we will provide the practical implementation of the mapping between the RBM parameters $\eta_j, \theta_i, w_{ij}$ and the couplings $H_{j}$ and $J_{j_1, j_2}^{(2)}$. 

## Contents
- [couplings_inference:](https://github.com/alfonso-navas/inferring_effective_couplings_with_RBMs/blob/main/couplings_inference.ipynb) Detailed presentation of the Python functions that implement the mapping combined with examples of how to use them.
- [Ising_samples:](https://github.com/alfonso-navas/inferring_effective_couplings_with_RBMs/tree/main/Ising_samples) Training dataset used in the RBM models provided as examples.
- [models:](https://github.com/alfonso-navas/inferring_effective_couplings_with_RBMs/tree/main/models) Trained RBM models used as examples.

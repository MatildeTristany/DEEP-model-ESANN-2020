# DEEP-model-ESANN-2020
Equilibrium Propagation for Complete Directed Neural Networks

> Artificial neural networks, one of the most successful approaches to supervised learning, were originally inspired by their biological counterparts. However, the most successful learning algorithm for artificial neural networks, backpropagation, is considered biologically implausible. This work aims to contribute to the topic of biologically plausible neural learning by building upon and extending the equilibrium propagation model introduced by [Scellier and Bengio (2017)](https://arxiv.org/abs/1602.05179). Specifically, we introduce: a new neuronal dynamics and learning rule for arbitrary network architectures; a sparsity-inducing method able to prune irrelevant connections; a dynamical-systems characterization of the models, using Lyapunov theory.

The DEEP model here implemented is described by [Equilibrium Propagation for Complete Directed Neural Networks](https://fenix.tecnico.ulisboa.pt/cursos/mma/dissertacao/283828618790517), by Matilde Tristany Farinha, Sérgio Pequito, Pedro A. Santos and Mário T. Figueiredo.

## How it works

**I** - Package requirements:
- This code is written in jupyter notebooks;
- Python 3.6.5 is used.

**II** - Files:
- *logical_operations_DEEP.ipynb*: contains DEEP's implementation for learning logic operations (introduced on Chapter 4 & 5 from [MSc Thesis (2019)](https://fenix.tecnico.ulisboa.pt/cursos/mma/dissertacao/283828618790517, https://arxiv.org/abs/2006.08798v2));
- *logical_operations_DEEP_oh.ipynb*: contains the asymmetric EP's implementation for learning logic operations with onehot encoding (based on [MSc Thesis (2019)](https://arxiv.org/abs/2006.08798v2);
- *logical_operations_EP_asym.ipynb*: contains the asymmetric EP's implementation for learning logic operations (based on [Scellier et al. (2018)](https://arxiv.org/abs/1808.04873).

**III** - Details in the Files:
Each model trained is automatically saved into a .save document. The following binary paramaters are given to the training function (*train*):
- *regularized*: if True, adds L1 regularization to the learning rule;
- *sparse*: if True, actively removes connections through the sparsity inducing method introduced in [Equilibrium Propagation for Complete Directed Neural Networks](https://fenix.tecnico.ulisboa.pt/cursos/mma/dissertacao/283828618790517).

The hyperparameters given (as a dictionary) to the training function are:
- *N_H*: number of hidden neurons;
- *n_epochs*: number of training epochs;
- *T1*: number of 1st phase iterations;
- *T2*: number of 2nd phase iterations;
- *dt*: learning step of the state variable;
- *stop*: near-equilibrium relaxation parameter;
- *beta*: clamping factor;
- *dt_W*: learning step for the synaptic weights;
- *beta_0*, *beta_1*: STDP parameters;
- *reg_W*: influence of the L_1 regularization term in the learning rule;
- *tol_W*: threshold bellow which the synaptic weights are considered for removal;
- *temp*: temperature of the Bolzmann distribution used for sparsification;

Additionally, the training function also receives the number of models it should train: *num_net*.

Some auxiliary functions are defined in both jupyter notebooks:
- *constrain_weights*: function that constrains the matrix of synaptic weights (and biases);
- *hard_sigmoid*: function that bounds the input (hard-sigmoid);
- *weigths_init*: function that initializes weights;
- *states_init*: function that initializes the states;
- *get_predictions*: function that gets the prediction labels from the output when not one-hot encoded (y_out<0.5 => y_pred=0 and y_out>0.5 => y_pred=1);
- *avg_neq*: function that computes the average classification error (number of unequal predictions).

To test the model, we created the function *test_predcitions*, which receives the inputs (*X*), *N_H* and the number of output neurons (*N_Y*), and returns the predicted output.

The code is further commented in each notebook.

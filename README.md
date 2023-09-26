# flowing
_flowing_ contains a machine learning tool applying normalising flows to Bayesian gravity inversion. This project has two aspects to it:
1. Generate a data set consisting of rectangular prism (box) underdensities. Two different representations can be chosen.
   1.1 The box can be described by 9 parameters and the forward model described in Li et al. (1998) is applied to compute the gravitational signal at the given gravimetry survey locations.
   1.2 The box can also be described as an array of density values of a grid of voxels, and the forward model can be computed for each voxel seperately, and the results are summed for all survey locations.
2. Using the generated data set a neural network can be trained which uses a normalising flow method to infer the parameters (9 parameteres, or array of densities) of the box. Tools to test the network and plot the results are also included.
The _nflows_ (C. Durkan et al. 2019) package is used to construct implement the normalising flow elements and _glasflow_ (Williams et al. (2023) is used to construct the neural network. 

## Installation

## Usage
**Data generation:**
1. make_data.py script includes all functions necessary for the generation of the data set.
2. To generate a comprehensive example data set, with both parameterised and voxelised data representation the sim_data.py can be ran as
```bash
python sim_data.py
```
To edit the data set setup and the data location, edit the _params.json_ file.

**Gravity inversion:**
1. A neural network can be trained with the generated data set, or any other data set we desire to use.
```bash
python grav_inv_flow.py
```
The data set used and the network parameters are defined in _params.json_.
3. During training, diagnostics can are plotted and saved.
4. After training, the trained flow model can be saved, which then can be used to test the performance of the method or simply use it for inversion. As long as the problem we are trying to solve is consistent with the training data set, the network does not need to be retrained.
To run a test with an example set of data:
```bash
python test_grav_inv_flow.py
```
The test data location and flow model locations are defined in _params.json_.
## Contributing

## Acknowledgements

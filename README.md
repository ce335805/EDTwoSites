# ED code for two site system
 This repository contains the ED code for reproducing the data for https://arxiv.org/abs/2303.02176.

## Installation

The code uses `cmake`, `python` and the `hdf5` file format.
Installations of all of these tools are necessary to run the code.
We performed computations with python 3.9.7, cmake 3.16.3, hdf5 1.10.4 and as the MKL version 2021.10.0.
The preferred `c++` compiler may be configured in the `CMakeLists.txt` file in the top directory.
We used intels icc compiler version 2021.10.0 but a newer compiler should work as well.
The code is installed using cmake and, if all needed packages are configured suitably, should take less than a minute to install on a stadard laptop.

## Usage

First clone the respository as usual from this repository.
Then change into the directory for setting up the Hamiltonian

```
$ cd setupH
```

Within this directory create a new subdirectory

```
$ mkdir savedOperators
```
and run the python script to create the different operators used by ED

``` 
$ python setupH.py
```

Afterwards change back to the to directory by `cd ..` and create the directory for the output data
```
$ mkdir data/
```

Afterwards install the progam using `cmake`

```
$ cmake CMakeLists.txt
```

Afterwards build the project using the generated `Makefile`

```
$ make
```

Now one may run the executable that has been created

```
$ ./PolaritonSqueezing.out
```

In order to create the plots for the paper go to the plotting directory

``` 
$ cd plots/
```

create the directory to save the created plots

``` 
$ mkdir savedPlots
```

and run the plotting script

```
$ python plotMain.py
```

The code is currently configured to only work with small parameters sets such that its execution on a laptop should take less than 10 minutes.
However, results are not converged in the parameters such that this will not reproduce the identical results of the paper.
To reproduce them one will need to run the code on an HPC system.
The parameters may be adjusted suitably in `./include/globals.h`.


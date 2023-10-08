# CUDA Advanced Libraries course project

## Description
This project uses the CUDNN library allows the creation of a fairly simple neural 
network using only a subset of the different types of layers. This code implements
Dense, Conv2D, POOL2D, and SoftMax layers to demonstarte a neural network to 
classify MNIST images of digits. The code also implements two different activations
for the layers, Relu and TanH, that are selectable from the command line. The code
also implements a Loss function, cross entropy, to allow the tuning of the weights
and biases. `model.hpp` and `model.cpp` are used to implement a simple linear nueralnet. 
To add a `Layer`, a user should call the `add()` method of the `Model` and supply as 
arguments a string indicating the type of layer desired, and an array or vector of 
integers that specify parameters relevant to the `Layer`. Note that the shape of a 
single input minibatch must be given to the Model's constructor as NCHW.

Once a Model is constructed, a user can call the Model's `train()` method with a set 
of training data of the specified input shape, a set of corresponding labels with the 
specified output shape, the number of training examples being used, and the desired 
mini-batch size. Similar functions exist to return the Model's predictions -` predict()` 
on a test set and to evaluate the Model's performance on a test set, given a set of 
ground truth labels - `evaluate()`.

The MNIST directory contains four files - The training set of images, the training
set of labels for the corresponding images, the test set of images amnd labels for
performing performance analysis of the model.

The MNIST dataset is not in a regular image file format. I am using a program from
Henry Tan and Aadyot Bhatngarm to read the MNIST dataset - `MNISTParser.hpp`.

The log file shows the output of running the program on the MNIST dataset found in
mnist directory.

## Key Concepts

Image Processing, Neural Network, CUDNN Library

## Supported SM Architectures

[SM 3.5 ](https://developer.nvidia.com/cuda-gpus)  [SM 3.7 ](https://developer.nvidia.com/cuda-gpus)  [SM 5.0 ](https://developer.nvidia.com/cuda-gpus)  [SM 5.2 ](https://developer.nvidia.com/cuda-gpus)  [SM 6.0 ](https://developer.nvidia.com/cuda-gpus)  [SM 6.1 ](https://developer.nvidia.com/cuda-gpus)  [SM 7.0 ](https://developer.nvidia.com/cuda-gpus)  [SM 7.2 ](https://developer.nvidia.com/cuda-gpus)  [SM 7.5 ](https://developer.nvidia.com/cuda-gpus)  [SM 8.0 ](https://developer.nvidia.com/cuda-gpus)  [SM 8.6 ](https://developer.nvidia.com/cuda-gpus)

## Supported OSes

Linux, Windows


## CUDA APIs involved
CUDNN 


## Build and Run
To build the executables simply run the `make` cammand at the root directory of the project.
The executable built will be bin/neuralnet. To run the program, you should use the command
`bin/neuralnet [--dir <mnist_directory>] [--act <"relu" or "tanh">]`. The --dir argument sets 
the directory from which the MNIST data will be read, while the --act argument sets the 
activation that this neural network will use for intermediate layers ("tanh" or "relu"). 
The default activation is relu.


### Windows
The Windows samples are built using the Visual Studio IDE. Solution files (.sln) are provided for each supported version of Visual Studio, using the format:
```
*_vs<version>.sln - for Visual Studio <version>
```

To build/examine all the samples at once, the complete solution files should be used.

run program by typing `./bin/nueralnet` at the command line in the main directory. The program assumes the folder structure of this project and will read the .mnist files from the mnist folder, do the computations.

### Linux
The Linux samples are built using makefiles. To use the makefiles, change the current directory to the sample directory you wish to build, and run make:
```
$ cd <sample_dir>
$ make
```
The samples makefiles can take advantage of certain options:
*  **TARGET_ARCH=<arch>** - cross-compile targeting a specific architecture. Allowed architectures are x86_64, ppc64le, armv7l.
    By default, TARGET_ARCH is set to HOST_ARCH. On a x86_64 machine, not setting TARGET_ARCH is the equivalent of setting TARGET_ARCH=x86_64.<br/>
`$ make TARGET_ARCH=x86_64` <br/> `$ make TARGET_ARCH=ppc64le` <br/> `$ make TARGET_ARCH=armv7l` <br/>
    See [here](http://docs.nvidia.com/cuda/cuda-samples/index.html#cross-samples) for more details.
*   **dbg=1** - build with debug symbols
    ```
    $ make dbg=1
    ```
*   **SMS="A B ..."** - override the SM architectures for which the sample will be built, where `"A B ..."` is a space-delimited list of SM architectures. For example, to generate SASS for SM 50 and SM 60, use `SMS="50 60"`.
    ```
    $ make SMS="50 60"
    ```

run program by typing `./bin/neuralnet` at the command line in the main directory. The program assumes the folder structure of this project and will read the mnist files from the mnist folder, do the computations.

# CUDA Build with Conda

This repository provides guidance for managing CUDA installations for Python development, especially when different versions of the CUDA Toolkit are required. Using Conda, we can simplify the process without installing multiple versions of the CUDA Toolkit locally.

## Using `cudatoolkit` in Conda

When working with packages like `pytorch`, it's common to install `cudatoolkit` via Conda. However, it's important to note that `cudatoolkit` in Conda only includes runtime libraries needed to run CUDA applications. It does not encompass the complete CUDA Toolkit's development environment, which consists of the compiler (`nvcc`), headers, and other essential tools for building CUDA applications from source. This becomes particularly relevant when you need to install Python packages from `pip` that require compiling CUDA code.

## Using `cudatoolkit-dev` in Conda

To access the full set of development tools, including the compiler and headers, `cudatoolkit-dev` is the preferred choice. This package includes the necessary components for compiling CUDA code. You can install it using the following command:

```bash
conda install -c conda-forge cudatoolkit-dev
```

## Setting Environment Variables

After installing cudatoolkit-dev, it's necessary to set the CUDA_HOME environment variable. This ensures that the correct CUDA version is used for compilation tasks. Set CUDA_HOME to the root of your Conda environment where cudatoolkit-dev is installed:

```bash
export CUDA_HOME=~/miniconda3/envs/your_env
```
Note that setting the environment variable via the terminal is a temporary measure. It only applies to the current terminal session and will not persist across new sessions. If you frequently work with CUDA, consider adding this export command to your shell's startup script (e.g., .bashrc or .bash_profile) to automate the process.

With CUDA_HOME set, you can now proceed to install Python packages that require compiling CUDA code using pip:
```bash
pip install your_package
```
Keep in mind that managing different CUDA versions and ensuring compatibility with your Python packages can be complex. Always refer to the specific package documentation for detailed installation instructions and CUDA version requirements.

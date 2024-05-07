# CUDA_Profiling

This is CUDA profiling project with an intention to compare the kernals performance details from both compute and systems tools from Nvidia.

# Project Introduction:
The project is a CUDA program that performs a simple mathematical operation on a set of input arrays. The goal is to showcase the performance benefits of using GPU acceleration through CUDA programming compared to a CPU-based implementation.

The project includes the following main components:
GPU Kernels:
gpu_testfunction: A CUDA kernel that performs the mathematical operation on the GPU.
gpu_testfunction_uni_mem: Another CUDA kernel that uses unified memory to manage data between the CPU and GPU.

CPU Function:
cpu_testfunction: A CPU-based implementation of the same mathematical operation.

Main Function:
Allocates memory for the input and output arrays on both the CPU and GPU.
Calls the cpu_testfunction to get the reference result.
Copies the input data from the CPU to the GPU using cudaMemcpy.
Launches the gpu_testfunction kernel on the GPU.
Copies the result from the GPU to the CPU using cudaMemcpy.
Launches the gpu_testfunction_uni_mem kernel on the GPU using unified memory.
Compares the results from the CPU and GPU implementations.




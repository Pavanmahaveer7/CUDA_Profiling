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


Observations-
•  gpu_testfunction_uni_mem kernel takes 83.6% of the total time (562.874 μs). 
•  Host-to-Device memory copy takes 10.4% of the total time (70.272 μs). 
•  Device-to-Host memory copy takes 4.8% of the total time (32.415 μs)

gpu_testfunction_uni_mem:
•	The kernel is executed once (1 instance).
•	The executed instructions per cycle (IPC) is 0.4, indicating relatively low instruction-level parallelism.
•	The SM (Streaming Multiprocessor) utilization is 20.2%, suggesting that the kernel is not fully utilizing the GPU's compute resources.
•	The memory throughput is 77.67 MB/s, and the memory utilization (Mem Busy) is 22.26%, indicating moderate memory access activity.
•	The L1/TEX cache hit rate is 25%, suggesting room for improvement in cache utilization.
•	The L2 cache hit rate is 99.01%, which is good
gpu_testfunction:
•	The performance metrics are similar to gpu_testfunction_uni_mem, with slightly higher SM utilization (20.28%) and memory throughput (77.67 MB/s).
Points to be considered and improvements needed:
•	•  The gpu_testfunction_uni_mem kernel dominates the execution time, suggesting it is the primary computational kernel in your application. 
•	•  Both kernels seem to have relatively low instruction-level parallelism (IPC) and moderate GPU utilization (SM Busy), indicating potential performance bottlenecks or opportunities for optimization. 
•	•  Memory access patterns appear to be moderately efficient, with reasonable memory throughput and L2 cache hit rates. However, the low L1/TEX cache hit rates suggest potential improvements in data access patterns or cache utilization. 
•	•  The memory copy operations (Host-to-Device and Device-to-Host) contribute a non-negligible portion of the total execution time, suggesting potential bottlenecks in data transfer between the host and device





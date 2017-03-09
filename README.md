# Parallel--Merge-Sort-Using-MPI
Implementing Merge Sort Using MPI
# Abstract
While merge sort is 
ll-understood in parallel algorithms theory, relatively little is known of how to implement parallel merge sort with mainstream parallel programming platforms as MPI, and run it. Hence better understanding of merge sort parallelization can contribute to better understanding of divide-and-conquer parallelization in general. Here, I investigate a serial and parallel merge-sorts with message-passing merge sort that runs on computer clusters with MPI. In my experiments, comparing measured time of serial and parallel version of merge sort, parallel version has achieved best speedup.

# 3- Parallel Implementation of Merge Sort Algorithm
 - Single Instruction Multiple Data
I have the same tasks and different data, so it is a good idea to use single instruction multiple parallel implementation.
# 3-1 Partitioning the Data equally
At first I partition the data equally into processors, but sometimes data cannot be equally dividable by processors. In order to have equal local data in each processor, I add one to local n, the quotient of the number of data (n) divided by the number of processors. And I have some new elements so I should assign them into zero. In order to calculate the number of new elements I subtract the local n from r, the remainder of the dividing the number of data by the number of processors. Afterwards, I generate the elements of data randomly. In order to generate some three-digit numbers I use the remainder of dividing random numbers by 1000.
# 3-2 Sorting the Data
I use the function MPI-Broadcast to send the size of local n to all processors and also allocate memory for them. And I use the function MPI Scatter to send the needed components to each of the other processors.
Afterwards, I call the sort function for all processors.
# 3-3 Merging the Data
I use the tree structure global sum strategy to merge the sorted data in each processor to produce a merged sorted array.
I need to find the pattern the rank of receiver and sender processors. If the rank of a processor is dividable by my step it receives the sorted array of the processor the rank of which is not dividable by the step, and merge it with its sorted array. I assign steps the multiples of 2.
# 4- Taking time
I calculate the CPU time by using the function Clock to measure the run-time of both serial and parallel implementations.


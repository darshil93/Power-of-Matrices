Formulations:

Four implemented formulations
In order to calculate the determinant of the kth power of the matrix, I implemented four formulations. Serial formulation, Strassen's formulation, Cannon's formulation, DNSformulation.

>- Steps to calculate determinant
The algorithm for finding the determinant of the k-th power of the matrix is as follows:
 *  Initially generate the array at the logical root process
 *  Use cannon or dns formulation distribute the array across the mesh or cube accordingly
 *  Calculate the k-th power of the matrix and then Find the determinant

>- Calculating matrix multiplication using associative property
To find the final result we calculated the product of k/2 and square the product. If k is
odd, then after squaring we multiply once more with matrix A. To enable associativity
in the program, add the -a flag when running.

>- Conventional Serial Formulation
In this formulation the conventional θ(n3) algorithm for matrix multiplication is implemented. The
runtime for this algorithm is θ(n^3).

>- Strassen Matrix Multiplication
The Strassen algorithm for matrix multiplication faster than serial matrix multiplication
algorithm. The running time of Strassen algorithm is O(N^2.8074)

>- Cannon Formulation
Algorithm is distributed for a mesh of nodes. For matrix multiplication A and B bothare identical so calculation the power of matrix is used by memcpy. A get copied into B. Afterwards A and B are partitioned into p square blocks amongst the processes. In the first communication step, the algorithm aligns the blocks of A and B in such a way that each process multiplies its local sub matrices. To align the matrices, Ai,j is shifted to the left by i steps while all Bi,j are all shifted up by j steps. After the alignment, each block calculates its own local product and local matrix ABi,j gets shifted to the left while local matrix Bi,j gets shifted up. A sequence of sqrt(p) are performed. The method implementing this formulation:<br/> 
float *performCannonOp(MPI_Comm *comm_new, float *A, float *B, int local_rank, int num_procs)

>- DNS Formulation
Cannon algorithm uses block 2-D partitioning of the input and output matrices anduses up to n2 processes for nxn matrices, the DNS algorithm can use up to n3 processes in time Θ(logn) by using Ω(p3/2) processes. In the DNS algorithm the processes are arranged in a three-dimensional n x n x n logical array.

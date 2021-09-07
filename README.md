# external-sort

This repo consists of implementation and test of extrenal sort algorithm:
- `generate_n_int_file` function in `external_sort.py` is to generate a file with N random 4-byte integers, `integers.txt` is a generated sample file 
- `ExternalSortOperator` class in `external_sort.py` is the actual implementation of the algorithm, it can be divided into 2 main parts:
  - `sort_chunks` method: split the large file into multiple small files that fits into in-memory sort (no more than M integers), then generate intermediate output small sorted files in the `tmp` folder
  - `heap_sort` method: using heap data structure to merge all the intermediate output small sorted files to get the final large sorted file `output.txt`
- `	if __name__ == '__main__':` entrance of the module, it generates a file with 10^4 integers, with a memory limit of 10^3 integers, performs the external sort algorithms, then validate if the output file is sorted correctly

Follow-up questions:
1. Suppose the program is likely to be I/O bound, to take advantage of this, we can use input buffer (when reading small intermediate fils) and output buffer (when writing to the final ouput file) to reduce the I/O time.
2. Parallelization across multiple cores in the same machine: 
3. Parallelization across multiple disks in the same machine:
4. Parallelization across multiple machines:
5. Choose M for different N, cores, spindles, and machines: 






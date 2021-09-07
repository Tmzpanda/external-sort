# external-sort

This repo consists of implementation and test of extrenal sort algorithm:
- `generate_n_int_file` function in `external_sort.py` is to generate a file with N random 4-byte integers, `integers.txt` is a generated sample file 
- `ExternalSortOperator` class in `external_sort.py` is the actual implementation of the algorithm, it can be divided into 2 main parts:
  - `sort_chunks` method: split the large file into multiple small files that fits into in-memory sort (no more than M integers), then generate intermediate output small sorted files in the `tmp` folder. Time complexity T = O(MlogM)
  - `heap_sort` method: using min heap data structure to merge all the intermediate output small sorted files to get the final large sorted file `output.txt`. Time complexity T = O(NlogK) where K = N/M
- `	if __name__ == '__main__':` entrance of the module, it generates a file with 10^4 integers, with a memory limit of 10^3 integers, performs the external sort algorithms, then validate if the output file is sorted correctly

Follow-up questions:
1. Suppose the program is likely to be I/O bound, to take advantage of this, we can use input buffer (when reading small intermediate fils) and output buffer (when writing to the final ouput file) to reduce the I/O time.
2. Parallelization across multiple cores in the same machine: small dataset in-memory sort (`sort_chunks` method in `ExternalSortOperator` class) can be parallized across multiple cores
3. Parallelization across multiple disks in the same machine: read large file into multiple small dataset in memory (`read_n_int` method in `ExternalSortOperator` class) can be parallized across multiple disks
4. Parallelization across multiple machines: aggegation to the final result (`heap_sort` method in `ExternalSortOperator` class) can be parallized across multiple machines by using pre-aggregation
5. Choose M for different N, cores, disks, and machines: dynamically to reduce the total time T = T(sort_chunks) + T(merge_k) + T(i/o)






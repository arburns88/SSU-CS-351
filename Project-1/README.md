# Project 1: Remote GitHub Development and Performance Monitoring

## Experimental Data Summary

| Configuration | alloca.out | list.out | malloc.out | new.out |
| :--- | :--- | :--- | :--- | :--- |
| **Experiment A (Unoptimized -g)** | 0.01 | 0.021 | 0.003 | 0.02 |
| **Experiment A (Optimized -O2)** | 0 | 0.008 | 0 | 0.004 |
| **Experiment B (Small Bytes)** | 0 | 0 | 0 | 0 |
| **Experiment B (Large Bytes)** | 0.144 | 0.148 | 0.147 | 0.144 |
| **Experiment C (Small Blocks)** | 0 | 0.004 | 0 | 0.006 |
| **Experiment C (Large Blocks)** | 0.186 | 0.283 | 0.211 | 0.287 |

---

## Analysis and Reporting


### 1. Which program is fastest? Is it always the fastest?
*Generally the alloca.out program ran fastest, however in the unoptimized test case the malloc.out program ran fastest.*

### 2. Which program is slowest? Is it always the slowest?
*The slowerst program was list.out, however there was an anomaly to this as well, with the long length test case new.out ran the longest.*

### 3. Was there a trend in program execution time based on the size of data in each Node? If so, what, and why?
*Yes, as the nodes got larger in size, the programs took more time hashing the data. This is reflected in the runtimes being very close as shown in Experiment B, because the processing bottleneck overpowers the memory alocation efficiency.*

### 4. Was there a trend in program execution time based on the length of the block chain?
*Yes, the execution times scaled with the addition of more nodes. This is a result of more allocation, initialization, hashing, etc. to do with each node addition*

### 5. Consider heap breaks, what's noticeable? Does increasing the stack size affect the heap? Speculate on any similarities and differences in programs?
*The programs list, new and malloc all trigger heap breaks, however alloca does not. This is because it uses stack memory. Increasing the stack size does not affect the heap. Thie biggest similarity is that list, new and malloc are all heap bound, whereas alloca uses the stack.*

### 6. Considering either the malloc.cpp or alloca.cpp versions of the program, generate a diagram showing two Nodes.
```text
[head] -> [ Node 1 ] -> [ Node 2 ] -> [ nullptr ]
            |             |
            +-> (6 bytes) +-> (data pointer)
```

### 7. There's an overhead to allocating memory, initializing it, and eventually processing (in our case, hashing it). For each program, were any of these tasks the same? Which one(s) were different?

*The initialization and processing phases were identical across all programs. It was the allocation step that was distinct for each program. Alloca allocates through the stack frame pointer via alloca(), malloc through the heap via malloc(), new requests memory via the new opereator, and finally list via the list container*

### 8. As the size of data in a Node increases, does the significance of allocating the node increase or decrease?

*The significance of the allocation method decreases with the increase of the data node size. As I briefly explained in 3, the processing bottleneck vastly overpowers the allocation efficiency, as shown by Experiment B.*
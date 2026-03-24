# Radix Stack Sorter

A high-performance integer sorting engine that operates on two stacks using a **chunk-based radix sort** algorithm, minimizing the total number of operations to achieve a fully sorted state.

## Overview

The algorithm partitions input integers into optimally-sized chunks based on dataset size, then uses a greedy rotation strategy — choosing between `ra`/`rb` rotations to minimize total moves. For small inputs (≤5), hand-optimized decision trees guarantee the theoretical minimum operation count.

## Algorithm

| Input Size | Strategy | Max Operations |
|------------|----------|---------------|
| n ≤ 3 | Hardcoded optimal | 2 |
| n ≤ 5 | Decision tree | 12 |
| n ≤ 100 | Chunk sort (≈5 chunks) | ~700 |
| n ≤ 500 | Chunk sort (≈11 chunks) | ~5500 |

**Core Operations**

| Op | Description |
|----|-------------|
| `sa` / `sb` | Swap top two elements |
| `pa` / `pb` | Push top element between stacks |
| `ra` / `rb` / `rr` | Rotate stack upward |
| `rra` / `rrb` / `rrr` | Reverse rotate stack downward |

## Features

- Integer overflow detection and input validation
- Duplicate detection with early error exit
- Linked-list based stack implementation
- Normalized index mapping for uniform distribution

## Build & Run

```bash
make
./push_swap 3 1 4 1 5 9 2 6 5 3
# outputs: sa\npb\nra\n...

# verify with checker
./push_swap 4 67 3 87 23 | ./checker 4 67 3 87 23
# OK
```

## Tech Stack

`C` `Makefile` `Linked Lists` `Stack Operations` `Radix Sort`


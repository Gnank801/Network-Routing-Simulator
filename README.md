
# Routing Protocols

**Course**: CS425 - Computer Networks 
**Instructor**: Adithya Vadapalli 
**TAs**: Rishit and Yugul 
**Submission Deadline**: 21.04.2025

---

## Team Members

| Name               | Roll Number |
|--------------------|-------------|
| Banoth Mithun Raj  | 210258      |
| Gude Rachana       | 210398      |
| Kinjarapu Gnan     | 210520      |

---

## Objective

This project involves simulating two fundamental routing algorithms:
- **Distance Vector Routing (DVR)**
- **Link State Routing (LSR)**

Both algorithms are implemented in C++ using an adjacency matrix input, representing the network topology. The program computes the shortest paths and displays the routing tables for each node accordingly.

---

## Files Included

- `routing_sim.cpp`: Main C++ implementation of the DVR and LSR algorithms.
- `input1.txt`, `input2.txt`, `input3.txt`, `input4.txt`: Sample input files containing adjacency matrices.
- `README.md`: This file.

---

## How to Compile and Run

### 1. **Compile**
```bash
g++ -o routing_sim routing_sim.cpp
```

### 2. **Run**
```bash
./routing_sim input1.txt
```

Replace `input1.txt` with any input file from the list.

---

## Input Format

Each input file contains:
- An integer `n` (number of nodes)
- An `n x n` adjacency matrix representing the cost between nodes

**Conventions:**
- `0` on the diagonal (self-loops)
- `9999` represents no direct connection (infinite cost)

---

## Sample Inputs & Outputs

### `input1.txt`
```
4
0 10 100 30
10 0 20 40
100 20 0 10
30 40 10 0
```

### Corresponding Output (Excerpt)
```
--- Distance Vector Routing Simulation ---
Node 0 Routing Table:
Dest	Cost	Next Hop
0	0	-
1	10	1
2	30	1
3	30	3
...

--- Link State Routing Simulation ---
Node 0 Routing Table:
Dest	Cost	Next Hop
1	10	1
2	30	1
3	30	3
...
```

---

## Implementation Details

### Distance Vector Routing (DVR)
- Based on **Bellman-Ford algorithm**
- Each node exchanges routing info with neighbors
- Updates continue until convergence (no more changes)
- Output: Routing tables after convergence

### Link State Routing (LSR)
- Based on **Dijkstra’s algorithm**
- Each node computes shortest paths using full topology
- Output: Final routing table per node

---

## Output Format

For both algorithms, each node's routing table is printed in the format:

```
Node <i> Routing Table:
Dest	Cost	Next Hop
<dest1>	<cost>	<next hop>
...
```

---

## Notes

- The program handles unreachable nodes (`9999`) appropriately.
- Tested with various topologies (`input1.txt` to `input4.txt`) to verify correctness.
- Makefile is optional; compilation via `g++` is direct.

---

## How to use the code in terminal and the outputs for different inputs
shannu@shannu:~$ cd Desktop/cs425-2025/Homeworks/A4/
shannu@shannu:~/Desktop/cs425-2025/Homeworks/A4$ g++ -o routing_sim routing_sim.cpp
shannu@shannu:~/Desktop/cs425-2025/Homeworks/A4$ ./routing_sim input1.txt

--- Distance Vector Routing Simulation ---
--- DVR Final Tables ---
Node 0 Routing Table:
Dest	Cost	Next Hop
0	0	-
1	10	1
2	30	1
3	30	3

Node 1 Routing Table:
Dest	Cost	Next Hop
0	10	0
1	0	-
2	20	2
3	30	2

Node 2 Routing Table:
Dest	Cost	Next Hop
0	30	1
1	20	1
2	0	-
3	10	3

Node 3 Routing Table:
Dest	Cost	Next Hop
0	30	0
1	30	2
2	10	2
3	0	-


--- Link State Routing Simulation ---
Node 0 Routing Table:
Dest	Cost	Next Hop
1	10	1
2	30	1
3	30	3

Node 1 Routing Table:
Dest	Cost	Next Hop
0	10	0
2	20	2
3	30	2

Node 2 Routing Table:
Dest	Cost	Next Hop
0	30	1
1	20	1
3	10	3

Node 3 Routing Table:
Dest	Cost	Next Hop
0	30	0
1	30	2
2	10	2

shannu@shannu:~/Desktop/cs425-2025/Homeworks/A4$ ./routing_sim input2.txt

--- Distance Vector Routing Simulation ---
--- DVR Final Tables ---
Node 0 Routing Table:
Dest	Cost	Next Hop
0	0	-
1	10	1
2	30	1
3	60	1
4	100	1

Node 1 Routing Table:
Dest	Cost	Next Hop
0	10	0
1	0	-
2	20	2
3	50	2
4	90	2

Node 2 Routing Table:
Dest	Cost	Next Hop
0	30	1
1	20	1
2	0	-
3	30	3
4	70	3

Node 3 Routing Table:
Dest	Cost	Next Hop
0	60	2
1	50	2
2	30	2
3	0	-
4	40	4

Node 4 Routing Table:
Dest	Cost	Next Hop
0	100	3
1	90	3
2	70	3
3	40	3
4	0	-


--- Link State Routing Simulation ---
Node 0 Routing Table:
Dest	Cost	Next Hop
1	10	1
2	30	1
3	60	1
4	100	1

Node 1 Routing Table:
Dest	Cost	Next Hop
0	10	0
2	20	2
3	50	2
4	90	2

Node 2 Routing Table:
Dest	Cost	Next Hop
0	30	1
1	20	1
3	30	3
4	70	3

Node 3 Routing Table:
Dest	Cost	Next Hop
0	60	2
1	50	2
2	30	2
4	40	4

Node 4 Routing Table:
Dest	Cost	Next Hop
0	100	3
1	90	3
2	70	3
3	40	3

shannu@shannu:~/Desktop/cs425-2025/Homeworks/A4$ ./routing_sim input3.txt

--- Distance Vector Routing Simulation ---
--- DVR Final Tables ---
Node 0 Routing Table:
Dest	Cost	Next Hop
0	0	-
1	5	1
2	10	2
3	15	3

Node 1 Routing Table:
Dest	Cost	Next Hop
0	5	0
1	0	-
2	7	2
3	19	2

Node 2 Routing Table:
Dest	Cost	Next Hop
0	10	0
1	7	1
2	0	-
3	12	3

Node 3 Routing Table:
Dest	Cost	Next Hop
0	15	0
1	19	2
2	12	2
3	0	-


--- Link State Routing Simulation ---
Node 0 Routing Table:
Dest	Cost	Next Hop
1	5	1
2	10	2
3	15	3

Node 1 Routing Table:
Dest	Cost	Next Hop
0	5	0
2	7	2
3	19	2

Node 2 Routing Table:
Dest	Cost	Next Hop
0	10	0
1	7	1
3	12	3

Node 3 Routing Table:
Dest	Cost	Next Hop
0	15	0
1	19	2
2	12	2

shannu@shannu:~/Desktop/cs425-2025/Homeworks/A4$ ./routing_sim input4.txt

--- Distance Vector Routing Simulation ---
--- DVR Final Tables ---
Node 0 Routing Table:
Dest	Cost	Next Hop
0	0	-
1	10	1
2	15	1
3	17	1
4	20	1

Node 1 Routing Table:
Dest	Cost	Next Hop
0	10	0
1	0	-
2	5	2
3	7	2
4	10	2

Node 2 Routing Table:
Dest	Cost	Next Hop
0	15	1
1	5	1
2	0	-
3	2	3
4	5	3

Node 3 Routing Table:
Dest	Cost	Next Hop
0	17	2
1	7	2
2	2	2
3	0	-
4	3	4

Node 4 Routing Table:
Dest	Cost	Next Hop
0	20	3
1	10	3
2	5	3
3	3	3
4	0	-


--- Link State Routing Simulation ---
Node 0 Routing Table:
Dest	Cost	Next Hop
1	10	1
2	15	1
3	17	1
4	20	1

Node 1 Routing Table:
Dest	Cost	Next Hop
0	10	0
2	5	2
3	7	2
4	10	2

Node 2 Routing Table:
Dest	Cost	Next Hop
0	15	1
1	5	1
3	2	3
4	5	3

Node 3 Routing Table:
Dest	Cost	Next Hop
0	17	2
1	7	2
2	2	2
4	3	4

Node 4 Routing Table:
Dest	Cost	Next Hop
0	20	3
1	10	3
2	5	3
3	3	3

shannu@shannu:~/Desktop/cs425-2025/Homeworks/A4$

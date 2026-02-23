# Analysis and Design of Algorithms - Assignment 2024

This repository contains the solutions and algorithmic analysis for the 2024 assignment in **Analysis and Design of Algorithms (ADA)**. The problems focus on graph theory, greedy strategies, and dynamic programming.

## 📝 Problem 1: Graphs and Fuel Capacity

### 1.1 Connectivity Analysis (Reachability)
* **Objective:** Determine if a route exists from city $s$ to city $t$ given a fuel capacity $L$.
* **Algorithm:** **Depth-First Search (DFS)**. 
* **Methodology:** A graph $G=(V, E)$ is constructed where edges $(u, v)$ exist only if the distance $w(u, v) \leq L$. Starting from city $s$, DFS explores all reachable nodes. If the discovery time $f[t]$ indicates $t$ was visited during the traversal starting from $s$, the route is feasible.
* **Complexity:** $O(|V| + |E|)$, as the modification only involves a constant-time check.



### 1.2 Minimum Fuel Capacity (Dijkstra Modification)
* **Objective:** Find the minimum fuel capacity $L_{min}$ required to travel from $s$ to $t$.
* **Algorithm:** Modified **Dijkstra** using a **Binary Heap**.
* **Methodology:** Instead of minimizing the total sum of edge weights, the algorithm minimizes the maximum weight edge on the path. The distance update rule becomes: $dist[v] = \min(dist[v], \max(dist[u], w(u, v)))$.
* **Complexity:** $O((|V| + |E|) \log |V|)$ using a binary heap for priority queue operations.

---

## 🕒 Problem 2: Queue Optimization (Waiting Time)

### Greedy Strategy for Scheduling
* **Objective:** Minimize the total waiting time for $n$ citizens with known service times $st_i$.
* **Algorithm:** **Greedy Scheduling (Shortest Processing Time First)**.
* **Methodology:** 1.  Sort citizens in non-decreasing order of their service times $st_i$.
    2.  Serve the citizen with the smallest $st_i$ first.
* **Proof Sketch:** Any sequence not sorted by $st_i$ can be improved by swapping two adjacent elements that are out of order, which reduces the waiting time of the second element and all subsequent elements.
* **Pseudocode:**
    ```text
    Greedy_queue(ST):
      sort(ST) // Increasing order
      total_waiting_time = 0
      current_wait = 0
      for i from 1 to n-1:
        current_wait += ST[i]
        total_waiting_time += current_wait
      return total_waiting_time
    ```
* **Complexity:** $O(n \log n)$ due to the sorting step.



---

## 🧩 Problem 3: String Splitting (Dynamic Programming)

### Optimal String Cut
* **Objective:** Find the minimum cost to split a string of length $n$ at $m$ specific points.
* **Algorithm:** **Dynamic Programming (DP)**.
* **Methodology:**
    * Define $D[i][j]$ as the minimum cost to perform all cuts between indices $T[i]$ and $T[j]$.
    * **Recurrence Relation:** $D[i][j] = (T[j] - T[i]) + \min_{i < k < j} \{ D[i][k] + D[k][j] \}$.
    * Base cases: $D[i][i+1] = 0$ (no cuts possible between adjacent points).
* **Optimization Features:** * **Optimal Substructure:** Larger problems are solved using previously computed optimal solutions of smaller intervals.
    * **Overlapping Subproblems:** Results are stored in a table $D$ to avoid redundant calculations.
* **Pseudocode:**
    ```text
    for length from 2 to m:
      for i from 0 to m - length:
        j = i + length
        D[i][j] = infinity
        for k from i + 1 to j - 1:
          cost = (T[j] - T[i]) + D[i][k] + D[k][j]
          D[i][j] = min(D[i][j], cost)
    ```
* **Complexity:** $O(m^3)$, where $m$ is the number of cuts.



---

## 🛠 Technologies Used
* **Algorithm Design:** Greedy, Dynamic Programming, Graph Theory (DFS, Dijkstra).
* **Complexity Analysis:** Big O Notation.
* **Pseudocode Representation.**

## 📂 Repository Content
* 📄 `ADA_Assignment_2024.pdf`: The complete technical report containing analytical solutions, proofs, and pseudocode for all problems.

---
*Developed as part of the "Analysis and Design of Algorithms" course at the Electrical and Computer Engineering Department, AUTh.*

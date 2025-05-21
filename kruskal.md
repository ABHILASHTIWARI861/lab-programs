# Kruskal's Algorithm in C

This program implements Kruskal's Algorithm to find the Minimum Spanning Tree (MST) of a given graph using its cost adjacency matrix.

## 🧾 Code

```c
#include <stdio.h>
#include <stdlib.h>

int i, j, k, a, b, u, v, n, ne = 1;
int min_cost = 0, min, parent[9], cost[9][9];

int find(int i) {
    while (parent[i]) {
        i = parent[i];
    }
    return i;
}

int uni(int i, int j) {
    if (i != j) {
        parent[j] = i;
        return 1;
    }
    return 0;
}

int main() {
    printf("Enter the number of vertices: ");
    scanf("%d", &n);

    printf("Enter the cost adjacency matrix:\n");
    for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= n; j++) {
            scanf("%d", &cost[i][j]);
            if (cost[i][j] == 0) {
                cost[i][j] = 999;
            }
        }
    }

    printf("\nThe edges of the Minimum Spanning Tree are:\n");
    while (ne < n) {
        min = 999;
        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= n; j++) {
                if (cost[i][j] < min) {
                    min = cost[i][j];
                    a = u = i;
                    b = v = j;
                }
            }
        }

        u = find(u);
        v = find(v);

        if (uni(u, v)) {
            printf("\n%d edge (%d --> %d): %d", ne++, a, b, min);
            min_cost += min;
        }

        cost[a][b] = cost[b][a] = 999;
    }

    printf("\nCost of Minimum Spanning Tree = %d\n", min_cost);
    return 0;
}


output

Enter the number of vertices: 4
Enter the cost adjacency matrix:
0 20 10 50
20 0 60 999
10 60 0 40
50 999 40 0

The edges of the Minimum Spanning Tree are:

1 edge (1 --> 3): 10
2 edge (1 --> 2): 20
3 edge (3 --> 4): 40
Cost of Minimum Spanning Tree = 70
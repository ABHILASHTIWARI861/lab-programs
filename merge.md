#include <stdio.h>
#include <stdlib.h>
#include <time.h>

void Merge(int a[], int low, int mid, int high) {
    int i = low, j = mid + 1, k = low;
    int b[2000]; // ensure b is large enough

    while (i <= mid && j <= high) {
        if (a[i] <= a[j])
            b[k++] = a[i++];
        else
            b[k++] = a[j++];
    }

    while (i <= mid)
        b[k++] = a[i++];
    while (j <= high)
        b[k++] = a[j++];

    for (k = low; k <= high; k++)
        a[k] = b[k];
}

void MergeSort(int a[], int low, int high) {
    if (low >= high)
        return;

    int mid = (low + high) / 2;
    MergeSort(a, low, mid);
    MergeSort(a, mid + 1, high);
    Merge(a, low, mid, high);
}

int main() {
    int n, a[2000];
    clock_t st, et;
    double ts;

    printf("Enter how many numbers: ");
    scanf("%d", &n);

    srand(time(NULL)); // Seed for random number generation

    printf("The random numbers are:\n");
    for (int k = 0; k < n; k++) {
        a[k] = rand();
        printf("%d\t", a[k]);
    }

    st = clock();
    MergeSort(a, 0, n - 1);
    et = clock();
    ts = (double)(et - st) / CLOCKS_PER_SEC;

    printf("\nSorted numbers are:\n");
    for (int k = 0; k < n; k++) {
        printf("%d\t", a[k]);
    }

    printf("\nThe time taken is %e seconds\n", ts);

    return 0;
}

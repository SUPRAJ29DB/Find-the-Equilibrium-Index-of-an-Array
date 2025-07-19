# Find-the-Equilibrium-Index-of-an-Array
An equilibrium index in an array is a position such that:  The sum of all elements to the left of that index is equal to the sum of all elements to the right of that index.
# Find-the-Equilibrium-Index-of-an-Array

An **equilibrium index** in an array is a position such that:

> The sum of all elements to the **left** of that index is equal to the sum of all elements to the **right** of that index.

---

 Example:
For the array: `{ -7, 1, 5, 2, -4, 3, 0 }`

- At index 3:
  - Left sum = -7 + 1 + 5 = -1
  - Right sum = -4 + 3 + 0 = -1 ✅

So, index `3` is an equilibrium index.

---

 Logic:

- Compute the total sum of the array.
- Traverse the array while keeping track of the left sum.
- At each index `i`, the right sum is:
  ```
  total sum - left sum - arr[i]
  ```
- If left sum == right sum → equilibrium found.

---

 C Code (No function used):


#include <stdio.h>

int main() {
    int m, i, total = 0, leftsum = 0;
    printf("Enter size: ");
    scanf("%d", &m);
    int arr[m];

    // Input array
    printf("Enter elements:\n");
    for (i = 0; i < m; i++) {
        scanf("%d", &arr[i]);
        total += arr[i];  // calculate total sum during input
    }

    // Find equilibrium index
    for (i = 0; i < m; i++) {
        total -= arr[i];  // total now becomes right sum

        if (leftsum == total) {
            printf("Equilibrium index is: %d\n", i);
            return 0;
        }

        leftsum += arr[i];  // update left sum
    }

    printf("No equilibrium index found.\n");
    return 0;
}


---

Notes:
- This program returns the **first equilibrium index** it finds.
- If none exists, it outputs a message accordingly.


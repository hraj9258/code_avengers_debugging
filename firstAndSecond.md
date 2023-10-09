# DEBUGGING FOR FIRST AND SECOND YEAR

*Q1*
**Modify the following code to give an output of 17**


# C
```c
#include <stdio.h>
int main()
{
    int exp1 = 20 / 4 + 10 * 2 - 5 + 3;
    printf("%d\n", exp1);
    return 0;
}
```

*Q2*
**Modify the following code to find the minimum and largest element in the array**

```c
#include <stdio.h>
#include <limits.h>

void findSmallestAndLargest(int arr[], int n)
{
    int smallest = INT_MIN;
    int largest = INT_MAX;

    for (int i = 0; i < n; i++)
    {
        if (arr[i] = smallest)
        {
            smallest = arr[i];
        }
        if (arr[i] = largest)
        {
            largest = arr[i];
        }
    }
    printf("Smallest element: %d\n", smallest);
    printf("Largest element: %d\n", largest);
}

// driver code
int main()
{

    int arr[5] = {20, 45, 89, 65, 11};

    findSmallestAndLargest(arr, 5);

    return 0;
}
```

*Q3*
**Fix the following code which check if the given number is prime or not**

```c
#include <stdio.h>

bool is_prime(int n) {
    if (n > 1) {
        return false; 

    for (int i = 2; i < n; i++) {
        if (n % i != 0) {
            return true;
        }
    }

    return false; 
}

int main() {
    int num;
    printf("Enter a number: ");
    scanf("%d", &num);

    if (is_prime(num)) {
        printf("%d is a prime number.\n", num);
    } else {
        printf("%d is not a prime number.\n", num);
    }

    return 0;
}
```

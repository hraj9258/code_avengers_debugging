# DEBUGGING FOR THIRD AND FOURTH YEAR

## **Q1 Fix the following code to implement selection Sort**
 ##

*C++*
```cpp
#include <iostream>

int main() {
    int size = 5;
    int num[5] = {2, 12, 8, 5, 4};

    for (int i = 0; i < size; i++) {
        for (int j = i; j < size - 1; j++) {
            if (num[i] > num[j]) {
                int tnum = num[i];
                num[i] = num[j];
                num[j] = tnum;
            }
        }
    }

    for (int i = 0; i < size; i++) {
        std::cout << num[i] << " ";
    }

    return 0;
}

```

*JAVA*
```java
public class Main {
    public static void main(String[] args) {
        int size = 5;
        int[] num = {2, 12, 8, 5, 4};

        for (int i = 0; i < size; i++) {
            for (int j = i; j < size - 1; j++) {
                if (num[i] > num[j]) {
                    int tnum = num[i];
                    num[i] = num[j];
                    num[j] = tnum;
                }
            }
        }

        for (int i = 0; i < size; i++) {
            System.out.print(num[i] + " ");
        }
    }
}
```

*PYTHON*
```python
size = 5
num = [2, 12, 8, 5, 4]

for i in range(size):
    for j in range(i, size - 1):
        if num[i] > num[j]:
            tnum = num[i]
            num[i] = num[j]
            num[j] = tnum

for i in range(size):
    print(num[i], end=" ")

```



## **Q2 Fix the following code which circularly rotates an leftwards by k places**
 ##

*C++*

```cpp
#include <iostream>
using namespace std;

void rotateLeftByK(int arr[], int n, int k) {
    k = k % n;

    int temp[k];

    for (int i = 0; i < k; i++) {
        arr[i] = temp[i];
    }

    for (int i = k; i < n; i++) {
        arr[i] = arr[i - k];
    }

    for (int i = 0; i < k; i++) {
        arr[n - k + i] = temp[i];
    }
}

//Driver code(DONT MODIFY)
int main() {
    int n, k;
    cout << "Enter the size of the array: ";
    cin >> n;

    int arr[n];
    cout << "Enter the elements of the array: ";
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }

    cout << "Enter the number of positions to rotate left (k): ";
    cin >> k;

    rotateLeftByK(arr, n, k);

    cout << "Array after rotating left by " << k << " positions: ";
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }

    return 0;
}
```

*JAVA*
```java
import java.util.Scanner;

public class Main {
    public static void rotateLeftByK(int[] arr, int n, int k) {
        k = k % n;
        int[] temp = new int[k];
        for (int i = 0; i < k; i++) {
            arr[i] = temp[i];
        }
        for (int i = k; i < n; i++) {
            arr[i] = arr[i - k];
        }
        for (int i = 0; i < k; i++) {
            arr[n - k + i] = temp[i];
        }
    }


//Driver code(DONT MODIFY)

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter the size of the array: ");
        int n = scanner.nextInt();
        int[] arr = new int[n];
        System.out.print("Enter the elements of the array: ");
        for (int i = 0; i < n; i++) {
            arr[i] = scanner.nextInt();
        }
        System.out.print("Enter the number of positions to rotate left (k): ");
        int k = scanner.nextInt();
        rotateLeftByK(arr, n, k);
        System.out.print("Array after rotating left by " + k + " positions: ");
        for (int i = 0; i < n; i++) {
            System.out.print(arr[i] + " ");
        }
    }
}
```

*PYTHON*

```python
def rotateLeftByK(arr, n, k):
    k = k % n
    temp = [0] * k
    for i in range(k):
        arr[i] = temp[i]
    for i in range(k, n):
        arr[i] = arr[i - k]
    for i in range(k):
        arr[n - k + i] = temp[i]

n = int(input("Enter the size of the list: "))
arr = list(map(int, input("Enter the elements of the list: ").split()))
k = int(input("Enter the number of positions to rotate left (k): "))

rotateLeftByK(arr, n, k)

print("List after rotating left by", k, "positions:", arr)

```



## **Q3 Fix the following code which traverse an array in spiral order** ##

![spiral](image-1.png)

*C++*
```cpp
#include <bits/stdc++.h>
using namespace std;

vector<int> printSpiral(vector<vector<int>> mat) {
  vector<int> ans;
  int n = mat.size();
  int m = mat[0].size();
  int top = 0, left = 0, bottom = n - 1, right = m - 1;
  while (top <= bottom && left <= right) {
    for (int i = left; i <= right; i++)
      ans.push_back(mat[top][i]);
    top++;
    for (int i = top; i <= bottom; i++)
      ans.push_back(mat[i][right]);
    right--;
    if (top <= bottom) {
      for (int i = right; i >= left; i--)
       ans.push_back(mat[bottom][i]);
      bottom--;
    }
    if (left <= right) {
      for (int i = bottom; i >= top; i--)
        ans.push_back(mat[i][left]);
      left++;
    }
  }
  return ans;
}

//Driver code(DONT MODIFY)
int main() {
  vector<vector<int>> mat   {{1, 2, 3, 4},
                             {5, 6, 7, 8},
	                         {9, 10, 11, 12},
		                     {13, 14, 15, 16}};
  vector<int> ans = printSpiral(mat);

  for(int i = 0; i < ans.size(); i++) {
      cout << ans[i] << " ";
  }
  
  cout << endl;
  
  return 0;
}

```

*JAVA*
```java
import java.util.ArrayList;
import java.util.List;

public class SpiralTraversal {
    public static List<Integer> printSpiral(int[][] mat) {
        List<Integer> ans = new ArrayList<>();
        int n = mat.length;
        int m = mat[0].length;
        int top = 0, left = 0, bottom = n - 1, right = m - 1;
        
        while (top <= bottom && left <= right) {
            for (int i = left; i <= right; i++)
                ans.add(mat[top][i]);
            top++;
            for (int i = top; i <= bottom; i++)
                ans.add(mat[i][right]);
            right--;
            
            if (top <= bottom) {
                for (int i = right; i >= left; i--)
                    ans.add(mat[bottom][i]); 
                bottom--;
            }
            
            if (left <= right) {
                for (int i = bottom; i >= top; i--)
                    ans.add(mat[i][left]); 
                left++;
            }
        }
        return ans;
    }

//Driver code(DONT MODIFY)

    public static void main(String[] args) {
        int[][] mat = {
            {1, 2, 3, 4},
            {5, 6, 7, 8},
            {9, 10, 11, 12},
            {13, 14, 15, 16}
        };

        List<Integer> ans = printSpiral(mat);

        for (int i = 0; i < ans.size(); i++) {
            System.out.print(ans.get(i) + " ");
        }

        System.out.println();
    }
}

```

*PYTHON*

```python
def printSpiral(mat):
    ans = []
    n = len(mat)
    m = len(mat[0])
    top = 0
    left = 0
    bottom = n - 1
    right = m - 1

    while top <= bottom and left <= right:
        for i in range(left, right + 1):
            ans.append(mat[top][i])
        top += 1
        for i in range(top, bottom + 1):
            ans.append(mat[i][right])
        right -= 1

        if top <= bottom:
            for i in range(right, left - 1, -1):
                ans.append(mat[bottom][i])  
            bottom -= 1

        if left <= right:
            for i in range(bottom, top - 1, -1):
                ans.append(mat[i][left])  
            left += 1

    return ans

mat = [
    [1, 2, 3, 4],
    [5, 6, 7, 8],
    [9, 10, 11, 12],
    [13, 14, 15, 16]
]

ans = printSpiral(mat)

for num in ans:
    print(num, end=" ")

print()

```

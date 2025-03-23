## find the floor and ceiling in sorted array. (c++)

Given an sorted array arr[] of integers and an integer x, find the floor and ceiling of x in arr[].

Floor of x is the largest element which is smaller than or equal to x. Floor of x doesn’t exist if x is smaller than smallest element of arr[].

Ceil of x is the smallest element which is greater than or equal to x. Ceil of x doesn’t exist if x is greater than greatest element of arr[].

Return an array of integers denoting the [floor, ceil]. Return -1 for floor or ceiling if the floor or ceiling is not present.
## Example
Input Format: n = 6, arr[] ={3, 4, 4, 7, 8, 10}, x= 5

Result: 4 7

Explanation: The floor of 5 in the array is 4, and the ceiling of 5 in the array is 7.

## PROGRAM:(Main.cpp)
```
#include <bits/stdc++.h>
using namespace std;

int findFloor(int arr[], int n, int x)
{
    int low = 0, high = n - 1;
    int ans = -1;  

    while (low <= high)
    {
        int mid = (low + high) / 2;

        if (arr[mid] <= x)
        {
            ans = arr[mid];  
            low = mid + 1;   
        }
        else
        {
            high = mid - 1;  
        }
    }
    return ans;
}

int findCeil(int arr[], int n, int x)
{
    int low = 0, high = n - 1;
    int ans = -1;  

    while (low <= high)
    {
        int mid = (low + high) / 2;

        if (arr[mid] >= x)
        {
            ans = arr[mid];  
            high = mid - 1;  
        }
        else
        {
            low = mid + 1;   
        }
    }
    return ans;
}

pair<int, int> getFloorAndCeil(int arr[], int n, int x)
{
    int f = findFloor(arr, n, x);
    int c = findCeil(arr, n, x);
    return make_pair(f, c);  
}


```
## Complexity
- Time complexity : O(N)

- Space complexity : O(1)

## OUTPUT
Output: 4,7

## Floor in a Sorted Array (c++)

Given a sorted array arr[] and an integer x, find the index (0-based) of the largest element in arr[] that is less than or equal to x. This element is called the floor of x. If such an element does not exist, return -1.

Note: In case of multiple occurrences of ceil of x, return the index of the last occurrence.
## Example
Input: arr[] = [1, 2, 8, 10, 10, 12, 19], x = 5

Output: 1

Explanation: Largest number less than or equal to 5 is 2, whose index is 1.

## PROGRAM:(Main.cpp)
```
class Solution {
  public:

    int findFloor(vector<int>& arr, int x) {
        int n=arr.size();
        int l=0;
        int r=n-1;
        int ans=-1;
        while(l<=r)
        {
            int mid=(l+r)/2;
            if(arr[mid]<=x) 
            {
                ans=mid;
                l=mid+1;
            }
            else r=mid-1;
        }
        return ans;
    }
};
```
## Complexity
- Time complexity : O(logN)

- Space complexity : O(1)

## OUTPUT
Output: 1

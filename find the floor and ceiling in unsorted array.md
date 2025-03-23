## find the floor and ceiling in unsorted array. (c++)

Given an unsorted array arr[] of integers and an integer x, find the floor and ceiling of x in arr[].

Floor of x is the largest element which is smaller than or equal to x. Floor of x doesn’t exist if x is smaller than smallest element of arr[].

Ceil of x is the smallest element which is greater than or equal to x. Ceil of x doesn’t exist if x is greater than greatest element of arr[].

Return an array of integers denoting the [floor, ceil]. Return -1 for floor or ceiling if the floor or ceiling is not present.
## Example
Input: x = 7 , arr[] = [5, 6, 8, 9, 6, 5, 5, 6]

Output: 6, 8

Explanation: Floor of 7 is 6 and ceil of 7 is 8.

## PROGRAM:(Main.cpp)
```
class Solution {
  public:
    vector<int> getFloorAndCeil(int x, vector<int> &arr) 
    {
        int n=arr.size();
        int flooor=INT_MIN;
        int ceiil=INT_MAX;
     
        for(int i=0;i<n;i++)
        {
            if(arr[i]<=x && flooor<arr[i])
            {
                flooor=arr[i];
            }
            if(arr[i]>=x && ceiil>arr[i])
            {
                ceiil=arr[i];
            }
        }
        if(flooor==INT_MIN) flooor=-1;
        if(ceiil==INT_MAX) ceiil=-1;
        return {flooor,ceiil};
    }
};
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(1)

## OUTPUT
Output: 6,8

## Kth Missing Positive Number (c++)

Given an array arr of positive integers sorted in a strictly increasing order, and an integer k.

Return the kth positive integer that is missing from this array.
## Example
Input: arr = [2,3,4,7,11], k = 5

Output: 9

Explanation: The missing positive integers are [1,5,6,8,9,10,12,13,...]. The 5th missing positive integer is 9.

## PROGRAM:(Main.cpp)
```
class Solution {
public:
    int findKthPositive(vector<int>& arr, int k) 
    {
        int n=arr.size();
        int l=0, h=n-1;

        while(l<=h)
        {
            int mid=(l+h)/2;

            int missing = arr[mid] - (mid + 1);
            if(missing <k) 
            {
                l=mid+1;
            }
            else 
            {
                h=mid-1;
            }
        }
        return l+k;
    }
};
```
## Complexity
- Time complexity : O(logN)

- Space complexity : O(1)

## OUTPUT
Output: 9

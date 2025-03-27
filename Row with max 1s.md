## Row with max 1s (c++)

You are given a 2D binary array arr[][] consisting of only 1s and 0s. Each row of the array is sorted in non-decreasing order. Your task is to find and return the index of the first row that contains the maximum number of 1s. If no such row exists, return -1.

Note:

The array follows 0-based indexing.
The number of rows and columns in the array are denoted by n and m respectively.

## Example
Input: arr[][] = [[0,1,1,1], [0,0,1,1], [1,1,1,1], [0,0,0,0]]

Output: 2

Explanation: Row 2 contains the most number of 1s (4 1s). Hence, the output is 2.

## PROGRAM:(Main.cpp)
```
class Solution {
  public:
    int lowerbound(vector<int>&arr,int m,int k)
    {
        int ans=m,l=0,h=m-1;
        while(l<=h)
        {
            int mid=(l+h)/2;
            if(arr[mid]>=k)
            {
                ans=mid;
                h=mid-1;
            }
            else
            {
                l=mid+1;
            }
        }
        return ans;
    }
    int rowWithMax1s(vector<vector<int>> &arr) 
    {
        int n=arr.size();
        int m=arr[0].size();
        int cnt_max=0;
        int index=-1;
        for(int i=0;i<n;i++)
        {
            int cnt_ones=m-lowerbound(arr[i],m,1);
            if(cnt_ones>cnt_max)
            {
                cnt_max=cnt_ones;
                index=i;
            }
        }
        return index;
    }
};
```
## Complexity
- Time complexity : O(N * log M)

- Space complexity : O(1)

## OUTPUT
Output: 2

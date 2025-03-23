## Ceil or Lower bound (c++)

Implement Lower Bound or Ceil.
## Example
Input: arr[] = [1, 2, 8, 10, 10, 12, 19], x = 5

Output: 2

## PROGRAM:(Main.cpp)
```
class Solution {
  public:

    int findceil(vector<int>& arr, int x) {
        int n=arr.size();
        int l=0;
        int r=n-1;
        int ans=-1;
        while(l<=r)
        {
            int mid=(l+r)/2;
            if(arr[mid]>=x) 
            {
                ans=mid;
                r=mid-1;
            }
            else l=mid+1;
        }
        return ans;
    }
};
```
## Complexity
- Time complexity : O(logN)

- Space complexity : O(1)

## OUTPUT
Output: 2

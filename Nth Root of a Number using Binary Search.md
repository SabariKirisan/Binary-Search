## Nth Root of a Number using Binary Search (c++)

You are given 2 numbers n and m, the task is to find n√m (nth root of m). If the root is not integer then returns -1.
## Example
Input: n = 2, m = 9

Output: 3

Explanation: 32 = 9

## PROGRAM:(Main.cpp)
```
class Solution {
  public:
    int fun(int mid,int n,int m)
    {
        int ans=1;
        for(int i=0;i<n;i++)
        {
            ans=ans*mid;
        }
        if(ans==m) return 1;
        else if(ans>m) return 2;
        else return 0;
    }
    int nthRoot(int n, int m) {
        int l=0,r=m;
        
        while(l<=r)
        {
            int mid=(l+r)/2;
            int midf=fun(mid,n,m);
            
            if(midf==1) return mid;
            else if(midf==2) r=mid-1;
            else l=mid+1;
        }
        return -1;
    }
};
```
## Complexity
- Time complexity : O(logN)

- Space complexity : O(1)

## OUTPUT
Output: 3

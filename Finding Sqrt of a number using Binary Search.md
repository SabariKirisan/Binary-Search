## Finding Sqrt of a number using Binary Search (c++)

Given a positive integer n, find the square root of n. If n is not a perfect square, then return the floor value.

Floor value of any number is the greatest Integer which is less than or equal to that number
## Example
Input: n = 4

Output: 2

Explanation: Since, 4 is a perfect square, so its square root is 2.

## PROGRAM:(Main.cpp)
```
class Solution {
  public:
    int floorSqrt(int n) 
    {
        int l=0,r=n;
        while(l<=r)
        {
            long long mid=(l+r)/2;
            long long val=mid*mid;
            
            if(val<=n)
            {
                l=mid+1;
            }
            else
            {
                r=mid-1;
            }
        }
        return r;
    }
};
```
## Complexity
- Time complexity : O(logN)

- Space complexity : O(1)

## OUTPUT
Output: 2

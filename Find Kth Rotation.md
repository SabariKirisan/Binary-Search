## Find out how many times the array has been rotated  (c++)

Given an increasing sorted rotated array arr of distinct integers. The array is right-rotated k times. Find the value of k.

Let's suppose we have an array arr = [2, 4, 6, 9], so if we rotate it by 2 times so that it will look like this:

After 1st Rotation : [9, 2, 4, 6]

After 2nd Rotation : [6, 9, 2, 4]
## Example
Input: arr = [5, 1, 2, 3, 4]

Output: 1

Explanation: The given array is 5 1 2 3 4. The original sorted array is 1 2 3 4 5. We can see that the array was rotated 1 times to the right.

## PROGRAM:(Main.cpp)
```
class Solution {
  public:
    int findKRotation(vector<int> &arr) 
    {
        int n=arr.size();
        int l=0,r=n-1;
        int index=-1;
        
        while(l<=r)
        {
            int mid=(l+r)/2;
            
            if(arr[l]<=arr[r]) 
            {
                return l;
            }
            if(arr[l]<=arr[mid]) 
            {
                index=l;
                l=mid+1;
            }
            else 
            {
                index=mid;
                r=mid;
            }
        }
        return index;
    }
};
```
## Complexity
- Time complexity : O(logN) 

- Space complexity : O(1)

## OUTPUT
Output: 1

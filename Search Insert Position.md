## Search Insert Position (c++)

Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You must write an algorithm with O(log n) runtime complexity.
## Example
Input: nums = [1,3,5,6], target = 5

Output: 2

## PROGRAM:(Main.cpp)
```
class Solution {
public:
    int searchInsert(vector<int>& nums, int target) 
    {
        int n=nums.size();
        int l=0;
        int r=n-1;
        while(l<=r)
        {
            int mid=(l+r)/2;
            if(nums[mid]>=target)
            {
                r=mid-1;
            }
            else l=mid+1;
        }
        return l;
    }
};
```
## Complexity
- Time complexity : O(logN)

- Space complexity : O(1)

## OUTPUT
Output: 2

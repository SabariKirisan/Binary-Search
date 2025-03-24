## Search in Rotated Sorted array ||  (c++)

There is an integer array nums sorted in non-decreasing order (not necessarily with distinct values).

Before being passed to your function, nums is rotated at an unknown pivot index k (0 <= k < nums.length) such that the resulting array is [nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]] (0-indexed). For example, [0,1,2,4,4,4,5,6,6,7] might be rotated at pivot index 5 and become [4,5,6,6,7,0,1,2,4,4].

Given the array nums after the rotation and an integer target, return true if target is in nums, or false if it is not in nums.

You must decrease the overall operation steps as much as possible.
## Example
Input: nums = [2,5,6,0,0,1,2], target = 0

Output: true

## PROGRAM:(Main.cpp)
```
class Solution {
public:
    bool search(vector<int>& nums, int target) 
    {
        int n=nums.size();
        int l=0,r=n-1;

        while(l<=r)
        {
            int mid=(l+r)/2;

            if(nums[mid]==target) return true;
            if(nums[l]==nums[mid] && nums[mid]==nums[r])
            {
                l++;
                r--;
                continue;
            }

            if(nums[l]<=nums[mid])
            {
                if(nums[l]<=target && target<=nums[mid])
                {
                    r=mid-1;
                }
                else
                {
                    l=mid+1;
                }
            }
            else
            {
                if(nums[mid]<=target && target<=nums[r])
                {
                    l=mid+1;
                }
                else
                {
                    r=mid-1;
                }
            }
        }
        return false;     
    }
};
```
## Complexity
- Time complexity : O(logN) - Best case || O(n) - Worst case

- Space complexity : O(1)

## OUTPUT
Output: true

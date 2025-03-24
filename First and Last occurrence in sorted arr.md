## First and Last occurrence in sorted arr (c++)

Given an array of integers nums sorted in non-decreasing order, find the starting and ending position of a given target value.

If target is not found in the array, return [-1, -1].

You must write an algorithm with O(log n) runtime complexity.
## Example
Input: nums = [5,7,7,8,8,10], target = 8

Output: [3,4]

## PROGRAM:(Main.cpp)
```
class Solution {
public:
    int first(vector<int>&nums,int target,int n)
    {
        int l=0,r=n-1;
        int first=-1;
        while(l<=r)
        {
            int mid=(l+r)/2;

            if(target==nums[mid])
            {
                first=mid;
                r=mid-1;
            }
            else if(target<nums[mid]) r=mid-1;
            else l=mid+1;
        }
        return first;
    }
    int last(vector<int> &nums,int target,int n)
    {
        int l=0,r=n-1;
        int last=-1;
        while(l<=r)
        {
            int mid=(l+r)/2;
            if(nums[mid]==target)
            {
                last=mid;
                l=mid+1;
            }
            else if(target<nums[mid]) r=mid-1;
            else l=mid+1;
        }
        return last;
    }
    vector<int> searchRange(vector<int>& nums, int target) 
    {
      int n=nums.size();
      int f=first(nums,target,n);
      if(f == -1) return {-1,-1};
      int l=last(nums,target,n);
      return {f,l};

        
    }
};
```
## Complexity
- Time complexity : O(logN)

- Space complexity : O(1)

## OUTPUT
Output: [3,4]

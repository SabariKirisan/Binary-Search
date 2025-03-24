## Search Single Element in a sorted array (c++)

You are given a sorted array consisting of only integers where every element appears exactly twice, except for one element which appears exactly once.

Return the single element that appears only once.

Your solution must run in O(log n) time and O(1) space.
## Example
Input: nums = [1,1,2,3,3,4,4,8,8]

Output: 2

## PROGRAM:(Main.cpp)
```
class Solution {
public:
    int singleNonDuplicate(vector<int>& nums) 
    {
        int n=nums.size();

        if(n==1) return nums[0];
        if(nums[1]!=nums[0]) return nums[0];
        if(nums[n-1]!=nums[n-2]) return nums[n-1];

        int l=1,r=n-2;
        while(l<=r)
        {
            int mid=(l+r)/2;

            if(nums[mid-1]!=nums[mid] && nums[mid]!=nums[mid+1]) return nums[mid];

            if((mid%2==1 && nums[mid-1]==nums[mid]) || (mid%2==0 && nums[mid]==nums[mid+1])) l=mid+1;
            else r=mid-1;
        }
        return -1;
    }
};
```
## Complexity
- Time complexity : O(logN) 

- Space complexity : O(1)

## OUTPUT
Output: 2

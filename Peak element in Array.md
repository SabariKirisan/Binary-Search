## Peak element in Array (c++)

A peak element is an element that is strictly greater than its neighbors.

Given a 0-indexed integer array nums, find a peak element, and return its index. If the array contains multiple peaks, return the index to any of the peaks.

You may imagine that nums[-1] = nums[n] = -∞. In other words, an element is always considered to be strictly greater than a neighbor that is outside the array.

You must write an algorithm that runs in O(log n) time.
## Example
Input: nums = [1,2,3,1]

Output: 2

Explanation: 3 is a peak element and your function should return the index number 2.

## PROGRAM:(Main.cpp)
```
class Solution {
public:
    int findPeakElement(vector<int>& nums) 
    {
        int n=nums.size();
        if(n==1) return 0;
        if(nums[0]>nums[1]) return 0;
        if(nums[n-1]>nums[n-2]) return n-1;

        int l=1,r=n-2;

        while(l<=r)
        {
            int mid=(l+r)/2;

            if(nums[mid]>nums[mid-1] && nums[mid]>nums[mid+1]) return mid;
            else if(nums[mid]>nums[mid-1]) l=mid+1;
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

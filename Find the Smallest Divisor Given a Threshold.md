## Find the Smallest Divisor Given a Threshold (c++)

Given an array of integers nums and an integer threshold, we will choose a positive integer divisor, divide all the array by it, and sum the division's result. Find the smallest divisor such that the result mentioned above is less than or equal to threshold.

Each result of the division is rounded to the nearest integer greater than or equal to that element. (For example: 7/3 = 3 and 10/2 = 5).
## Example
Input: nums = [1,2,5,9], threshold = 6

Output: 5

Explanation: We can get a sum to 17 (1+2+5+9) if the divisor is 1. 
If the divisor is 4 we can get a sum of 7 (1+1+2+3) and if the divisor is 5 the sum will be 5 (1+1+1+2). 

## PROGRAM:(Main.cpp)
```
class Solution {
public:
    int func(vector<int>&nums,int mid ,int threshold)
    {
        int ans=0;
        int n=nums.size();
        for(int i=0;i<n;i++)
        {
            ans+=ceil((double)nums[i]/(double)mid);
        }
        return ans<=threshold;
    }
    int smallestDivisor(vector<int>& nums, int threshold) 
    {
        int maxx=INT_MIN;
        int n=nums.size();
        for(int i=0;i<n;i++)
        {
            maxx=max(nums[i],maxx);
        }

        int ans=0,l=1,h=maxx;

        while(l<=h)
        {
            int mid=(l+h)/2;
            if(func(nums,mid,threshold))
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
};
```
## Complexity
- Time complexity : O(N log(maxx))

- Space complexity : O(1)

## OUTPUT
Output: 5

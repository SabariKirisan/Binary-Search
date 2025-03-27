## Split Array - Largest Sum (same as Allocate Books) (c++)

Given an integer array nums and an integer k, split nums into k non-empty subarrays such that the largest sum of any subarray is minimized.

Return the minimized largest sum of the split.

A subarray is a contiguous part of the array.
## Example
Input: nums = [7,2,5,10,8], k = 2

Output: 18

Explanation: There are four ways to split nums into two subarrays.
The best way is to split it into [7,2,5] and [10,8], where the largest sum among the two subarrays is only 18.

## PROGRAM:(Main.cpp)
```
class Solution {
public:
int func(vector<int>&arr,int n,int m,int mid)
{
    int pages=0,student=1;
    for(int i=0;i<n;i++)
    {
        if(pages+arr[i] <= mid)
        {
            pages+=arr[i];
        }
        else
        {
            student++;
            pages=arr[i];
        }
    }
    return student;
}


int findPages(vector<int>& arr, int n, int m) 
{
    if(m>n) return -1;
    int maxx=INT_MIN,sum=0,ans=-1;
    for(int i=0;i<n;i++)
    {
        maxx=max(maxx,arr[i]);
        sum+=arr[i];
    }
    int l=maxx,h=sum;

    while(l<=h)
    {
        int mid=(l+h)/2;

        if(func(arr,n,m,mid) <= m)
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
int splitArray(vector<int>& nums, int k) 
{
    return findPages(nums,nums.size(),k);
}
};
```
## Complexity
- Time complexity : O(N * log(sum(arr[])-max(arr[])+1))

- Space complexity : O(1)

## OUTPUT
Output: 18

## Minimum days to make M bouquets (c++)

You are given an integer array bloomDay, an integer m and an integer k.

You want to make m bouquets. To make a bouquet, you need to use k adjacent flowers from the garden.

The garden consists of n flowers, the ith flower will bloom in the bloomDay[i] and then can be used in exactly one bouquet.

Return the minimum number of days you need to wait to be able to make m bouquets from the garden. If it is impossible to make m bouquets return -1.
## Example
Input: bloomDay = [1,10,3,10,2], m = 3, k = 1

Output: 3

Explanation: Let us see what happened in the first three days. x means flower bloomed and _ means flower did not bloom in the garden.
We need 3 bouquets each should contain 1 flower.

After day 1: [x, _, _, _, _]   // we can only make one bouquet.

After day 2: [x, _, _, _, x]   // we can only make two bouquets.

After day 3: [x, _, x, _, x]   // we can make 3 bouquets. The answer is 3.

Explanation: 9 exists in nums and its index is 4

## PROGRAM:(Main.cpp)
```
class Solution {
public:
    int func(vector<int>&bloomDay,int mid,int m,int k)
    {
        int n=bloomDay.size();
        int cnt=0,ans=0;

        for(int i=0;i<n;i++)
        {
            if(mid>=bloomDay[i])
            {
                cnt++;
            }
            else
            {
                ans+=(cnt/k);
                cnt=0;
            }
        }
        ans += (cnt / k);
        return ans>=m;
    }
    int minDays(vector<int>& bloomDay, int m, int k) 
    {
        int n=bloomDay.size();
        if(n < m*1LL*k*1LL) return -1;

        int minn=INT_MAX;
        int maxx=INT_MIN;

        for(int i=0;i<n;i++)
        {
            minn=min(minn,bloomDay[i]);
            maxx=max(maxx,bloomDay[i]);
        }
        int low=minn,high=maxx,ans=0;

        while(low<=high)
        {
            int mid=(low+high)/2;

            if(func(bloomDay,mid,m,k))
            {
                ans=mid;
                high=mid-1;
            }
            else
            {
                low=mid+1;
            }
        }
        return ans;
    }
};
```
## Complexity
- Time complexity : O(N log(min to max)

- Space complexity : O(1)

## OUTPUT
Output: 3

## Capacity to Ship Packages within D Days (c++)

A conveyor belt has packages that must be shipped from one port to another within days days.

The ith package on the conveyor belt has a weight of weights[i]. Each day, we load the ship with packages on the conveyor belt (in the order given by weights). We may not load more weight than the maximum weight capacity of the ship.

Return the least weight capacity of the ship that will result in all the packages on the conveyor belt being shipped within days days.
## Example
Input: weights = [1,2,3,4,5,6,7,8,9,10], days = 5

Output: 15

Explanation: A ship capacity of 15 is the minimum to ship all the packages in 5 days like this:

1st day: 1, 2, 3, 4, 5

2nd day: 6, 7

3rd day: 8

4th day: 9

5th day: 10

Note that the cargo must be shipped in the order given, so using a ship of capacity 14 and splitting the packages into parts like (2, 3, 4, 5), (1, 6, 7), (8), (9), (10) is not allowed.

## PROGRAM:(Main.cpp)
```
class Solution {
public:
    int func(vector<int>&weights,int days,int mid)
    {
        int n=weights.size();
        int load=0,day=1;
        for(int i=0;i<n;i++)
        {
            load+=weights[i];
            if(load>mid)
            {
                day=day+1;
                load=weights[i];
            }

        }
        return day<=days;
    }
    int shipWithinDays(vector<int>& weights, int days) 
    {
        int n=weights.size();
        int sum=0,maxx=INT_MIN;

        for(int i=0;i<n;i++)
        {
            sum+=weights[i];
            maxx=max(maxx,weights[i]);
        }
        int ans=0,low=maxx,high=sum;

        while(low<=high)
        {
            int mid=(low+high)/2;

            if(func(weights,days,mid))
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
- Time complexity : O(Nlog(sum))

- Space complexity : O(1)

## OUTPUT
Output: 15

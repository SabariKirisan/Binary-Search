## Koko Eating Bananas (c++)

Koko loves to eat bananas. There are n piles of bananas, the ith pile has piles[i] bananas. The guards have gone and will come back in h hours.

Koko can decide her bananas-per-hour eating speed of k. Each hour, she chooses some pile of bananas and eats k bananas from that pile. If the pile has less than k bananas, she eats all of them instead and will not eat any more bananas during this hour.

Koko likes to eat slowly but still wants to finish eating all the bananas before the guards return.

Return the minimum integer k such that she can eat all the bananas within h hours.
## Example
Input: piles = [3,6,7,11], h = 8

Output: 4

## PROGRAM:(Main.cpp)
```
class Solution {
public:
    int findmax(vector<int> &piles)
    {
        int n=piles.size();
        int maxx=0;
        for(int i=0;i<n;i++)
        {
            maxx=max(piles[i],maxx);
        }
        return maxx;
    }
    int calculatehour(vector<int> &piles, int mid)
    {
        int n=piles.size();
        long long hour=0;
        for(int i=0;i<n;i++)
        {
            hour+=ceil((double)piles[i]/(double)mid);
            if(hour>1e9) return hour;
        }
        return hour;
    }
    int minEatingSpeed(vector<int>& piles, int h) 
    {
        int l=1,r=findmax(piles);
        int bana_to_eat=INT_MAX;

        while(l<=r)
        {
            int mid=(l+r)/2;

            if(calculatehour(piles, mid) <= h)
            {
                bana_to_eat=mid;
                r=mid-1;
            }
            else
            {
                l=mid+1;
            }
        }
        return bana_to_eat;
    }
};
```
## Complexity
- Time complexity : O(n * log(maxPile))

- Space complexity :

O(1) if we don't count input storage (ignoring the input array).

O(n) if we count the input array storage.

## OUTPUT
Output: 4

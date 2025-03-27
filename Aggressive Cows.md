## Aggressive Cows (c++)

You are given an array with unique elements of stalls[], which denote the position of a stall. You are also given an integer k which denotes the number of aggressive cows. Your task is to assign stalls to k cows such that the minimum distance between any two of them is the maximum possible.
## Example
Input: stalls[] = [1, 2, 4, 8, 9], k = 3

Output: 3

Explanation: The first cow can be placed at stalls[0], 

the second cow can be placed at stalls[2] and 

the third cow can be placed at stalls[3]. 

The minimum distance between cows, in this case, is 3, which also is the largest among all possible ways.

## PROGRAM:(Main.cpp)
```
class Solution {
  public:
    bool func(vector<int> &stalls ,int mid,int k)
    {
        int n=stalls.size();
        int cnt=1,last=stalls[0];
        for(int i=1;i<n;i++)
        {
            if(stalls[i]-last>=mid)
            {
                cnt++;
                last=stalls[i];
            }
            if(cnt>=k) return true;
    
        }
        return false;
    }
    int aggressiveCows(vector<int> &stalls, int k) 
    {
        int n=stalls.size();
        sort(stalls.begin(),stalls.end());
        int l=1,h=stalls[n-1]-stalls[0];
        int ans=0;
        
        while(l<=h)
        {
            int mid=(l+h)/2;
            
            if(func(stalls,mid,k)==true)
            {
                ans=mid;
                l=mid+1;
            }
            else
            {
                h=mid-1;
            }
        }
        return ans;
    }
};
};
```
## Complexity
- Time complexity : O(NlogN) + O(N * log(max(stalls[])-min(stalls[])))

- Space complexity : O(1)

## OUTPUT
Output: 3

## Count the Number of occurrence (c++)

Given a sorted array, arr[] and a number target, you need to find the number of occurrences of target in arr[]. 
## Example
Input: arr[] = [1, 1, 2, 2, 2, 2, 3], target = 2

Output: 4

Explanation: target = 2 occurs 4 times in the given array so the output is 4.

## PROGRAM:(Main.cpp)
```
class Solution {
  public:
    int first(vector<int>&arr,int target,int n)
    {
        int l=0,r=n-1;
        int first=-1;
        while(l<=r)
        {
            int mid=(l+r)/2;

            if(target==arr[mid])
            {
                first=mid;
                r=mid-1;
            }
            else if(target<arr[mid]) r=mid-1;
            else l=mid+1;
        }
        return first;
    }
    int last(vector<int> &arr,int target,int n)
    {
        int l=0,r=n-1;
        int last=-1;
        while(l<=r)
        {
            int mid=(l+r)/2;
            if(arr[mid]==target)
            {
                last=mid;
                l=mid+1;
            }
            else if(target<arr[mid]) r=mid-1;
            else l=mid+1;
        }
        return last;
    }
    vector<int> searchRange(vector<int>& arr, int target,int n) 
    {
      int f=first(arr,target,n);
      if(f == -1) return {-1,-1};
      int l=last(arr,target,n);
      return {f,l};

    }

    int countFreq(vector<int>& arr, int target) 
    {
        int n=arr.size();
        vector<int>ans=searchRange(arr,target,n);
        if(ans[0]==-1) return 0;
        return ans[1] - ans[0] +1;
    }
};
```
## Complexity
- Time complexity : O(logN)

- Space complexity : O(1)

## OUTPUT
Output: 4

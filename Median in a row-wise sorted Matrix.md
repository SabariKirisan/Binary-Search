## Median in a row-wise sorted Matrix  (c++)

Given a row-wise sorted matrix where the number of rows and columns is always odd, find the median of the matrix.
## Example
Input: mat = [[1, 3, 5], [2, 6, 9], [3, 6, 9]]

Output: 5

Explanation: Sorting matrix elements gives us {1,2,3,3,5,6,6,9,9}. Hence, 5 is median. 
## PROGRAM:(Main.cpp)
```
class Solution {
  public:
    int upperbound(vector<int> &mat,int x, int m)
    {
        int ans=m;
        int low=0,high=m-1;
        while(low<=high)
        {
            int mid=(low+high)/2;
            if(mat[mid]>x)
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
    int func(vector<vector<int>> &mat,int mid,int n,int m)
    {
        int cnt=0;
        for(int i=0;i<n;i++)
        {
            cnt+=upperbound(mat[i],mid,m);
        }
        return cnt;
    }
    int median(vector<vector<int>> &mat) 
    {
        int n=mat.size();
        int m=mat[0].size();
        int low=INT_MAX,high=INT_MIN;
        for(int i=0;i<n;i++)
        {
            low=min(low,mat[i][0]);
            high=max(high,mat[i][m-1]);
        }
        int req=(n*m)/2;
        while(low<=high)
        {
            int mid=(low+high)/2;
            
            int small_equal=func(mat,mid,n,m);
            if(small_equal<=req) low=mid+1;
            
            else high=mid-1;
        }
        return low;
    }
};
```
## Complexity
- Time complexity : O(log(10^9)) X O(N(logM)), where N = number of rows in the given matrix, M = number of columns in the given matrix

Reason: Our search space lies between [0, 109] as the min(matrix) can be 0 and the max(matrix) can be 10^9. We are applying binary search in this search space and it takes O(log(10^9)) time complexity. Then we call countSmallEqual() function for every ‘mid’ and this function takes O(N(logM)) time complexity.

- Space complexity : O(1)

## OUTPUT
Output: 5

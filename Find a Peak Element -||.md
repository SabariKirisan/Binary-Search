## Find a Peak Element -||  (c++)

A peak element in a 2D grid is an element that is strictly greater than all of its adjacent neighbors to the left, right, top, and bottom.

Given a 0-indexed m x n matrix mat where no two adjacent cells are equal, find any peak element mat[i][j] and return the length 2 array [i,j].

You may assume that the entire matrix is surrounded by an outer perimeter with the value -1 in each cell.

You must write an algorithm that runs in O(m log(n)) or O(n log(m)) time.
## Example

![image](https://github.com/user-attachments/assets/57c225f0-f073-4d0b-a5da-8c7265866a56)



Input: mat = [[1,4],[3,2]]

Output: [0,1]

Explanation: Both 3 and 4 are peak elements so [1,0] and [0,1] are both acceptable answers.
## PROGRAM:(Main.cpp)
```
class Solution {
public:
    int func(vector<vector<int>> &mat,int n,int m,int col)
    {
        int maxx=-1;
        int index=-1;
        for(int i=0;i<n;i++)
        {
            if(mat[i][col]>maxx)
            {
                maxx=mat[i][col];
                index=i;
            }
        }
        return index;
    }
    vector<int> findPeakGrid(vector<vector<int>>& mat) 
    {
        int n=mat.size();
        int m=mat[0].size();

        int l=0,h=m-1;
        while(l<=h)
        {
            int mid=(l+h)/2;
            int cnt_max_row=func(mat,n,m,mid);
            int left= mid-1 >=0 ? mat[cnt_max_row][mid-1] :-1;
            int right= mid+1 <m ? mat[cnt_max_row][mid+1] :-1;

            if(mat[cnt_max_row][mid] > left && mat[cnt_max_row][mid] > right)
            {
                return {cnt_max_row,mid};
            }
            else if(mat[cnt_max_row][mid] < left) h=mid-1;

            else l=mid+1;
        }
        return {-1,-1};
    }
};
```
## Complexity
- Time complexity : O(N * log M)

- Space complexity : O(1)

## OUTPUT
Output: [0,1]

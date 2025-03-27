## Search in a row and column-wise sorted matrix (c++)

Write an efficient algorithm that searches for a value target in an m x n integer matrix matrix. This matrix has the following properties:

Integers in each row are sorted in ascending from left to right.

Integers in each column are sorted in ascending from top to bottom.
## Example

![image](https://github.com/user-attachments/assets/b9818187-3b82-4b93-961e-60965992af64)



Input: matrix = [[1,4,7,11,15],[2,5,8,12,19],[3,6,9,16,22],[10,13,14,17,24],[18,21,23,26,30]], target = 5

Output: true

## PROGRAM:(Main.cpp)
```
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) 
    {
        int n=matrix.size();
        int m=matrix[0].size();

        int row=0,col=m-1;

        while(row<n && col>=0)
        {
            if(matrix[row][col]==target) return true;

            else if(matrix[row][col]<target) row++;

            else col--;
        }
        return false;   
    }
};
```
## Complexity
- Time complexity : O(log(N+M))

- Space complexity : O(1)

## OUTPUT
Output: true

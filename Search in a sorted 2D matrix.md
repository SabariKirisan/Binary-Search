## Search in a sorted 2D matrix (c++)

You are given an m x n integer matrix matrix with the following two properties:

Each row is sorted in non-decreasing order.

The first integer of each row is greater than the last integer of the previous row.

Given an integer target, return true if target is in matrix or false otherwise.

You must write a solution in O(log(m * n)) time complexity.
## Example

![image](https://github.com/user-attachments/assets/622df4ab-e06d-4c88-b7ef-35a1e225afcd)


Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 3

Output: true

## PROGRAM:(Main.cpp)
```
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) 
    {
        int n=matrix.size();
        int m=matrix[0].size();

        int low=0,high=n*m-1;

        while(low<=high)
        {
            int mid =(low+high)/2;
            int row=mid/m;
            int col=mid%m;
            if(matrix[row][col]==target) return true;
            
            else if(matrix[row][col]<target) low=mid+1;

            else high=mid-1;
        }
        return false;  
    }
};
```
## Complexity
- Time complexity : O(log(N*M))

- Space complexity : O(1)

## OUTPUT
Output: true

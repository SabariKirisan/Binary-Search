## Painter's Partition (same as Allocate Books) (c++)

Given an array/list of length ‘n’, where the array/list represents the boards and each element of the given array/list represents the length of each board. Some ‘k’ numbers of painters are available to paint these boards. Consider that each unit of a board takes 1 unit of time to paint.

You are supposed to return the area of the minimum time to get this job done of painting all the ‘n’ boards under a constraint that any painter will only paint the continuous sections of boards.
## Example
Input: arr = [2, 1, 5, 6, 2, 3], k = 2

Output: 11

Explanation:
First painter can paint boards 1 to 3 in 8 units of time and the second painter can paint boards 4-6 in 11 units of time. Thus both painters will paint all the boards in max(8,11) = 11 units of time. It can be shown that all the boards can't be painted in less than 11 units of time.

## PROGRAM:(Main.cpp)
```
#include<bits/stdc++.h>
using namespace std;
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

int findLargestMinDistance(vector<int> &boards, int k)
{
    findPages(boards,boards.size(),k);
}
```
## Complexity
- Time complexity : O(N * log(sum(arr[])-max(arr[])+1))

- Space complexity : O(1)

## OUTPUT
Output: 11

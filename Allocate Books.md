## Allocate Books (c++)

Given an array ‘arr’ of integer numbers, ‘arr[i]’ represents the number of pages in the ‘i-th’ book.

There are ‘m’ number of students, and the task is to allocate all the books to the students.

Allocate books in such a way that:

1. Each student gets at least one book.

2. Each book should be allocated to only one student.

3. Book allocation should be in a contiguous manner.

You have to allocate the book to ‘m’ students such that the maximum number of pages assigned to a student is minimum.

If the allocation of books is not possible, return -1.
## Example
Input: ‘n’ = 4 ‘m’ = 2 

‘arr’ = [12, 34, 67, 90]

Output: 113

Explanation: All possible ways to allocate the ‘4’ books to '2' students are:

12 | 34, 67, 90 - the sum of all the pages of books allocated to student 1 is ‘12’, and student two is ‘34+ 67+ 90 = 191’, so the maximum is ‘max(12, 191)= 191’.

12, 34 | 67, 90 - the sum of all the pages of books allocated to student 1 is ‘12+ 34 = 46’, and student two is ‘67+ 90 = 157’, so the maximum is ‘max(46, 157)= 157’.

12, 34, 67 | 90 - the sum of all the pages of books allocated to student 1 is ‘12+ 34 +67 = 113’, and student two is ‘90’, so the maximum is ‘max(113, 90)= 113’.

We are getting the minimum in the last case.

Hence answer is ‘113’.

## PROGRAM:(Main.cpp)
```
#include <bits/stdc++.h>
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
```
## Complexity
- Time complexity : O(N * log(sum(arr[])-max(arr[])+1))

- Space complexity : O(1)

## OUTPUT
Output: 113

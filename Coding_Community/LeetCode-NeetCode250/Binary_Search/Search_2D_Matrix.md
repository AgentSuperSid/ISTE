You are given an m x n integer matrix matrix with the following two properties:

Each row is sorted in non-decreasing order.
The first integer of each row is greater than the last integer of the previous row.
Given an integer target, return true if target is in matrix or false otherwise.

You must write a solution in O(log(m * n)) time complexity.

Example 1:
```
Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 3
Output: true
```

Example 2:
```
Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 13
Output: false
 ```

Constraints:
```
m == matrix.length
n == matrix[i].length
1 <= m, n <= 100
-104 <= matrix[i][j], target <= 104
```
### Your Solution:
```
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target)
    {   // YOUR IDEA
        /* 
        First do binary search for the first elements in each row to see in which row the element may lie.
        Then do binary search in that row.
        */
        int begm=0 , endm=matrix.size()-1; 
        unsigned int midm;
        unsigned int targetrow=0;
        if(matrix.empty())
        {
            return false;
        }
        while(begm<=endm)
        {
            midm=endm - (endm-begm)/2;
            if(matrix[midm][0]==target)
            {
                return true;
            }
            else if(matrix[midm][0]>target)
            {
                endm=midm-1;
            }
            else
            {
                begm=midm+1;
            }
            if(endm<0)
            {
                return false;
            }
        }
        targetrow=endm;
         int beg=0; //If you do unsigned for beg and end it will go out of bounds for beg<=end fr -ve target
         int end= matrix[0].size()-1;
        unsigned int mid;
        while(beg<=end)
        {
            mid=end-(end-beg)/2;
            if(matrix[targetrow][mid]==target)
            {
                return true;
            }
            else if(matrix[targetrow][mid]>target)
            {
                end=mid-1;
            }
            else
            {
                beg=mid+1;
            }
        }
        return false;
    }
};
```

### Learning
* In Binary Search you are narrowing to a row that has a high probability of having the target. It may not be there
* To handle edge cases like what if the target was -ve or the matrix itself was empty.
* After the while loop for binary search ends, the beg ptr crosses the end ptr and the row which the end ptr is pointing will have the target if present.

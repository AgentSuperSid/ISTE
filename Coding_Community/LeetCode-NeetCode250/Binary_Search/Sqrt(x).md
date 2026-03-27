Given a non-negative integer x, return the square root of x rounded down to the nearest integer. The returned integer should be non-negative as well.
You must not use any built-in exponent function or operator.
For example, do not use pow(x, 0.5) in c++ or x ** 0.5 in python.
 

Example 1:
```
Input: x = 4
Output: 2
Explanation: The square root of 4 is 2, so we return 2.
```

Example 2:
```
Input: x = 8
Output: 2
Explanation: The square root of 8 is 2.82842..., and since we round it down to the nearest integer, 2 is returned.
 ```

Constraints:

`0 <= x <= 231 - 1`

### Your Solutiom:
```
class Solution {
public:
        int mySqrt(int x) 
    {
        
        if(x==1 || x==0)
        {
            return x;
        }
        /*
        unsigned int prev=1; // The first idea u got was brute force method. It works, but not efficient.
        unsigned int i;
        for(i=1;((i*i <= x) && (i<= x/2)) ; i++)
        {
            prev=i;
        }
        return prev;
    
        */

        /* */
            unsigned int ans;
            unsigned int beg=1 , end= x/2;
            unsigned int mid = beg + (end - beg) / 2;
            while(beg<=end)  // Then after realizing that this question comes under binary search u tried
                             // this method.
            {
                mid = beg + (end - beg) / 2; // Better than (beg + end)/2 cuz the latter may add upto a bigger
                                             // value bofore /2 which may cross the unsigned int size
                if(mid>x/mid)   // mid*mid > or <= x was replaced with mid > or <= x/mid. 
                                // This avoided possible memory or time limit.
                {
                    end=mid-1;
                    
                }
                else if(mid<=x/mid) // This will include both the lesser or equal condition. So no need
                                    // another == condtion
                {
                    ans=mid; //
                    beg=mid+1;
                   
                }
 
            }
            return ans;
        /* */
    }
};
```

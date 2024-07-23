```java
class Solution {
public:
    int maxScore(vector<int>& nums) {
        // subhahu
        // start 04:06 AM

        // dp - definately (we can thing better than dp but latter)
        // solved 04:12 (very easY)
        // now then more better solutions

        int n = nums.size();
        vector<int> dp(n, 0);

        for(int i = 1 ; i < n ; i++) {
            for(int j = 0 ; j < i ; j++) {
                dp[i] = max(dp[i], ((i-j) * nums[i]) + dp[j]);
            }
            cout << dp[i] << endl;
        }

        return dp[n-1];
    }
};

/**
trying to come up with better solutions

a, b, c (index)
d, e, f

(b-a)*e
now if i want to calculate for e (b index) what will maximise my ans (as required)
be - ae (be will not change as for calculating for that index, so we need to minimise ae value)
so we nned to minimise value of (a) (so find the farest.....)
NO some issue with above last line conclusion... NEED TO CONTINUE FROM HERE>

*/
```

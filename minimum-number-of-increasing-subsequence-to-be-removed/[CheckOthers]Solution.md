```java
class Solution {
public:
    int minOperations(vector<int>& nums) {
        // subhahu
        // need to start..
        // 02:22 AM
        // first submission 02:55 AM (32 mins)
        // 627 / 632 testcases passed (getting TLE, but most of test are passing)
        // improvement can be using binary search to find lower closte 
        // (MUST THINK FOR OTHER SOLUTION) have done this before, forgot about how i did it before (above mentoiedn line)
        // in this its simple if all number are bigger then simple insert will work
        // Finally Done (beated everyone - 03:19, 55 mins)


        // keep find longest subsequence and repeat. (every longe will take n*n)
        // but this will be too much
        // can we use minStack here.
        // queustion is about finding min total number of increasing subsequence we can form
        // what if i sort and compare sorted vs given
        // or what if we find all the peaks
        // question if about how many increasing subsequence subset we can create...
        // dp can be use..
        // like overlapping of interval, we will find out if a number is a part of any of the
        // subsequence (means previous number if not +1);
        // but in this ther can overlapping for (in case of duplicate)
        // what if we start createing parallel subequence while traversin from left to right.
        // - first check if this can be a part of any existing subequence
        // - other new chain will be created
        // use priority queue - (store tip of every subequence with value);

        // priority_queue<int> pq;
        // pq.push(nums[0]);
        vector<int> pq;
        pq.push_back(nums[0]);

        for(int i = 1 ; i < nums.size() ; i++) {
            // issue in algo i can't always say that we shoudl form pair with lowest availabe.
            // pair should be always with lower but closet number
            // if(pq.top() < nums[i]) {
            //     pq.pop();
            //     pq.push(nums[i]);
            // }
            // else {
            //     pq.push(nums[i]);
            // }
            
            // check if lower closet availabe
            // int lowerIndex = -1;
            // for(int k = 0 ; k < pq.size() ; k++) {
            //     if(nums[i] > pq[k] && lowerIndex == -1) {
            //         lowerIndex = k;
            //     }
            //     else if(nums[i] > pq[k] && pq[lowerIndex] < pq[k]){
            //         lowerIndex = k;
            //     }
            // }

            // do binary search with upper_bound
            int lowerIndex = lower_bound(pq.begin(), pq.end(), nums[i]) - pq.begin();

            //else push

            if(lowerIndex == 0) {
                pq.insert(pq.begin(),nums[i]);
            }
            else {
                pq[lowerIndex-1] = nums[i];
            }
        }

        
        return pq.size();
        
    }
};
```

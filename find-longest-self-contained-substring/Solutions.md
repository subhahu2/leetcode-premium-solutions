```java
class Solution {
public:
    int maxSubstringLength(string s) {
        // subhahu
        // 10:36 PM (2 Aug 2024)

        // pick substring in such a way that all chacter can be disected (disjont)
        // what if we store first and last index of every character...
        // i remember i have seen this question before..
        // - storing first and last occurent of every character will help
        // - what if we trying to find substring form first and last index of every char
        // - and verify if it is possible or not. this can be easy as we are only sotring first and last
        // - because we are only storing first and last and total character are only 26.
        // - but ...with this we will have to try multiple combination of pairs...
        // - will this work ?(need a thought)
        // - so we need to create cominbartion with 26 character(1st and 2nd index)
        // - but how to make conbinations.....
        // - question is like we are given mulitple intervals, we need to find longest overlapping.
        // - what if we use sweep line here, (with hash)

        // NOt able to solve this after this ...... (tried for 30 mins).....
        // afgetr just viewing the soluton, it seems i was doing good and was on correct path
        // but was not able to combine all observatoin and concpet to come up complete solutions.
        

    }
};
```

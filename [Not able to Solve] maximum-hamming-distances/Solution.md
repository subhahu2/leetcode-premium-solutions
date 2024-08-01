```java
class Solution {
public:
    vector<int> maxHammingDistances(vector<int>& nums, int m) {
        // subhahu
        // 12:29 AM

        // related to bit manipulation
        // brute force - loop n^2 find happing distance again all numbers
        // but will be TLE
        // (NOT SURE) WHAT if we do bucketing all bit places...(total 17)
        // like how many number have set bit in 1st palce and so on....
        // -- so with this we will have 17 vs all index of array .
        // what if we starting generating all number with all 17places by using bit, and check in hash map if it exist... (not sure.)
        // thing hamming distance in terms of decimal number (but how ?) (with hash
        // or sorting + binary search (but how...)?
        // -- sort based on set bits and then do binary search (but binary search not making sense here..)
        // in simple ter, we are given string which only consist of 0s and 1s, for every string
        // we need to find which string has larget distance...
        // this is like XOR, we can use xor...(if different then 1 otherwise zero)
        // so we need to find out a number with which pair has highest XOR.
        // first question - find pair value for each value in such a way that xor is maximum
        // second quesotn  - once we got pair value count their difference..

        // was able to come up with very simplified version of this question
        // but not solved.

    }
};
```

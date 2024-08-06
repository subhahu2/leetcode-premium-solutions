```c++
/**
 * Definition for an infinite stream.
 * class InfiniteStream {
 * public:
 *     InfiniteStream(vector<int> bits);
 *     int next();
 * };
 */
class Solution {
public:
    int findPattern(InfiniteStream* stream, vector<int>& pattern) {
        // subhahu
        // 06 Aug (11:36 PM)
        // after 23 mins 42 seconds - 9622 / 12841 testcases passed (12:00 AM) (:) pattern need to build first, but even that :) :))...
        // After fixing patternVal - 9622 / 12841 testcases passed (same)
        // so many test cases are passing because mostly answer is zero...
        // Not able to Solve - checking solution
        // my solution was correct, in writing code, messed up somewhere... so wash comparing my solution with other soluiton with same approach like mine rolling hash..
        


        // stragigh comparing both arry from begining - (but if match is partial, then how to backtrack ?)
        // kind of rolling hash...
        // problem is how to remove first bit from window and then add new to verif..
        // consider every bit like binary number bit...
        // when first bit left, calulate the impact and then 
        // - start with stream and first reach pattenr.size() char, and then only do this rolling start...
        // can't we use simple left shift and right shift
        // but issue in this entire thing pattern can start with 00 also.

        long long times = 10001;
        int curr = 0;
        long long c = 0;
        int index = 0;
        int patternVal = 0;
        int pSize = pattern.size();

        for(int i = 0 ; i < pSize ; i++) {
            patternVal = ((patternVal << 1) + (1*pattern[i]));
        }

        cout << patternVal << endl;

        while(c < times) {
            cout << c << " - " << curr << endl;
            int nextBit = stream->next();
            if(c < pattern.size()) {
                curr = ((curr << 1) + (1*nextBit));
            }
            else if(curr == patternVal) return index;
            else {
            // remove first bit and add new bit.
            // fetch first bits
            // if((1 << pSize) & curr) {
                curr = curr >> 1;
            // }
            // adding new bit.
                curr = ((curr << 1) + (1*nextBit));
                index++;
                cout << "index - " << index << endl;
            }
            c++;
        }

        if(curr == patternVal) return index;
        return -1;
    }
};
```

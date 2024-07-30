```java
class Solution {
public:
    long long tripletCount(vector<int>& a, vector<int>& b, vector<int>& c) {
        // subhahu
        // started at 03:51 AM
        // first code complete - 04:09 AM (after 18min 40Ssec)
        // there was some issue in my code with find total set bit from number
        // just for this i copied code from chatgpt
        // now - 677 / 704 testcases passed - 04:16 AM (after 26min 0 sec) (getting some signed integer overflow: 3440184 * 1855 )
        // Done i killed it - 04:20 AM (after 28min 35 sec) (fix was to add typecase of long long to all multiplication numbers)
        // now will see what is issue in my set bit calculation code..
        // fixed my set bit count code - (was using && instead of &, i was used in two loops in same scope, log2 needs to be used not log10 (since we nned szie of binary number)) (also make suer to check log value of end cases like 0 - log10(0) is -infi);


        // initially i was thing to come up with all number which has even bit but this will dfs.
        // also we cannot generate all tripllets at it will be 10^15
        // Need to thing from XOR operator properties way.
        // what if we count bit for all number in an array for every bit.
        // (MAIN) two even will make always even, two odd also always make even (may be wrong here, have not thought in depth)
        // what about even vs odd ?
        // we will find all odd/even in all array based on set bit.
        // seems like combination and permutation question.
        // (MAIN) odd vs even will always be - odd

        int aEven = totalEven(a);
        int bEven = totalEven(b);
        int cEven = totalEven(c);

        cout << aEven << endl;
        cout << bEven << endl;
        cout << cEven << endl;

        long long ans = 0ll;

        // combinations
        // even*3, even*odd-2
        ans += (long long)((long long) aEven * (long long) bEven * (long long)cEven);

        ans += (long long)((long long) aEven * (long long) (b.size() - bEven) * (long long) (c.size() - cEven));
        ans += (long long)((long long)(a.size() - aEven) * (long long)bEven * (long long)(c.size() - cEven));
        ans += (long long)((long long)(a.size() - aEven) * (long long)(b.size() - (long long)bEven) * cEven);

        return ans;

    }

    // wrote by me
    int totalEven(vector<int> &a) {
        int even = 0;
        for(int i = 0 ; i < a.size() ; i++) {
            if(a[i] == 0) {
                even++;
                continue;
            }
            int sz = log2(a[i]);
            int count = 0;
            for(int k = 0 ; k <= sz ; k++) {
                if(a[i] & (1 << k)) {
                    count++;
                } 
            }
            if(count % 2 == 0) {
                even++;
            }
        }

        return even;
    }

// came from chatgpt
// int totalEven(vector<int> &a) {
//     int even = 0;
//     for(int i = 0; i < a.size(); i++) {
//         int num = a[i];
//         int count = 0;

//         // Count the number of set bits (1s) in the binary representation of num
//         while (num > 0) {
//             count += num & 1;
//             num >>= 1;
//         }
        
//         // Check if the count of set bits is even
//         if (count % 2 == 0) {
//             even++;
//         }
//     }

//     return even;
// }

};
```

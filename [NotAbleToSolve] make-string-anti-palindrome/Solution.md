```c++
class Solution {
public:
    string makeAntiPalindrome(string s) {
        // subhahu (12:27 AM)
        // 06 August 2024
        // 1st solution - very easy/basic - 938 / 1212 testcases passed (after 21 mins)
        // checking solution after 28 mins
        // this was a easy question, i was very close to final complete solutions - but missed. it.
        

        // we are given a string, conser anther one with reverse..
        // bet thing would be to count all character count and start writing it one by one..
        // question is more about how to distribute the character in string in such a way
        // that they are not euqal and smalles in lex...
        // if highes frequency count is greater than n/2 then it is imposssible....
        // this is more like how to use left lex character with their specific count...
        // may be dp...
        // IMPO - TO CHECK - also :: is there any meaning of having even length always ????
        // priority queue, based on number left and small character.
        // 1st one - count frequency and always append lex smalles and if any char is over/
        // lapping left and right half of string just handle that part and one
        // 2nd one - just sort the string.

        sort(s.begin(), s.end());

        int mid = s.length()/2-1;

        cout << mid << endl;

        if(s[mid] == s[mid+1]) {
            // find left similar char
            // find right similay characte
            // basically find range
            return "-1";
        }


        return s;
    }
};
```

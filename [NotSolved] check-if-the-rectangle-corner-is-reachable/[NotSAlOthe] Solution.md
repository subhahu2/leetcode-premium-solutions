not solve also need to check other.

```java
class Solution {
public:
    bool canReachCorner(int X, int Y, vector<vector<int>>& circles) {
        // start at 02:12 AM...
        // end at 03:05AM, it took some time but i am able to reach a solution which will not give TLE for sure.
        // becasuse of some other work, leaving this here, willl start from same..
        
        // instead of find hwo to react from bottom to top
        // lets see all the config where ti will be false..
        // if it is in all mean circles is not touch any bounday than it will be always true
        // find in what condition circles can block top .
        // if circles is touch both (top-right) side of rectangle then it will always return false or even intersections, or if end point les in circle;
        // -- need to play with circl center and x, y - need to think of a forumual..
        // -- if distance between centre and xy is begger than radius then true (not sure, ..)
        // -- how we will calculate distance..
        // oops i missed that there are multiple circles - now this is very hard.
        // -- still we find out uptouch and right touch but we will hvae to find if there any 
        // ...space present in case touch belongs to different circel..
        // total cicles are only 10^3, even brute force should work, what will be brute force here.
        // one more thing if bottom is blocked then also it will not work.
        // we can write code for partial test cases, like if no (less than 2) two touch are present then true.
        // what if i build graph of all connect circel (so every circel will be tested again every cirlce, we can have four types of touch (four side))

        unordered_map<int, vector<pair<int, string>>> adj; // store reverse also.

        for(int i = 0 ; i < circles.size() ; i++) {
            for(int k = i + 1 ; k < circles.size() ; k++) {
                checkOverlap(circles, i, k, adj);
            }
        }

        for(int i = 0 ; i < circles.size() ; i++) {
            // first check if cicles is not already traversed 
            // then if it intersect with upside or left side
            // at every grpah chain check if it touches rightside or bottom side.
            // (upside, rightside are paired), (left, bottom are paired) intersectino in side will not work 
            // here we are finding if reach can be block or not.
        }

        return true;

    }

    void checkOverlap(vector<vector<int>>& circles, int a, int b, unordered_map<int, vector<pair<int, string>>> adj) {
        // int upDiff = abs(Y-circles[])
        // find if circle intersect.

    }
};
```

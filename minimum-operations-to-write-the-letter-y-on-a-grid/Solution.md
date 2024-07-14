```java
class Solution {
public:
    int minimumOperationsToWriteY(vector<vector<int>>& grid) {
        // subhahu
        // calcualte all count of 1, 0, 2
        // count value in Y
        // 1st try - 246 / 909 testcases passed
        // took help of chatgpt, got to know issue was in my isY() function logic...
        // coment my one and used chatgpt ones....
        /** Explanation - The top part of the 'Y' should include cells where the row index equals the column index (i == j) and where the row index equals the column index mirrored around the center (i == n - 1 - j). Your function only included the i == j condition and did not consider the mirrored condition. */


        int n = grid.size();
        int midOfY = n/2; // index;
        int operations = INT_MAX;
        vector<int> count;
        count.push_back(0);count.push_back(0);count.push_back(0);

        vector<int> yCount;
        int totalY = 0;
        yCount.push_back(0);yCount.push_back(0);yCount.push_back(0);

        for(int i = 0  ; i < grid.size() ; i++) {
            for(int j = 0 ; j < grid[i].size() ; j++) {
                // check if cell belongs to Y.
                if(isY(i, j, n)) {
                    yCount[grid[i][j]]++;
                    totalY++;
                }
                else {
                    count[grid[i][j]]++;
                }
            }
        }

        // now how to calcuate minise operation.
        // not sure what algo to use..

        // simple thing we have 2 bucket, where in each bucket we have 3 types of balls
        // find how many minium balls to replace -- 
        // recursive combination (because we only have 3 values, 0, 1, 2);

        for(int i = 0 ; i < yCount.size() ; i++) {
            for(int j = 0 ; j < count.size() ; j++) {
                if(i != j) {
                    int opY = (totalY - yCount[i]);
                    int op = (n*n-totalY) - count[j];
                    cout << "opY- " << opY << endl;
                    cout << op << endl;
                    operations = min(operations, op + opY);
                }
            }
        }


        return operations;
    }

    // bool isY(int i, int j, int n) {
    //     if(i == j && i <= n/2) {
    //         return true;
    //     }
    //     if(i > n/2 && j == n/2) return true;
    //     return false;
    // }
    bool isY(int i, int j, int n) {
        int mid = n / 2;
        if (i <= mid && (j == i || j == n - 1 - i)) return true; // top 'V' part
        if (i > mid && j == mid) return true; // vertical line
        return false;
    }
};
```

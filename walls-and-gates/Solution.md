```java
class Solution {
public:
    void wallsAndGates(vector<vector<int>>& rooms) {
        // BFS - starts with traversing from all gates...
        // and use hashing with i*n + m, so if we are done with one coor we will not
        // ... reprocess it , as we are using BFS it is already shor.t.
        // time complextiy n^2, every cell is only traversed once or twocie but linear
        // i am taking time to come up with hashing formual for 2d coordination to 1d int.
        // fist submit after 19 minus - 6 / 62 testcases passed
        // initially missing adding next ndoe to queue...
        // i am definately missing some small bug, logic is fine.- asking chagpt for issue in done
        // first fix - i was using rooms.size() instead of rooms[0].size() in inital nested loops.....--- 14 / 62 testcases passed
        // issue was with way i was writing if/else conditino, chatgpt combied all of my if condition and it worked.... (all commented lines in first accepted solutin is that.)
        // aflter investigation i found out that hash[hashId] = true in all continue cases is creating the majore issue and test are failig. 2. also one minor bug else if(rooms == -1) should be in if, not else if......
        // need to investigate why above line are not correct, what i am missing in thinking.
        // related debuggin chatgpt url - https://chatgpt.com/c/65c916c5-4862-4394-a10f-9483c9589db5



        unordered_map<int, bool> hash;
        // int = i * j + j

        queue<pair<int, int>> q;
        for(int i = 0 ; i < rooms.size() ; i++) {
            for(int j = 0 ; j < rooms[0].size() ; j++) {
                int hashId = i*rooms[0].size() + j;
                if(rooms[i][j] == 0) {
                    q.push({i, j});
                    hash[hashId] = true;
                }
            }
        }

        int distance = 1;

        while(!q.empty()) {
            int sz = q.size();
            for(int i = 0 ; i < sz ; i++) {
                vector<vector<int>> dir{{0, -1}, {-1, 0}, {0, 1}, {1, 0}};
                pair<int, int> cellIndex = q.front();
                q.pop();
                for(int k = 0 ; k < 4 ; k++) {
                    int r = cellIndex.first + dir[k][0];
                    int c = cellIndex.second + dir[k][1];
                    int hashId = r*rooms[0].size() + c;

                    if(!isSafe(r, c, rooms.size(), rooms[0].size()) || hash[hashId] == true || rooms[r][c] == -1) {
                        // hash[hashId] = true; -- issue to debug.
                        continue;
                    }

                    // if(!isSafe(r, c, rooms.size(), rooms[0].size())) {
                    //     hash[hashId] = true;
                    //     continue;
                    // }

                    // if(hash[hashId] == true) {
                    //     continue;
                    // }
                    // else if(rooms[r][c] == -1){
                    //     hash[hashId] = true;
                    //     continue;
                    // }
                    // else {
                        hash[hashId] = true;
                        rooms[r][c] = distance;
                        q.push(make_pair(r, c));
                    // }
                }
            }
            distance++;
        }

        return;
    }

    bool isSafe(int i, int j, int n, int m) {
        if(i >= 0 && i < n && j >= 0 && j < m) {
            return true;
        }
        return false;
    }
};
```

```java
class Solution {
public:
    int maximumInvitations(vector<vector<int>>& grid) {
        // subhahu
        // 03:27 AM

        // create all edges of graph for all nodes, seems kind of bipartite graph
        // calculate all indegree of girls, which who have least indegree starts with that..
        // so, use priority queue kind of thing...

        // but girl may got multile invitatoin so which one to pick....
        // change - get all inviation of boy and pick the girl which has least indegree.
        // least connection for boy and girl both need to be started, but issuer here is BOTH.
        
        // or change - think it like matrix where if we slecte one cell then entire row and column of that will become zero....
        // very hard to think solution in this way.

        // create two priority queue with girl and boys
        // pick one from either of them with lowest count and will cursh them.
        // for boy - count outdegree, for girl count indegree;

        // after seeening solutoin (bipartite graph also came to my mind but..)


        unordered_map<int, int> girlsIndegreeCount;
        unordered_map<int, int> boyOutdegree;

        for(int i = 0 ; i < grid.size() ; i++) {
            for(int j = 0 ; j < grid[i].size() ; j++) {
                if(grid[i][j] == 1) {
                    girlsIndegreeCount[j]++;
                    boyOutdegree[i]++;
                }
            }
        }

        auto bCmp = [](const pair<int, int> &a, const pair<int, int> &b) {
            return a.second < b.second;
        };

        priority_queue<pair<int, int>, vector<pair<int, int>>, decltype(bCmp)> boys(bCmp);
        priority_queue<pair<int, int>, vector<pair<int, int>>, decltype(bCmp)> girls(bCmp);

        for(auto i:girlsIndegreeCount) {
            girls.push(make_pair(i.first, i.second));
        }
        for(auto i:boyOutdegree) {
            boys.push(make_pair(i.first, i.second));
        }

        int inviations = 0;

        while(!boys.empty() && !girls.empty()) {
            pair<int, int> b = boys.top();
            boys.pop();
            pair<int, int> g = girls.top();
            girls.pop();

            if(g.second < b.second) {

            }
            else if(b.second < g.second) {

            }
            else if(b.second == g.second) {

            }
        }

        return inviations;
    }
    // bool static bCmp(const pair<int, int> &a, const pair<int, int> &b) {
    //     return a.second < b.second;
    // }
    // bool static gCmp(const int &a, const int &b) {
    //     return girlsIndegreeCount[a] < girlsIndegreeCount[b];
    // }
};
```

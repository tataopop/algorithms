# UnionFind

### Leetcode 547. Number of Provinces

There are n cities. Some of them are connected, while some are not. If city a is connected directly with city b, and city b is connected directly with city c, then city a is connected indirectly with city c.

A province is a group of directly or indirectly connected cities and no other cities outside of the group.

You are given an n x n matrix isConnected where isConnected[i][j] = 1 if the ith city and the jth city are directly connected, and isConnected[i][j] = 0 otherwise.

Return the total number of provinces.

#### Example :
```
Input: isConnected = [[1,1,0],[1,1,0],[0,0,1]]
Output: 2
```

#### Solution :
```
class Solution {
    public int findCircleNum(int[][] M) {
        Uf uf = new Uf(M.length);
        for(int i = 0; i < M.length; i++) {
            for(int j = 0; j < M.length; j++) {
                if(M[i][j] == 1) uf.union(i, j);
            }
        }
        return uf.count;
    }

    class Uf {
        int[] parent;
        int count;

        public Uf(int n) {
            parent = new int[n];
            for(int i = 0; i < n; i++) {
                parent[i] = i;
            }
            count = n;
        }

        public int find(int i) {
            while(parent[i] != i) {
                parent[i] = parent[parent[i]];
                i = parent[i];
            }
            return i;
        }

        public void union(int i, int j) {
            int m = find(i);
            int n = find(j);
            if(m == n) return;
            count--;
            parent[n] = m;
        }
    }
}
```

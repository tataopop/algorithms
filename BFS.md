# BFS

### Leetcode 675 : Cut Off Trees for Golf Event

You are asked to cut off trees in a forest for a golf event. The forest is represented as a non-negative 2D map, in this map:
```
0 represents the obstacle can't be reached.
1 represents the ground can be walked through.
The place with number bigger than 1 represents a tree can be walked through, and this positive number represents the tree's height.
```

In one step you can walk in any of the four directions top, bottom, left and right also when standing in a point which is a tree you can decide whether or not to cut off the tree.

You are asked to cut off all the trees in this forest in the order of tree's height - always cut off the tree with lowest height first. And after cutting, the original place has the tree will become a grass (value 1).

You will start from the point (0, 0) and you should output the minimum steps you need to walk to cut off all the trees. If you can't cut off all the trees, output -1 in that situation.

You are guaranteed that no two trees have the same height and there is at least one tree needs to be cut off.

#### Example 1:
```
Input: 
[
 [1,2,3],
 [0,0,4],
 [7,6,5]
]
Output: 6
```

#### Solution :
```
class Solution {
    private int[][] dirs = new int[][]{{1, 0}, {-1, 0}, {0, 1}, {0, -1}};
    public int cutOffTree(List<List<Integer>> forest) {
        Queue<Integer> queue = new PriorityQueue<>((a,b) -> a - b);
        for(List<Integer> list: forest) {
            for(int h : list) {
                if(h > 1) queue.offer(h);
            }
        }
        int m = forest.size(), n = forest.get(0).size(), res = 0;
        int[] pos = new int[]{0, 0};
        while(!queue.isEmpty()) {
            int step = helper(queue.poll(), forest, pos);
            if(step == -1) return -1;
            res += step;
        }
        return res;
    }
    
    public int helper(int target, List<List<Integer>> forest, int[] pos) {
        int res = 0, m = forest.size(), n = forest.get(0).size();
        Queue<int[]> positions = new LinkedList<>();
        positions.add(pos);
        boolean[][] visited = new boolean[m][n];
        visited[pos[0]][pos[1]] = true;
        while(!positions.isEmpty()) {
            int size = positions.size();
            while(size-- > 0) {
                int[] cur = positions.poll();
                if(forest.get(cur[0]).get(cur[1]) == target) {
                    pos[0] = cur[0];
                    pos[1] = cur[1];
                    return res;
                }
                for(int[] dir : dirs) {
                    int x = cur[0] + dir[0], y = cur[1] + dir[1];
                        if(x < 0 || x >= m || y < 0 || y >= n || visited[x][y] || forest.get(x).get(y) == 0) continue;
                        visited[x][y] = true;
                        positions.add(new int[]{x, y});
                }
            }
            res++;
        }
        return -1;
    }
}
```

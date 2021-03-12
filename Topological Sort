# Topological Sort

### Leetcode 210. Course Schedule II

There are a total of n courses you have to take labelled from 0 to n - 1.

Some courses may have prerequisites, for example, if prerequisites[i] = [ai, bi] this means you must take the course bi before the course ai.

Given the total number of courses numCourses and a list of the prerequisite pairs, return the ordering of courses you should take to finish all courses.

If there are many valid answers, return any of them. If it is impossible to finish all courses, return an empty array.

#### Example :
```
Input: numCourses = 4, prerequisites = [[1,0],[2,0],[3,1],[3,2]]
Output: [0,2,1,3]
Explanation: There are a total of 4 courses to take. To take course 3 you should have finished both courses 1 and 2. Both courses 1 and 2 should be taken after you finished course 0.
So one correct course order is [0,1,2,3]. Another correct ordering is [0,2,1,3].
```

#### Solution :
```
class Solution {
    public int[] findOrder(int numCourses, int[][] prerequisites) {
        if(numCourses == 0) return new int[0];
        int[] indegree = new int[numCourses];
        int[] order = new int[numCourses];
        Map<Integer, Set<Integer>> map = new HashMap<>();
        for(int[] pre: prerequisites) {
            Set<Integer> set = map.getOrDefault(pre[1], new HashSet<>());
            set.add(pre[0]);
            map.put(pre[1], set); 
            indegree[pre[0]]++;
        }

        Queue<Integer> queue = new LinkedList<>();
        for(int i = 0; i < numCourses; i++) {
            if(indegree[i] == 0)
                queue.add(i);
        }
        int idx = 0;
        while(!queue.isEmpty()) {
            int cur = queue.poll();
            order[idx++] = cur;
            if(!map.containsKey(cur)) continue;
            for(int next: map.get(cur)) {
                if(--indegree[next] == 0)
                    queue.add(next);
            }
        }
        return idx == numCourses ? order : new int[0];
    }
}
```

# Geometry

### Leetcode 963. Minimum Area Rectangle II

Given a set of points in the xy-plane, determine the minimum area of any rectangle formed from these points, with sides not necessarily parallel to the x and y axes.

If there isn't any rectangle, return 0.

#### Example :
```
Input: [[3,1],[1,1],[0,1],[2,1],[3,3],[3,2],[0,2],[2,3]]
Output: 2.00000
Explanation: The minimum area rectangle occurs at [2,1],[2,3],[3,3],[3,1], with an area of 2.
```

#### Solution :
```
class Solution {
    public double minAreaFreeRect(int[][] p) {
        Map<String, List<int[]>> map = new HashMap<>();
        
        for(int i = 0; i < p.length; i++) {
            for(int j = i + 1; j < p.length; j++) {
                double x = (p[i][0] + p[j][0]) / 2.0;
                double y = (p[i][1] + p[j][1]) / 2.0;
                String key = x + ","+ y + "," + getDist(p, i, j);
                map.putIfAbsent(key, new ArrayList<>());
                map.get(key).add(new int[]{i, j});
            }
        }
        
        
        double res = Double.MAX_VALUE;
        for(List<int[]> l : map.values()) {
            for(int i = 0; i < l.size(); i++) {
                for(int j = i + 1; j < l.size(); j++) {
                    res = Math.min(res, getArea(p, l.get(i), l.get(j)));
                }
            }
        }
        
        return res == Double.MAX_VALUE ? 0 : res;
    }
    
    int getDist(int[][] p, int i, int j) {
        return (p[i][0]-p[j][0])*(p[i][0]-p[j][0]) + (p[i][1]-p[j][1])*(p[i][1]-p[j][1]);
    }
    
    double getArea(int[][] p, int[] a, int[] b) {
        int dis1 = getDist(p, a[0], b[0]);
        int dis2 = getDist(p, a[0], b[1]);
        return Math.sqrt(dis1) * Math.sqrt(dis2);
    }
}
```

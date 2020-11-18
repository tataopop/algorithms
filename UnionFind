# Union Find

```
class Uf {
    private int[] parent;
    public Uf(int n) {
        parent = new int[n];
        for(int i = 0; i < n; i++) {
            parent[i] = i;
        }
    }

    public int find(int i) {
        while(i != parent[i]) {
            parent[i] = parent[parent[i]];
            i = parent[i];
        }
        return i;
    }

    public void union(int i, int j) {
        parent[find(j)] = parent[i];
    }

    public boolean isConnected(int i, int j) {
        return find(i) == find(j);
    }

    public int count() {
        Set<Integer> set = new HashSet<>();
        for(int i = 0; i < parent.length; i++) {
            set.add(find(i));
        }
        return set.size();
    }
}
```

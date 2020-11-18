# Trie

Also called digital tree or prefix tree, is a kind of search tree—an ordered tree data structure used to store a dynamic set or associative array where the keys are usually strings.

```
class TrieNode {
    TrieNode[] children;
    String word;

    public TrieNode() {
        children = new TrieNode[26];
    }
}

private TrieNode build(String[] words) {
    TrieNode root = new TrieNode();
    for(String word : words) {
        TrieNode cur = root;
        for(char c : word.toCharArray()) {
            if(cur.children[c - 'a'] == null) cur.children[c - 'a'] = new TrieNode();
            cur = cur.children[c - 'a'];
        }
        cur.word = word;
    }
    return root;
}

```

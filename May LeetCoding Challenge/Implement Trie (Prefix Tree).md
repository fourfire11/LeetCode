# Implement Trie (Prefix Tree)

###### tags: `LeetCode`

## 題目

Implement a trie with `insert`, `search`, and `startsWith` methods.

**Example**

    Trie trie = new Trie();

    trie.insert("apple");
    trie.search("apple");   // returns true
    trie.search("app");     // returns false
    trie.startsWith("app"); // returns true
    trie.insert("app");   
    trie.search("app");     // returns true

:arrow_right:[題目連結](https://leetcode.com/explore/challenge/card/may-leetcoding-challenge/534/week-1-may-1st-may-7th/3329/)

## C++程式碼
```C++
class TrieNode {
public:
    bool isWord;
    TrieNode *chi[26];
    
    TrieNode() {
        isWord = false;
        for(int i=0; i<26; i++) chi[i] = nullptr;
    }
};
class Trie {
public:
    /** Initialize your data structure here. */
    TrieNode* root;
    Trie() {
        root = new TrieNode();    
    }
    
    /** Inserts a word into the trie. */
    void insert(string word) {
        TrieNode *r = root;
        for(int i=0; i<word.length(); i++){
            char ch = word.at(i);
            int d = ch - 'a';
            if (!r->chi[d]) r->chi[d] = new TrieNode();
            r = r->chi[d];
        }
        r->isWord = true;
    }
    
    /** Returns if the word is in the trie. */
    bool search(string word) {
        TrieNode *r = root;
        for(int i=0; i<word.length(); i++){
            char ch = word.at(i);
            int d = ch - 'a';
            if (!r->chi[d]) return false;
            r = r->chi[d];
        }
        if(r->isWord == true) return true;
        else return false;
    }
    
    /** Returns if there is any word in the trie that starts with the given prefix. */
    bool startsWith(string prefix) {
        TrieNode *r = root;
        for(int i=0; i<prefix.length(); i++){
            char ch = prefix.at(i);
            int d = ch - 'a';
            if (!r->chi[d]) return false;
            r = r->chi[d];
        }
        return true;
    }
};

/**
 * Your Trie object will be instantiated and called as such:
 * Trie* obj = new Trie();
 * obj->insert(word);
 * bool param_2 = obj->search(word);
 * bool param_3 = obj->startsWith(prefix);
 */

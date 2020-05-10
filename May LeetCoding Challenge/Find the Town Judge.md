# Find the Town Judge

###### tags: `LeetCode`

## 題目

In a town, there are `N` people labelled from `1` to `N`.  There is a rumor that one of these people is secretly the town judge.

If the town judge exists, then:

The town judge trusts nobody.
Everybody (except for the town judge) trusts the town judge.
There is exactly one person that satisfies properties 1 and 2.
You are given `trust`, an array of pairs `trust[i] = [a, b]` representing that the person labelled `a` trusts the person labelled `b`.

If the town judge exists and can be identified, return the label of the town judge.  Otherwise, return `-1`.
**Example 1:**

    Input: N = 2, trust = [[1,2]]
    Output: 2

**Example 2:**

    Input: N = 3, trust = [[1,3],[2,3]]
    Output: 3
    
**Example 3:**

    Input: N = 3, trust = [[1,3],[2,3],[3,1]]
    Output: -1
    
**Example 4:**

    Input: N = 3, trust = [[1,2],[2,3]]
    Output: -1
    
**Example 5:**

    Input: N = 4, trust = [[1,3],[1,4],[2,3],[2,4],[4,3]]
    Output: 3

:arrow_right:[題目連結](https://leetcode.com/explore/challenge/card/may-leetcoding-challenge/534/week-1-may-1st-may-7th/3325/)


## C++程式碼
```C++
class Solution {
public:
    int findJudge(int N, vector<vector<int>>& trust) {
        // initial Mcount = 0
        int Mcount[N];
        for(int i=0; i<N; i++) Mcount[i] = 0;
        
        // Mcount[i] : 信任一個人會消耗1，被一個人信任會增加1
        for(vector<vector<int> >::iterator it = trust.begin(); it != trust.end(); it++) {
            --Mcount[(*it).front()-1];
            ++Mcount[(*it).back()-1];
        }
        
        // judge 必得到N-1個人的信任(+N-1)，並且不信任任何人(-0)
        for(int i=0; i<N; i++) if(N-1==Mcount[i]) return i+1;
        
        return -1;
    }
};

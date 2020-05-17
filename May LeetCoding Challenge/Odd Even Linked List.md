#  Odd Even Linked List

###### tags: `LeetCode`

## 題目

Given a singly linked list, group all odd nodes together followed by the even nodes. Please note here we are talking about the node number and not the value in the nodes.

You should try to do it in place. The program should run in O(1) space complexity and O(nodes) time complexity.

**Example 1:**

    Input: 1->2->3->4->5->NULL
    Output: 1->3->5->2->4->NULL
    
**Example 2:**

    Input: 1->2->3->4->5->NULL
    Output: 1->3->5->2->4->NULL

:arrow_right:[題目連結](https://leetcode.com/explore/challenge/card/may-leetcoding-challenge/534/week-1-may-1st-may-7th/3331/)

## C++程式碼
```C++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* oddEvenList(ListNode* head) {
        if(!head) return head;
        
        ListNode* evenHead = head->next;
        ListNode* even = evenHead;
        ListNode* odd = head;
        
        // null even means that the number of node is odd
        // null even->next means that the number of node is even
        while(even && even->next){
            odd->next = even->next;
            odd = odd->next;
            
            even->next = odd->next;
            even = even->next;
        }
        odd->next = evenHead;
        return head;
    }
};

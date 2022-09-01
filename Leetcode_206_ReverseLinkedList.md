# Leetcode 206: Reverse Linked List

- [Link to Problem](https://leetcode.com/problems/reverse-linked-list/)

## Solution
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode reverseList(ListNode head) {
        if (head == null) return head;
        
        ListNode current = head;
        ListNode next = head.next;
        current.next = null;
        
        while(next != null) {
            head = next.next;
            next.next = current;
            current = next;
            next = head;
        }
        return current;
    }
}
```
# LeetCode 86: Partition List

### Difficulty: Medium

### Description:
Given a linked list and a value x, partition it such that all nodes less than x come before nodes greater than or equal to x.

You should preserve the original relative order of the nodes in each of the two partitions.

Example:
```
Input: head = 1->4->3->2->5->2, x = 3
Output: 1->2->2->4->3->5
```

### Thought:
1. Key point: Singly linked list, Create dummy head node
2. A dummy head node can reduce a lot of codes and error checking
3. Separate two partitons of list then merge them
4. Time complexity: O(N), only traverse once
5. Space complexity: O(1), with 2 additional nodes

### Code:
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x;  }
 * }
 */
class Solution {
    public ListNode partition(ListNode head, int x) {
        ListNode dummyLeftHead = new ListNode(0);
        ListNode dummyRightHead = new ListNode(0);
        ListNode leftRunner = dummyLeftHead;
        ListNode rightRunner = dummyRightHead;
        while (head != null) {
            if (head.val < x) {
                leftRunner.next = head;
                leftRunner = head;
            } else {
                rightRunner.next = head;
                rightRunner = head;
            }
            head = head.next;
        }
        rightRunner.next = null;
        leftRunner.next = dummyRightHead.next;
        return dummyLeftHead.next;
    }
}
```

### Result:
Runtime: 0 ms, faster than 100% of Java online submissions

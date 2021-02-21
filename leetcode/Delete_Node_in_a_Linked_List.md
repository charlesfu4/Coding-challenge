## Delete Node in a Linked List

Write a function to delete a node in a singly-linked list. You will not be given access to the head of the list, instead you will be given access to the node to be deleted directly.

It is guaranteed that the node to be deleted is not a tail node in the list.

<img src="https://assets.leetcode.com/uploads/2020/09/01/node1.jpg" />


### Solution

Since the interface only provide next() function to the object ListNode. We solve this problem by reassigning the node value and rewiring the node next node. If the node is null. Then we simply return.

```java
class Solution {
    public void deleteNode(ListNode node) {
        if(node == null)
            return;
        node.val = node.next.val;
        node.next = node.next.next;
    }
}
```



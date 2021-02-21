## 104. Maximum Depth of Binary Tree

Given the root of a binary tree, return its maximum depth.

A binary tree's maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

!(binary tree)[https://assets.leetcode.com/uploads/2020/11/26/tmp-tree.jpg]

### Failed: Reference Solution

```java
class Solution {
    public int maxDepth(TreeNode root) {
        if(root == null) return 0;
        return Math.max(maxDepth(root.left), maxDepth(root.right))+1;
    }
}
```

This recursive problem is too difficult for me when I am in bad mood. So the idea is to think it through reversely. Which means we have to divide the trees into subtrees and think from the endnodes. When the query node is null(the end nodes), we return 0 to jump back to previous stage in recursive branch. Meanwhile, we have to add 1 if the queried node is existed. However, each subbranch will have different height most of the time. We collect the deepest branch by using the max function everytime when the current node is not null. It assist us to obtain the correct height od the lower branches that can be passed upwards.

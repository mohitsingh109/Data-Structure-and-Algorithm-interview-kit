### Question:
https://leetcode.com/problems/kth-smallest-element-in-a-bst/

### Algo:
dfs

### Sol:
```
class Solution {
  public int kthSmallest(TreeNode root, int k) {
    LinkedList<TreeNode> stack = new LinkedList<TreeNode>();

    while (true) {
      while (root != null) {
        stack.add(root);
        root = root.left;
      }
      root = stack.removeLast();
      if (--k == 0) return root.val;
      root = root.right;
    }
  }
}
```

### Sol2
```
ref: https://www.geeksforgeeks.org/find-k-th-smallest-element-in-bst-order-statistics-in-bst/

Method 2: Augmented Tree Data Structure (O(h) Time Complexity and O(h) auxiliary space)
The idea is to maintain the rank of each node. We can keep track of elements in the left subtree of every node while building the tree. Since we need the K-th smallest element, we can maintain the number of elements of the left subtree in every node.
Assume that the root is having ‘lCount’ nodes in its left subtree. If K = lCount + 1, root is K-th node. If K < lCount + 1, we will continue our search (recursion) for the Kth smallest element in the left subtree of root. If K > lCount + 1, we continue our search in the right subtree for the (K – lCount – 1)-th smallest element. Note that we need the count of elements in the left subtree only.

// A BST node
class Node {
    int data;
    Node left, right;
    int lCount;
    Node(int x)
    {
        data = x;
        left = right = null;
        lCount = 0;
    }
}

public static Node insert(Node root, int x) {
    if (root == null)
        return new Node(x);

    // If a node is inserted in left subtree, then
    // lCount of this node is increased. For simplicity,
    // we are assuming that all keys (tried to be
    // inserted) are distinct.
    if (x < root.data) {
        root.left = insert(root.left, x);
        root.lCount++;
    }

    else if (x > root.data)
        root.right = insert(root.right, x);
    return root;
}
     
// Function to find k'th largest element in BST
// Here count denotes the number of
// nodes processed so far
public static Node kthSmallest(Node root, int k) {
    // base case
    if (root == null)
        return null;

    int count = root.lCount + 1;
    if (count == k)
        return root;

    if (count > k)
        return kthSmallest(root.left, k);

    // else search in right subtree
    return kthSmallest(root.right, k - count);
}

```

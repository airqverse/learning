# Trees

## 📋 Definition
> A hierarchical data structure consisting of nodes connected by edges. It has a single root node, and each node (except the root) has exactly one parent.

## ⚙️ Operations & Complexity (BST)
| Operation | Time Complexity (Balanced) | Time Complexity (Worst) |
| --------- | -------------------------- | ----------------------- |
| Search    | [[04_Complexity/O(log n) - Logarithmic\|O(log n)]] | [[04_Complexity/O(n) - Linear\|O(n)]] |
| Insertion | [[04_Complexity/O(log n) - Logarithmic\|O(log n)]] | [[04_Complexity/O(n) - Linear\|O(n)]] |
| Deletion  | [[04_Complexity/O(log n) - Logarithmic\|O(log n)]] | [[04_Complexity/O(n) - Linear\|O(n)]] |

## 🐍 Python Implementation
```python
class TreeNode:
    def __init__(self, val):
        self.val = val
        self.left = None
        self.right = None

# Binary Tree Construction
root = TreeNode(1)
root.left = TreeNode(2)
root.right = TreeNode(3)

# Simple In-order Traversal
def inorder(node):
    if node:
        inorder(node.left)
        print(node.val, end=" ")
        inorder(node.right)

inorder(root) # 2 1 3
```

## 💡 Use Cases & Notes
- **Use when**: Representing hierarchical relationships (file systems), efficient searching (BSTs), or prefix-based searching (Tries).
- **Key Concepts**: Root, Leaves, Height, Depth, Balancing (AVL, Red-Black).

---
[[00_Index/01_Data_Structures_MOC|Back to Data Structures Index]]
# Linked Lists

## 📋 Definition
> A linear data structure where elements (nodes) are not stored in contiguous memory locations. Each node contains a data field and a reference (link) to the next node in the sequence.

## ⚙️ Operations & Complexity
| Operation | Time Complexity | Space Complexity |
| --------- | --------------- | ---------------- |
| Access    | [[04_Complexity/O(n) - Linear\|O(n)]] | [[04_Complexity/O(1) - Constant\|O(1)]] |
| Search    | [[04_Complexity/O(n) - Linear\|O(n)]] | [[04_Complexity/O(1) - Constant\|O(1)]] |
| Insertion | [[04_Complexity/O(1) - Constant\|O(1)]] | [[04_Complexity/O(1) - Constant\|O(1)]] |
| Deletion  | [[04_Complexity/O(1) - Constant\|O(1)]] | [[04_Complexity/O(1) - Constant\|O(1)]] |

## 🐍 Python Implementation
```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None

    def append(self, data):
        new_node = Node(data)
        if not self.head:
            self.head = new_node
            return
        last = self.head
        while last.next:
            last = last.next
        last.next = new_node

    def display(self):
        curr = self.head
        while curr:
            print(curr.data, end=" -> ")
            curr = curr.next
        print("None")

# Usage
ll = LinkedList()
ll.append(1)
ll.append(2)
ll.append(3)
ll.display() # 1 -> 2 -> 3 -> None
```

## 💡 Use Cases & Notes
- **Use when**: You need constant time insertions and deletions (if the pointer to the location is known).
- **Don't use when**: You need frequent random access to elements.

---
[[00_Index/01_Data_Structures_MOC|Back to Data Structures Index]]
# Lowest Common Ancestor and network routing

## Problem 
Given a binary search tree (BST), find the lowest common ancestor (LCA) node of two given nodes in the BST.

According to the definition of LCA on Wikipedia: “The lowest common ancestor is defined between two nodes p and q as the lowest node in T that has both p and q as descendants (where we allow a node to be a descendant of itself).”

![Binary Search Tree](./assets/binarysearchtree_improved.png)

    Input: root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 8
    Output: 6
    Explanation: The LCA of nodes 2 and 8 is 6.

## Code
```
def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':

    cur = root

    while cur:
        if p.val > cur.val and q.val > cur.val:
            cur = cur.right
        elif p.val < cur.val and q.val < cur.val:
            cur = cur.left
        else:
            return cur
```


## Network routing
    Let's consider a simplified network topology represented as a tree, where:
    Nodes represent network devices (routers, switches, endpoints)
    Edges represent connections between devices
Here's a Python implementation demonstrating this concept:
```
class NetworkNode:
    def __init__(self, id):
        self.id = id
        self.left = None
        self.right = None

def lowestCommonAncestor(root, p, q):
    if not root or root == p or root == q:
        return root
    
    left = lowestCommonAncestor(root.left, p, q)
    right = lowestCommonAncestor(root.right, p, q)
    
    if left and right:
        return root
    return left if left else right

# Create a sample network topology
def create_network_topology():
    root = NetworkNode(1)  # Core router
    root.left = NetworkNode(2)  # Distribution switch 1
    root.right = NetworkNode(3)  # Distribution switch 2
    root.left.left = NetworkNode(4)  # Access switch 1
    root.left.right = NetworkNode(5)  # Access switch 2
    root.right.left = NetworkNode(6)  # Access switch 3
    root.right.right = NetworkNode(7)  # Access switch 4
    return root

# Find the optimal routing point between two network devices
def find_optimal_routing_point(topology, device1, device2):
    lca = lowestCommonAncestor(topology, device1, device2)
    return lca.id

# Example usage
network = create_network_topology()
device1 = network.left.left  # Device connected to Access switch 1
device2 = network.right.left  # Device connected to Access switch 3

optimal_router = find_optimal_routing_point(network, device1, device2)
print(f"The optimal routing point between devices {device1.id} and {device2.id} is router/switch {optimal_router}")
```
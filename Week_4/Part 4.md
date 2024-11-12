# Trees

Trees are a special kind of graphs. A tree is a **connected, acyclic, undirected graph**. 

![](20241109141326.png)

**Key Properties**
- **Root**: The topmost node in the tree, from which all nodes can be accessed. In a tree, there is exactly one root.
- **Parent and Child**: In a tree, each node (except the root) has exactly one **parent** node. A **parent** node can have zero or more **children**.
- **Leaf**: A node that does not have any children. It is also known as a **terminal node**.
- **Edge**: The connection between two nodes.
- **Path**: A sequence of nodes connected by edges.
- **Depth**: The number of edges from the root to the node.
- **Height**: The maximum depth of any node in the tree (or the depth of the deepest leaf).
- **Subtree**: A tree formed by a node and its descendants.
- **Degree**: The number of children a node has.
- **Level**: The level of a node is the number of edges from the root to that node. The root is at level 0.

Because trees are also graphs, we can use graph algorithms for trees such as **BFS** and **DFS**.


## Code

To represent trees in C++, we use classes.

```cpp
#include <iostream>
#include <vector>
using namespace std;

// Definition of a tree node
struct TreeNode {
    int data;                  // Value of the node
    vector<TreeNode*> children; // List of child nodes
    
    // Constructor to create a new node
    TreeNode(int val) : data(val) {}
};

// GeneralTree class to encapsulate tree operations
class GeneralTree {
public:
    TreeNode* root;

    GeneralTree() : root(nullptr) {}

    // Function to insert a child to a parent node
    void insert(int parentVal, int childVal) {
        if (root == nullptr) {
            root = new TreeNode(parentVal);  // Create the root if tree is empty
        }
        TreeNode* parentNode = search(root, parentVal);
        if (parentNode != nullptr) {
            parentNode->children.push_back(new TreeNode(childVal)); // Add child to parent
        } else {
            cout << "Parent node not found!" << endl;
        }
    }

    // Function to search for a node in the tree
    TreeNode* search(TreeNode* node, int val) {
        if (node == nullptr) {
            return nullptr;
        }

        // If the current node matches the value, return the node
        if (node->data == val) {
            return node;
        }

        // Search in all children
        for (TreeNode* child : node->children) {
            TreeNode* foundNode = search(child, val);
            if (foundNode != nullptr) {
                return foundNode;
            }
        }

        return nullptr; // Return null if not found
    }

    // Functions to perform tree traversals
    void preorder() { preorderRecursive(root); cout << endl; }
    void postorder() { postorderRecursive(root); cout << endl; }

private:
    // Helper function for preorder traversal
    void preorderRecursive(TreeNode* node) {
        if (node == nullptr) {
            return;
        }
        cout << node->data << " ";  // Visit node
        for (TreeNode* child : node->children) {
            preorderRecursive(child);  // Traverse child nodes
        }
    }

    // Helper function for postorder traversal
    void postorderRecursive(TreeNode* node) {
        if (node == nullptr) {
            return;
        }
        for (TreeNode* child : node->children) {
            postorderRecursive(child);  // Traverse child nodes
        }
        cout << node->data << " ";  // Visit node after children
    }
};

int main() {
    GeneralTree tree;

    // Insert nodes
    tree.insert(1, 2);  // Parent: 1, Child: 2
    tree.insert(1, 3);  // Parent: 1, Child: 3
    tree.insert(2, 4);  // Parent: 2, Child: 4
    tree.insert(2, 5);  // Parent: 2, Child: 5
    tree.insert(3, 6);  // Parent: 3, Child: 6
    tree.insert(3, 7);  // Parent: 3, Child: 7

    // Perform preorder and postorder traversal
    cout << "Pre-order traversal: ";
    tree.preorder();  // Output: 1 2 4 5 3 6 7

    cout << "Post-order traversal: ";
    tree.postorder();  // Output: 4 5 2 6 7 3 1

    return 0;
}

```

### Problems
 - https://cses.fi/problemset/task/1674
 - https://cses.fi/problemset/task/1131
 - https://cses.fi/problemset/task/1132
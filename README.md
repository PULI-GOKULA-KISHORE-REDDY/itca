# itca


Intro to Trees
Tree is a nonlinear data structure, and hence order of the elements are not important. It represents data in hierarchical form. On the other side, linked list, stacks, queues etc are linear data structures.

In trees each node point to more nodes in contrast to linked list where each node points to only one node.

Why Trees
It helps you to store the hierarchical information. e.g. DNS root to find IP address.
Trees can be traversed in a way that makes information easy to search.
Glossary
Lets take a look on following tree, and understand the terminology that follows:

Trees

Root - The root of a tree is the node with no parents. There can be at most one root node in the tree. In above tree 1 is the root of the tree.
Parent - The element directly above nodes are called its parent. e.g. 2 is parent of 4.
Children - The elements that are directly under an element are called its children. e.g. 4 and 5 are children of 2
Leaf Node - A node with no children is called leaf node. e.g. 4, 5, 6, 7 are leaf nodes
Siblings - Children of same parent are called siblings. e.g. 6 and 7 are siblings.
Height of tree - It is the length of path from the root to the deepest node in the tree. e.g. The height of above tree is 2.
Size of tree - The size of the tree is no of nodes present in the tree. e.g. Above tree has 7 nodes hence size of tree is 7.
Types of Trees
There are different type of trees depending on their structure and how the operations (insertion, deletion, traversal) are performed on them.

Binary Trees
Binary Search Trees(BST)
There are more type of trees. For now, lb ets try to understand Binary Trees and BST in more detail:

Binary Trees
A tree is called binary tree if each node has at most 2 children i.e. zero child, one child or two children, is called a binary tree. We name two children as left child and right child.

Empty tree is also a valid binary tree. We can visualize a binary tree as consisting of a root and two disjoint binary trees, called the left and right subtrees of the root.

Trees

Structure of Binary Trees
Binary Tree node contains data and two pointers to left child and right child.

A tree is represented by a pointer to the topmost node in tree. If the tree is empty, then value of root is NULL.

Trees

Basic Operations on Tree
Following are the basic operations on tree:

Inserting an element into a tree
Deleting an element from a tree
Searching for an element
Traversing the trees
Example
Lets consider following example of creating a tree with few nodes.

Create root of the tree. Suppose we want to create 1 as root of the tree. Create a node with the data and null left and right pointers.

Trees

Now, we want want to insert 2 to the left of root and 3 to the right of root. Create new nodes with given data and null left and right pointers.

Put 2 to the root->left and 3 to the root->right.

Now left and right pointers of root are no more null, but they point to the node with data 2 and 3.

Trees

Similarly, if we want want to insert 4 to the left of 2 and 5 to the right of 2.

Create new nodes with given data and null left and right pointers.

Put 4 to the root->left->left and 5 to the root->left->right.

Now left and right pointers of node(2) are no more null, but they point to the node with data 4 and 5.

Trees

Left and right pointers of node(3) still points to null.

Representation of Trees in C/C++
Declaration of Tree node:

struct node  
{ 
  int data; 
  struct node *left; 
  struct node *right; 
};
Function to implement trees in C/C++*

struct node* newnode(int data) 
{ 
  // Allocate memory for new node, assign data
  // create left right null pointers 
  
  struct node* node = (struct node*)malloc(sizeof(struct node)); 
  node->data = data; 
  node->left = NULL; 
  node->right = NULL; 
  return(node); 
} 
  
  
int main() 
{ 
  // Create root
  struct node *root = newnode(1);   
  
  // Put 2 and 3 on left and right of root
  root->left        = newnode(2); 
  root->right       = newnode(3); 
  
  // Put 4 and 5 on left and right of 2
  root->left->left  = newnode(4); 
  root->left->right = newnode(5);
  return 0; 
}
Representation of Trees in Java
Declaration of Tree Node:

class Node 
{ 
    int key; 
    Node left, right; 
  
    public Node(int item) 
    { 
        key = item; 
        left = right = null; 
    } 
} 
Function to implement trees in Java*

/* Class containing left and right child of current 
   node and key value*/
class Node 
{ 
    int key; 
    Node left, right; 
  
    public Node(int item) 
    { 
        key = item; 
        left = right = null; 
    } 
} 
  
// A Java program to introduce Binary Tree 
class BinaryTree 
{ 
    // Root of Binary Tree 
    Node root; 
  
    // Constructors 
    BinaryTree(int key) 
    { 
        root = new Node(key); 
    } 
  
    BinaryTree() 
    { 
        root = null; 
    } 
  
    public static void main(String[] args) 
    { 
        BinaryTree tree = new BinaryTree(); 
  
        // Create root with 1 as data
        tree.root = new Node(1); 
  
        // Put 2 to left of root and 3 to right of root
  
        tree.root.left = new Node(2); 
        tree.root.right = new Node(3); 
        
        // Put 4 to left of 2 and 5 to right of 2
        tree.root.left.left = new Node(4); 
        tree.root.left.right = new Node(5);
    } 
} 
Representation of Trees in Python
Declaration of Tree Node:

class Node: 
    def __init__(self,key): 
        self.left = None
        self.right = None
        self.val = key 
Function to implement trees in Python*

# Binary Tree 
class Node: 
    def __init__(self,key): 
        self.left = None
        self.right = None
        self.val = key 
  
  
# create root 
root = Node(1) 
 
# Put 2 to left of root, and 3 to right of left
root.left      = Node(2); 
root.right     = Node(3); 
    
# Put 4 to left of 2 and 5 to right of 2  
root.left.left  = Node(4); 
root.left.right = Node(5);
Intro to Binary Search Trees
In binary tree, we does not impose any restriction on how the element is inserted, deleted or traversed from the tree, hence it is not optimised when we want to insert or retrieve any element from the tree.

Hence we use binary Search trees, where we wants to optimise search, minimum, maximum operations. It impose restriction on the type of data a node will contain. BST has following properties -

The left subtree of a node contains only nodes with keys lesser than the node’s key.
The right subtree of a node contains only nodes with keys greater than the node’s key.
The left and right subtree each must also be a binary search tree.
There must be no duplicate nodes.
Average search operation is optimised to O(logn).
Example
Trees

Insertion of a key in BST
A new key is always inserted as a leaf in BST. We traverse through the tree and insert the key as we find its right place (Should be greater than its root if it is at its right, should be smaller than its root, if its at its left, and the subtree so formed should be a binary search tree only).

We start searching a key from root till we reach the leaf. Then the new node is added as a child of the leaf node.

Algorithm

Start traversing the tree from root.
Compare the element we want to insert with root, if it is less than root, then recurse for left, else recurse for right.
After the element the end, insert the element at the left of the node if it is less then current node, else right of the node.
Example
Lets consider following example of creating a tree with nodes 7, 3, 4, 12, 10.

Pick the first element i.e. 7, as there is no root, create a new node with 7 as data, and make it root.

Trees

Now the next key is 3. It is smaller than 7 hence we recurse to the left and insert it.

Trees

Now the next key is 4. It is smaller than 7 hence we recurse to the left. Now compare it with 3. It is greater than 3 and we recurse to the right and find leaf, hence insert it.

Trees

Now the next key is 12. It is greater than 7 hence we recurse to the right, and find leaf, hence insert it.

Trees

Now the next key is 15. It is greater than 7 hence we recurse to the right. Now compare it with 12. It is again greater than 12 and we recurse to the right and find leaf, hence insert it.

Trees

Function to insert key in BST
 
Node* insert(ode* node, int key) 
{ 
    // If the tree is empty, return a new node
    if (node == NULL) 
        {
            Node *newnode = (Node*) malloc (sizeof(Node));
            newnode->data = key;
            newnode->left = NULL;
            newnode->right = NULL;
            return newnode;
        }       
  
    // If key is smaller, recurse left else right
    if (key < node->key) 
        node->left  = insert(node->left, key); 
    else if (key > node->key) 
        node->right = insert(node->right, key);    
  
    return node; 
} 
def insert(node, key):
    
    # If the tree is empty, return a new node
    if (node == NULL): 
        
            newnode = len(Node)
            newnode.data = key
            newnode.left = NULL
            newnode.right = NULL
            return newnode
  
    # If key is smaller, recurse left else right
    if (key < node.key): 
        node.left  = insert(node.left, key) 
    elif (key > node.key): 
        node.right = insert(node.right, key)    
  
    return node 
Searching a key in BST
Given a key and the root of the Binary Search Tree, we have to find if the key is present in the tree or not. TO do this, we first compare the key with root, if the key is present at root, we return root. If key is greater than root’s key, we recur for right subtree of root node. Otherwise we recur for left subtree.

Example
Lets say, we want to search 5 in following BST

Trees

Here, root 7 is greater than 5 hence we recurse left subtree.

Trees

Here, root 3 is smaller than 5 hence we recurse right subtree. Now, when we compare root with key i.e. 5 with 5 we return true here.

Trees

Function to search key in BST
def search(root, key):
    
    # If root is null or key equals root, return root
    if (root == NULL or root.key == key): 
       return root 
     
    # Key is greater than root's key 
    if (root.key < key): 
       return search(root.right, key) 
  
    # Key is smaller than root's key 
    return search(root.left, key) 
 
Node* search(Node* root, int key) 
{ 
    // If root is null or key equals root, return root
    if (root == NULL || root->key == key) 
       return root; 
     
    // Key is greater than root's key 
    if (root->key < key) 
       return search(root->right, key); 
  
    // Key is smaller than root's key 
    return search(root->left, key); 
} 

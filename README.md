# 0x1D. C - Binary Trees

![Monty](https://i.pinimg.com/736x/eb/8e/f9/eb8ef9bf06e88b6ddc4032e5e8ed0be3.jpg)

## Description
This project focuses on implementing various binary tree operations and algorithms in C. A binary tree is a hierarchical data structure where each node has at most two children, referred to as the left child and the right child. This project covers fundamental tree operations, traversal algorithms, and different types of binary trees.

## Learning Objectives
By the end of this project, you should be able to:
- Understand what a binary tree is
- Differentiate between a binary tree and a Binary Search Tree
- Understand the possible gain in terms of time complexity compared to linked lists
- Know the depth, height, and size of a binary tree
- Understand different traversal methods to go through a binary tree
- Know what a complete, full, perfect, and balanced binary tree is

## Requirements
### General
- Allowed editors: vi, vim, emacs
- All files will be compiled on Ubuntu 20.04 LTS using gcc with options: `-Wall -Werror -Wextra -pedantic -std=gnu89`
- All files should end with a new line
- A `README.md` file at the root of the project folder is mandatory
- Your code should use the Betty style (checked using `betty-style.pl` and `betty-doc.pl`)
- No more than 5 functions per file
- You are allowed to use the standard library
- The prototypes of all functions should be included in a header file called `binary_trees.h`
- All header files should be include guarded

## Data Structure
Use this structure for this project:

```c
/**
 * struct binary_tree_s - Binary tree node
 *
 * @n: Integer stored in the node
 * @parent: Pointer to the parent node
 * @left: Pointer to the left child node
 * @right: Pointer to the right child node
 */
struct binary_tree_s
{
    int n;
    struct binary_tree_s *parent;
    struct binary_tree_s *left;
    struct binary_tree_s *right;
};

typedef struct binary_tree_s binary_tree_t;

/* Binary Search Tree */
typedef struct binary_tree_s bst_t;

/* AVL Tree */
typedef struct binary_tree_s avl_t;

/* Max Binary Heap */
typedef struct binary_tree_s heap_t;
```

## Print Function
To visualize your binary trees, use this print function:

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

/* binary_tree_print.c */
void binary_tree_print(const binary_tree_t *);
```

## Function Prototypes

### Basic Operations
```c
binary_tree_t *binary_tree_node(binary_tree_t *parent, int value);
binary_tree_t *binary_tree_insert_left(binary_tree_t *parent, int value);
binary_tree_t *binary_tree_insert_right(binary_tree_t *parent, int value);
void binary_tree_delete(binary_tree_t *tree);
int binary_tree_is_leaf(const binary_tree_t *node);
int binary_tree_is_root(const binary_tree_t *node);
```

### Traversal Functions
```c
void binary_tree_preorder(const binary_tree_t *tree, void (*func)(int));
void binary_tree_inorder(const binary_tree_t *tree, void (*func)(int));
void binary_tree_postorder(const binary_tree_t *tree, void (*func)(int));
void binary_tree_levelorder(const binary_tree_t *tree, void (*func)(int));
```

### Tree Properties
```c
size_t binary_tree_height(const binary_tree_t *tree);
size_t binary_tree_depth(const binary_tree_t *tree);
size_t binary_tree_size(const binary_tree_t *tree);
size_t binary_tree_leaves(const binary_tree_t *tree);
size_t binary_tree_nodes(const binary_tree_t *tree);
int binary_tree_balance(const binary_tree_t *tree);
int binary_tree_is_full(const binary_tree_t *tree);
int binary_tree_is_complete(const binary_tree_t *tree);
int binary_tree_is_perfect(const binary_tree_t *tree);
```

### Tree Relationships
```c
binary_tree_t *binary_tree_sibling(binary_tree_t *node);
binary_tree_t *binary_tree_uncle(binary_tree_t *node);
binary_tree_t *binary_trees_ancestor(const binary_tree_t *first, const binary_tree_t *second);
```

### Binary Search Tree
```c
int binary_tree_is_bst(const binary_tree_t *tree);
bst_t *bst_insert(bst_t **tree, int value);
bst_t *array_to_bst(int *array, size_t size);
bst_t *bst_search(const bst_t *tree, int value);
bst_t *bst_remove(bst_t *root, int value);
```

### AVL Tree
```c
int binary_tree_is_avl(const binary_tree_t *tree);
avl_t *avl_insert(avl_t **tree, int value);
avl_t *array_to_avl(int *array, size_t size);
avl_t *avl_remove(avl_t *root, int value);
avl_t *sorted_array_to_avl(int *array, size_t size);
```

### Binary Heap
```c
int binary_tree_is_heap(const binary_tree_t *tree);
heap_t *heap_insert(heap_t **root, int value);
heap_t *array_to_heap(int *array, size_t size);
int heap_extract(heap_t **root);
int *heap_to_sorted_array(heap_t *heap, size_t *size);
```

## Tasks

### Mandatory Tasks

#### 0. New node
Write a function that creates a binary tree node.
- **Prototype:** `binary_tree_t *binary_tree_node(binary_tree_t *parent, int value);`
- **Return:** pointer to the new node, or NULL on failure

#### 1. Insert left
Write a function that inserts a node as the left-child of another node.
- **Prototype:** `binary_tree_t *binary_tree_insert_left(binary_tree_t *parent, int value);`
- If parent already has a left-child, the new node takes its place and the old left-child becomes the left-child of the new node

#### 2. Insert right
Write a function that inserts a node as the right-child of another node.
- **Prototype:** `binary_tree_t *binary_tree_insert_right(binary_tree_t *parent, int value);`
- If parent already has a right-child, the new node takes its place and the old right-child becomes the right-child of the new node

#### 3. Delete
Write a function that deletes an entire binary tree.
- **Prototype:** `void binary_tree_delete(binary_tree_t *tree);`
- If tree is NULL, do nothing

#### 4. Is leaf
Write a function that checks if a node is a leaf.
- **Prototype:** `int binary_tree_is_leaf(const binary_tree_t *node);`
- **Return:** 1 if node is a leaf, 0 otherwise

#### 5. Is root
Write a function that checks if a given node is a root.
- **Prototype:** `int binary_tree_is_root(const binary_tree_t *node);`
- **Return:** 1 if node is a root, 0 otherwise

#### 6. Pre-order traversal
Write a function that goes through a binary tree using pre-order traversal.
- **Prototype:** `void binary_tree_preorder(const binary_tree_t *tree, void (*func)(int));`

#### 7. In-order traversal
Write a function that goes through a binary tree using in-order traversal.
- **Prototype:** `void binary_tree_inorder(const binary_tree_t *tree, void (*func)(int));`

#### 8. Post-order traversal
Write a function that goes through a binary tree using post-order traversal.
- **Prototype:** `void binary_tree_postorder(const binary_tree_t *tree, void (*func)(int));`

#### 9. Height
Write a function that measures the height of a binary tree.
- **Prototype:** `size_t binary_tree_height(const binary_tree_t *tree);`
- If tree is NULL, return 0

#### 10. Depth
Write a function that measures the depth of a node in a binary tree.
- **Prototype:** `size_t binary_tree_depth(const binary_tree_t *tree);`
- If tree is NULL, return 0

#### 11. Size
Write a function that measures the size of a binary tree.
- **Prototype:** `size_t binary_tree_size(const binary_tree_t *tree);`
- If tree is NULL, return 0

#### 12. Leaves
Write a function that counts the leaves in a binary tree.
- **Prototype:** `size_t binary_tree_leaves(const binary_tree_t *tree);`
- If tree is NULL, return 0

#### 13. Nodes
Write a function that counts the nodes with at least 1 child in a binary tree.
- **Prototype:** `size_t binary_tree_nodes(const binary_tree_t *tree);`
- If tree is NULL, return 0

#### 14. Balance factor
Write a function that measures the balance factor of a binary tree.
- **Prototype:** `int binary_tree_balance(const binary_tree_t *tree);`
- If tree is NULL, return 0

#### 15. Is full
Write a function that checks if a binary tree is full.
- **Prototype:** `int binary_tree_is_full(const binary_tree_t *tree);`
- If tree is NULL, return 0

#### 16. Is perfect
Write a function that checks if a binary tree is perfect.
- **Prototype:** `int binary_tree_is_perfect(const binary_tree_t *tree);`
- If tree is NULL, return 0

#### 17. Sibling
Write a function that finds the sibling of a node.
- **Prototype:** `binary_tree_t *binary_tree_sibling(binary_tree_t *node);`
- **Return:** pointer to the sibling node, or NULL if no sibling

#### 18. Uncle
Write a function that finds the uncle of a node.
- **Prototype:** `binary_tree_t *binary_tree_uncle(binary_tree_t *node);`
- **Return:** pointer to the uncle node, or NULL if no uncle

### Advanced Tasks

#### 19. Lowest common ancestor
Write a function that finds the lowest common ancestor of two nodes.
- **Prototype:** `binary_tree_t *binary_trees_ancestor(const binary_tree_t *first, const binary_tree_t *second);`

#### 20. Level-order traversal
Write a function that goes through a binary tree using level-order traversal.
- **Prototype:** `void binary_tree_levelorder(const binary_tree_t *tree, void (*func)(int));`

#### 21. Is complete
Write a function that checks if a binary tree is complete.
- **Prototype:** `int binary_tree_is_complete(const binary_tree_t *tree);`

#### 22. Rotate left
Write a function that performs a left-rotation on a binary tree.
- **Prototype:** `binary_tree_t *binary_tree_rotate_left(binary_tree_t *tree);`

#### 23. Rotate right
Write a function that performs a right-rotation on a binary tree.
- **Prototype:** `binary_tree_t *binary_tree_rotate_right(binary_tree_t *tree);`

#### 24. Is BST
Write a function that checks if a binary tree is a valid Binary Search Tree.
- **Prototype:** `int binary_tree_is_bst(const binary_tree_t *tree);`

#### 25. BST - Insert
Write a function that inserts a value in a Binary Search Tree.
- **Prototype:** `bst_t *bst_insert(bst_t **tree, int value);`

#### 26. BST - Array to BST
Write a function that builds a Binary Search Tree from an array.
- **Prototype:** `bst_t *array_to_bst(int *array, size_t size);`

#### 27. BST - Search
Write a function that searches for a value in a Binary Search Tree.
- **Prototype:** `bst_t *bst_search(const bst_t *tree, int value);`

#### 28. BST - Remove
Write a function that removes a node from a Binary Search Tree.
- **Prototype:** `bst_t *bst_remove(bst_t *root, int value);`

#### 29. Big O #BST
What are the average time complexities of those operations on a Binary Search Tree?
- Inserting the value n
- Removing the node with the value n  
- Searching for a node with the value n

#### 30. Is AVL
Write a function that checks if a binary tree is a valid AVL Tree.
- **Prototype:** `int binary_tree_is_avl(const binary_tree_t *tree);`

#### 31. AVL - Insert
Write a function that inserts a value in an AVL Tree.
- **Prototype:** `avl_t *avl_insert(avl_t **tree, int value);`

#### 32. AVL - Array to AVL
Write a function that builds an AVL tree from an array.
- **Prototype:** `avl_t *array_to_avl(int *array, size_t size);`

#### 33. AVL - Remove
Write a function that removes a node from an AVL tree.
- **Prototype:** `avl_t *avl_remove(avl_t *root, int value);`

#### 34. AVL - From sorted array
Write a function that builds an AVL tree from a sorted array.
- **Prototype:** `avl_t *sorted_array_to_avl(int *array, size_t size);`

#### 35. Big O #AVL Tree
What are the average time complexities of those operations on an AVL Tree?
- Inserting the value n
- Removing the node with the value n
- Searching for a node with the value n

#### 36. Is Binary heap
Write a function that checks if a binary tree is a valid Max Binary Heap.
- **Prototype:** `int binary_tree_is_heap(const binary_tree_t *tree);`

#### 37. Heap - Insert
Write a function that inserts a value in Max Binary Heap.
- **Prototype:** `heap_t *heap_insert(heap_t **root, int value);`

#### 38. Heap - Array to Binary Heap
Write a function that builds a Max Binary Heap tree from an array.
- **Prototype:** `heap_t *array_to_heap(int *array, size_t size);`

#### 39. Heap - Extract
Write a function that extracts the root node of a Max Binary Heap.
- **Prototype:** `int heap_extract(heap_t **root);`

#### 40. Heap - Sort
Write a function that converts a Binary Max Heap to a sorted array of integers.
- **Prototype:** `int *heap_to_sorted_array(heap_t *heap, size_t *size);`

#### 41. Big O #Binary Heap
What are the average time complexities of those operations on a Binary Heap?
- Inserting the value n
- Extracting the root node
- Searching for a node with the value n

## Key Concepts

### Tree Terminology
- **Node:** Basic unit of a tree containing data and pointers to children
- **Root:** Top node of the tree with no parent
- **Leaf:** Node with no children
- **Height:** Number of edges on the longest path from node to a leaf
- **Depth:** Number of edges from root to the node
- **Level:** All nodes at the same depth

### Tree Types
- **Full Binary Tree:** Every node has either 0 or 2 children
- **Complete Binary Tree:** All levels are filled except possibly the last level
- **Perfect Binary Tree:** All internal nodes have 2 children and all leaves are at the same level
- **Balanced Binary Tree:** Height difference between left and right subtrees is at most 1

### Binary Search Tree (BST)
- Left subtree contains only nodes with values less than the parent node
- Right subtree contains only nodes with values greater than the parent node
- Both left and right subtrees are also binary search trees

### AVL Tree
- Self-balancing Binary Search Tree
- Height difference between left and right subtrees is at most 1
- Automatically maintains balance through rotations

### Binary Heap
- Complete binary tree
- Max Heap: Parent node is greater than or equal to its children
- Min Heap: Parent node is less than or equal to its children

## Compilation
All files are compiled with:
```bash
gcc -Wall -pedantic -Werror -Wextra -std=gnu89 *.c -o [executable_name]
```

## Testing
Each task includes a main file for testing. Use the provided `binary_tree_print.c` to visualize your trees:

```bash
gcc -Wall -Wextra -Werror -pedantic binary_tree_print.c 0-main.c 0-binary_tree_node.c -o 0-node
./0-node
```

## Memory Management
- Always free allocated memory when the tree is no longer needed
- Use `binary_tree_delete()` to properly deallocate entire trees
- Handle edge cases where nodes or trees might be NULL
- Check for successful memory allocation before using malloc'ed memory

## Author
ALX Software Engineering Program - Binary Trees Project

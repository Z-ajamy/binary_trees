# Tests Directory

![Binary Trees test](https://i.pinimg.com/736x/47/66/09/4766091a460842c56030f449fb8c4e20.jpg)

This directory contains test files and resources for the Binary Trees project.

## Running Tests

To compile and run tests for binary tree functions:

```bash
# Compile with test files
gcc -Wall -Wextra -Werror -pedantic binary_tree_print.c [task_file.c] [test_file.c] -o test

# Run the test
./test

# Example for specific tasks
gcc -Wall -Wextra -Werror -pedantic binary_tree_print.c 0-binary_tree_node.c 0-main.c -o 0-node
./0-node
```

## Test Categories

### Node Operations
- Node creation and initialization
- Memory allocation and deallocation
- Parent-child relationships
- Node data integrity

### Tree Traversal
- Pre-order traversal
- In-order traversal  
- Post-order traversal
- Level-order traversal
- Tree printing and visualization

### Tree Properties
- Tree height and depth calculations
- Node counting (leaves, internal nodes, total)
- Tree balance verification
- Size and structure validation

### Tree Modifications
- Node insertion at various positions
- Node deletion and tree restructuring
- Tree rotations
- Subtree operations

### Tree Types
- Binary Search Tree operations
- AVL tree properties
- Heap properties
- Complete and perfect tree validation

### Edge Cases
- Empty trees (NULL root)
- Single node trees
- Unbalanced trees
- Maximum depth scenarios
- Memory allocation failures

## Test File Structure

Test files typically follow this pattern:
- `[task_number]-main.c` - Test file for specific task
- `binary_tree_print.c` - Tree visualization helper
- `binary_trees.h` - Header with function prototypes

Example test structure:
```c
#include "binary_trees.h"

int main(void)
{
    binary_tree_t *root;
    
    root = binary_tree_node(NULL, 98);
    // Test operations...
    binary_tree_print(root);
    
    return (0);
}
```

## Adding New Tests

When creating new test files:
- Use clear, descriptive test scenarios
- Test both normal operations and edge cases
- Include visual output using `binary_tree_print()` when helpful
- Verify memory management and proper cleanup
- Test with various tree structures and sizes

## Helper Functions

The `binary_tree_print.c` file provides visualization capabilities:
- Displays tree structure in a readable format
- Useful for debugging and verifying tree operations
- Should be included in compilation for visual tests

## Notes

- Tests should validate both functionality and memory management
- Consider testing with different tree shapes and sizes
- Verify proper handling of NULL pointers and edge conditions  
- Test files can be organized by task number or functionality
- Use valgrind to check for memory leaks when available

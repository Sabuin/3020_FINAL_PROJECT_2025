# 3020_FINAL_PROJECT_2025
### Brodie A. Duprey & Sasha J. Abuin
This project extends our compiler to support more advanced language features and typing strategies. Our main goals were to implement **gradual typing, improve performance through some optimizations, and expand the compiler's capabilities to include string manipulation and floating-point arithmetic** These changes required careful updates mainly in our type-checker and select-instructions passes, as well as the addition of two new passes and inject & project functions. 

## Compiler Changes
### String_to_tuple pass
This pass is a transformation stage in the compiler that converts string constants into tuples of their ASCII values. 

### Type checker pass
We extended the type checker pass to support floats and string operations. 
* For float support, the arithmetic operations (add, sub, mult) were updated to accept both int and float types.
* For strings, we added handling for string constants by converting them into tuples of integer ASCII values in an earlier pass. The type checker recognizes these tuples and supports subscript operations on them. Additionally, we enabled string concatenation by treating it as tuple concatenation, verifying that both operands are tuples of the same type. 

### Select instructions 
We extended the select_instructions pass to support operations involving strings and floats. 

* For strings, which are represented as tuples of ASCII values, we added logic to handle tuple allocation, subscripting, and concatenation at the assembly level.
  * Specifically, string concatenation is implemented by allocating a new tuple, computing the combined tag, and copying elements from the original tuples into the newly allocated memory.
  * For printing, if the argument is a tuple (i.e., a string), each character is printed sequentially using print_int after being loaded from memory.
  
* For float operations, we treat them uniformly with integer operations during instruction selection by mapping them to the same x86 arithmetic instructions (Addq, Subq, Imulq). This approach assumes that float and int operations are handled equivalently at the instruction level for simplicity.

### Inject & Project
To support gradual typing and runtime type tagging, we added two helper assembly routines: inject and project, included via the add_inject and add_project functions. These routines allow values to be tagged or untagged with type information at runtime. 

### Remove Redundancies pass
As part of our optimization efforts, we implemented a *remove_redundancies* pass to eliminate unnecessary instructions in the generated x86-like assembly. Specifically, this pass removes redundant *movq* instructions where a register is moved to itself (e.g., movq %rax, %rax), which are semantically useless and only increase code size and execution time. The optimization traverses each function’s instruction blocks and filters out such instructions. While simple, this "cleanup" helps produce more efficient and readable output code by reducing redundancy in register assignments.

*Note: we have not tested this but we hope that in theory it works* 

## Features left to implement
DISCUSS DURING FINAL MEETING. 

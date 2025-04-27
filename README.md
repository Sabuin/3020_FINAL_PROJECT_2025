# 3020_FINAL_PROJECT_2025

## SCHEDULE
- [x] Thursday 24th - Floating point numbers and start string
- [ ] Sunday 27th - write project milestone
- [ ] Tuesday 29th - Start dynamic typing --> implement gradual dynamic typing. 
- [ ] Thursday May 1st - Work through new passes + write test cases
- [ ] Sunday May 4th - finish code, readme, video, submit everything

## TODO's
- [ ] Dynamic Typing
  - [ ] Modification 
  - [ ] def cast_inertion pass 
    - [ ] converts subexpressions into "anytype" object 
  - [ ] def reveal_casts pass
    - [ ] makes two new AST classes
    
- [ ] Strings
  - [x] In cs 3020 support directory, in python_parser.py
        - Modify constant case to have an assertion like `assert isinstance(c, (bool, int, str))`

  - [ ] Add support for string creation
    - [ ] Select-instructions: turn a string constant into a tuple holding ascii codes for the string's characters
    - [ ] copy/paste tuple construction case and just use the ord function to turn characters into numbers. 
  - [ ] Add support for string printing
    - [ ] Change the print case in select instructions
    - [ ] Option 1: implement print_str in the runtime.c
    - [ ] Option 2:  print strings by repeatedly printing ascii codes of the characters of the string (using print_int) 
  - [ ] Typechecker 
- [ ] Prim: concat
    - [ ] Allocate a new string that can hold the concatenation of both strings.
    - [ ] Copy characters from the two strings.
    - [ ] Implement this in select-instructions.
        
- [ ] Floating point numbers
  - [ ] Typechecker

- [ ] Optimizations 

## QUESTIONS FOR OFFICE HOURS
- [ ] We are adding floats. We changed python_parser.py, eval_x86.py (added classes). 
    - x86 parser is not liking floats. Our output when we run is --> line 96 in parser "invalid literal for int"

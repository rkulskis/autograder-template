# Autograder template
This template allows for course staff to easily create new assignments with 
maximal automation and speed.

## Getting started
### Demo
```bash
# generate tests and starter_code/classlib.py = subset of top-level classlib.py
# where only functions used in solution.py are included.
cd PA-template
make
cd starter_code
make				# runs all starter_code tests on submission.py
make T=1			# runs only test 1
cd ../autograder
make				# test submission.py against all autograder/tests
```

Run `make zip` inside `starter_code/` and `autograder/` to get zip files for 
`starter_code.zip` (for students) and `autograder.zip` (upload to gradescope).

### Customization
To port to your own assignment add your:
1. Library functions for the class to `classlib.py`
2. Test creation code to `create_assignment_files.py`
2. Test verification code to `test.py`
3. Write a solution in `solution.py`
   * Run `make` inside `starter_code

## Background
Below is a `tree` of the code including descriptions for the files and how to use
them. The template code just generates random graph tests for an assignment
which has one function, `doubleEdgeWeights()`. It generates 12 tests in
`create_assignment_files.py` against which to test `submission.py` code.

This structure is targeted toward comparing output files from python code
submissions, but can be extended to other languages as needed.
 
### Tree
```bash
⭐: Modify these files to make new assignment
⚙️: Autogenerated files
.
├── PA-template
│   ├── autograder
│   │   ├── Makefile
│   │   ├── run_autograder
│   │   ├── run_tests.py
│   │   ├── setup.sh
│   │   └── tests 
│   │       ├── classlib.py -> ../../../classlib.py
│   │       ├── test.py ⭐
│   │       └── {after_due_date,after_published,hidden,visible} ⚙️
│   │           ├── inputs ⚙️
│   │           │   └── input{%2d}.txt ⚙️
│   │           └── outputs ⚙️
│   │               └── output{%2d}.txt ⚙️
│   ├── create_assignment_files.py ⭐
│   ├── Makefile
│   ├── classlib.py -> ../classlib.py
│   ├── solution.py ⭐
│   └── starter_code
│       ├── submission.py ⭐
│       ├── README.md ⭐
│       ├── inputs -> ../autograder/tests/visible/inputs ⚙️
│       ├── outputs -> ../autograder/tests/visible/outputs ⚙️
│       └── classlib.py ⚙️
├── README.md
└── classlib.py ⭐
```

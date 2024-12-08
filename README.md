# Autograder template
This template allows for course staff to easily create new assignments with 
maximal automation and speed.

To pull this framework into an existing autograder repository run:
```
git remote add upstream git@github.com:rkulskis/autograder-template.git
git remote set-url --push upstream no_push
git config --global merge.keeporigin.driver "cp -f %A %O"
echo "classlib.py merge=keeporigin" > .gitattributes
git pull upstream main --allow-unrelated-histories
```

## Getting started
### Demo
```bash
make demo
```

Run `make zip` inside `starter_code/` and `autograder/` to get zip files for 
`starter_code.zip` (for students) and `autograder.zip` (upload to gradescope).

### Customization
To port to your own assignment add your:
1. Library functions for the class to `classlib.py`
2. Test creation code to `create_assignment_files.py`
   * Run `make` in same directory to call this
2. Test verification code to `test.py`
3. Write a solution in `solution/submission.py`
   * Run `make` inside `starter_code/`
   * Run `make` inside `autograder/`

## Background
Below is a `tree` of the code including descriptions for the files and how to use
them. The template code just generates random graph tests for an assignment
which has one function, `doubleEdgeWeights()`.

This structure is targeted toward comparing output files from python code
submissions, but can be extended to other languages as needed.
 
### Tree
```bash
⭐: Modify these files to make a new assignment
.
├── Makefile
├── PA-template
│   ├── assignment-description.pdf
│   ├── assignment-description.tex ⭐
│   ├── autograder
│   │   ├── Makefile
│   │   ├── requirements.txt
│   │   ├── run_autograder
│   │   ├── run_tests.py
│   │   ├── setup.sh
│   │   └── tests
│   │       └── test.py ⭐
│   ├── create_assignment_files.py ⭐
│   └── Makefile
├── problems ⭐
│   ├── classlib.py
│   ├── DoubleEdgeWeights.py
│   └── problem.py
└── README.md
```
### Tree (with autogenerated files)
```bash
KEY:
⚙️: Autogenerated files using Makefile
.
├── Makefile
├── PA-template
│   ├── assignment-description.pdf
│   ├── assignment-description.tex
│   ├── autograder
│   │   ├── classlib.py ⚙️
│   │   ├── Makefile
│   │   ├── requirements.txt
│   │   ├── run_autograder
│   │   ├── run_tests.py
│   │   ├── setup.sh
│   │   ├── submission.py -> ../starter_code/submission.py ⚙️
│   │   └── tests
│   │       ├── {after_due_date, after_published, hidden, visible} ⚙️
│   │       │   ├── inputs
│   │       │   │   └── input{%2d}.txt
│   │       │   └── outputs
│   │       │       └── output{%2d}.txt
│   │       ├── problems ⚙️
│   │       │   ├── {problems_for_this_PA}.py
│   │       │   └── problem.py
│   │       ├── test_descriptions.txt ⚙️
│   │       └── test.py
│   ├── autograder.zip ⚙️
│   ├── classlib.py -> ../problems/classlib.py ⚙️
│   ├── create_assignment_files.py
│   ├── Makefile
│   ├── problems -> ../problems ⚙️
│   ├── solution ⚙️
│   │   └── submission.py
│   ├── starter_code ⚙️
│   │   ├── assignment-description.pdf -> ../assignment-description.pdf
│   │   ├── classlib.py
│   │   ├── dist
│   │   │   ├── classlib.py
│   │   │   ├── problems
│   │   │   │   ├── {problems_for_this_PA}.py
│   │   │   │   └── problem.py
│   │   │   ├── pyarmor_runtime_000000
│   │   │   │   ├── darwin_x86_64
│   │   │   │   │   └── pyarmor_runtime.so
│   │   │   │   ├── __init__.py
│   │   │   │   ├── linux_x86_64
│   │   │   │   │   └── pyarmor_runtime.so
│   │   │   │   ├── __pycache__
│   │   │   │   │   └── __init__.cpython-312.pyc
│   │   │   │   └── windows_x86_64
│   │   │   │       └── pyarmor_runtime.pyd
│   │   │   └── test.py
│   │   ├── Makefile
│   │   ├── student_output.txt
│   │   ├── submission.py
│   │   └── tests
│   │       ├── inputs -> ../../autograder/tests/visible/inputs
│   │       ├── outputs -> ../../autograder/tests/visible/outputs
│   │       └── test_descriptions.txt -> ../../autograder/tests/test_descriptions.txt
│   └── starter_code.zip ⚙️
├── problems
│   ├── classlib.py
│   ├── DoubleEdgeWeights.py
│   └── problem.py
└── README.md
```

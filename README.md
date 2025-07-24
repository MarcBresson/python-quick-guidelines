# Python quick guidelines

The quality of the code can be assessed by how much time it takes to a new developer to understand what your code is doing.

Use a linter to help you practice these guidelines. I recommend [ruff](https://docs.astral.sh/ruff/) that check the style and quality of your python code.

# Quick guidelines

- keep your functions short (less than 30 lines)
- use docstring to document the modules, functions and classes
- respect naming conventions (use the right case at the right place)
- keep your lines short (less than 99 characters) by breaking them at the right place

# Naming convention

It exists a few cases used throughout python:
- the snake_case [more info](https://en.wikipedia.org/wiki/Snake_case): in lowercase with words separated by underscores.
- the PascalCase (or UpperCamelCase) [more info](https://en.wikipedia.org/wiki/Camel_case): Start each word with a capital letter. Do not separate words with underscores.
- the UPPERCASE for constants: everything in caps with words separated by underscores.

| Type | Naming Convention | Examples |
| ---- | ----------------- | -------- |
| Function | snake_case | function, my_function |
| Variable | snake_case | x, var, my_variable |
| Class | PascalCase | Model, MyClass |
| Method | snake_case | class_method, method |
| Constant | Use an uppercase single letter, word, or words. Separate words with underscores to improve readability. | CONSTANT, MY_CONSTANT, MY_LONG_CONSTANT |
| Module | snake_case, keep short | module.py, my_module.py |
| Package | lowercase, keep short, avoid underscores | package, mypackage |


# Code layout

## Blank lines

_From [https://peps.python.org/pep-0008/#blank-lines](https://peps.python.org/pep-0008/#blank-lines):_

Surround top-level function and class definitions with two blank lines.

Method definitions inside a class are surrounded by a single blank line.

Extra blank lines may be used (sparingly) to separate groups of related functions. Blank lines may be omitted between a bunch of related one-liners (e.g. a set of dummy implementations).

Use blank lines in functions, sparingly, to indicate logical sections.


### Examples
<details>

```python
def foo(): # top-level function
    something = 5


def bar(): # top-level function
    somethingelse = 42
```

```python
class A: # class
    CONSTANT = 2

    def foo(self): # method
        """bla.
        
        Returns
        -------
        int:
            the bla.
        """
        bla = self.CONSTANT

        return bla

    def bar(self, height: int = 10): # method
        """Compute the height.
        
        Parameters
        ----------
        height : int
            the new height.
        """
        bla = height


class B: # class
    pass
```
</details>

## Line length

for code lines, PEP8 recommands not to exceed 99 characters and advice to [stick to 79 characters](https://peps.python.org/pep-0008/#maximum-line-length). Do not make your variable name cryptic in order to meet this guideline.

comments and docstrings must be wrapped at 72 characters.

## Line breaking and indentation

Use 4 spaces indentation except for line continuation and in [hanging indent](https://peps.python.org/pep-0008/#fn-hi).

Because it can be hard to keep a line under the limit of 99 characters, you can use line breaking. Python will assume line continuation when code is inside parenthesis.

```python
# Aligned with opening delimiter.
foo = long_function_name(var_one, var_two,
                         var_three, var_four)

# Hanging indents should add a level.
foo = long_function_name(
    var_one, var_two,
    var_three, var_four)

# Add an extra level of indentation to distinguish arguments from the rest.
def long_function_name(
        var_one, var_two, var_three,
        var_four):
    print(var_one)
```

The closing brace/bracket/parenthesis on multiline constructs may be lined up under the first character of the line that starts the multiline construct.

```python
my_list = [
    1, 2, 3,
    4, 5, 6,
]
result = some_function_that_takes_arguments(
    'a', 'b', 'c',
    'd', 'e', 'f',
)
```

You can also break the line before using an operator.

```python
income = (gross_wages
          + taxable_interest
          + (dividends - qualified_dividends)
          - ira_deduction
          - student_loan_interest)
```

## Comments

Use inline comments sparingly. Comments should answer the question "why?" since the "what?" question can be answered by reading your code (which is hoopefully clear enough).

## Docstrings

Python has no convention for docstrings, but [numpy docstring convention](https://numpydoc.readthedocs.io/en/latest/format.html) exists. See [this summary of guidelines](https://github.com/MarcBresson/write-better-commit-messages) for more information.

## Imports order

We can distinguish 3 types of python import:
- the [standard library](https://docs.python.org/3/library/). It is including by default and does not need to be installed via pip. You can find pathlib, os, random, multiprocessing and many more.
- the external packages like numpy, pandas or matplotlib. They have to be installed via pip
- the internal packages or modules. They are references to your own code.

You should include them in the presented order i.e., the modules from the standard library, the external packages, the internal packages.

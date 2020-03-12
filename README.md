* [Tools](#tools)
  * [Command-line interface](#command-line-interface)
  * [Coding style](#coding-style)
  * [Documentation](#documentation)
  * [Testing](#testing)
  * [Profiling](#profiling)
  * [Fast computing](#fast-computing)
  * [Build and Interpreter](#build-and-interpreter)
  * [Continuous integration](#continuous-integration)
* [Cool libraries](#cool-libraries)
  * [Visualisation](#visualisation)
  * [Automatic differentiation](#automatic-differentiation)
* [Resources](#resources)

# Tools

## Command-line interface

### [argparse](https://docs.python.org/3/library/argparse.html)
> The argparse module makes it easy to write user-friendly command-line interfaces. The program defines what arguments it requires, and argparse will figure out how to parse those out of sys.argv. The argparse module also automatically generates help and usage messages and issues errors when users give the program invalid arguments

### [docopt](https://github.com/docopt/docopt)
> Isn't it awesome how argparse generate help messages based on your code?!
> Hell no! You know what's awesome? It's when the option parser is generated based on the beautiful help message that you write yourself! This way you don't need to write this stupid repeatable parser-code, and instead can write only the help message--the way you want it.

## Coding style

### [pycodestyle](http://pycodestyle.pycqa.org/en/latest/intro.html)
> Pycodestyle is a tool to check your Python code against some of the style conventions in PEP 8.

### [pylint](https://www.pylint.org/)
> Code analysis for Python: standards, errors, refactoring, customizable

### [pyflakes](https://github.com/PyCQA/pyflakes)
> A simple program which checks Python source files for errors
> Pyflakes is also faster than Pylint or Pychecker. This is largely because Pyflakes only examines the syntax tree of each file individually. As a consequence, Pyflakes is more limited in the types of things it can check

### [flakes8](https://flake8.pycqa.org/en/latest/)
> flake8 is a command-line utility for enforcing style consistency across Python projects. By default it includes lint checks provided by the PyFlakes project, PEP-0008 inspired style checks provided by the PyCodeStyle project

### [autopep8](https://github.com/hhatto/autopep8)
> A tool that automatically formats Python code to conform to the PEP 8 style guide

## Documentation

### [sphinx](https://www.sphinx-doc.org/en/master/)
> Sphinx is a tool that makes it easy to create intelligent and beautiful documentation, written by Georg Brandl and licensed under the BSD license.

### [Read The Docs](https://docs.readthedocs.io/en/stable/) with [sphinx](https://docs.readthedocs.io/en/stable/intro/getting-started-with-sphinx.html)
> Read the Docs simplifies software documentation by automating building, versioning, and hosting of your docs for you. Think of it as Continuous Documentation.

## Testing

### [unittest](https://docs.python.org/3/library/unittest.html) 
> The unittest unit testing framework was originally inspired by JUnit and has a similar flavor as major unit testing frameworks in other languages. It supports test automation, sharing of setup and shutdown code for tests, aggregation of tests into collections, and independence of the tests from the reporting framework.

```
import unittest
 
class TestBidule(unittest.TestCase):
 
    def test_machin(self):
        self.assertEqual(foo, bar)
 
if __name__ == '__main__':
    unittest.main()
```

### [pytest](https://docs.pytest.org/en/latest/)
> The pytest framework makes it easy to write small tests, yet scales to support complex functional testing for applications and libraries.

[Alledgedly](http://sametmax.com/un-gros-guide-bien-gras-sur-les-tests-unitaires-en-python-partie-3/) better than _unittest_.
```
def test_machin():
    assert foo == bar
```

### [Coverage](https://coverage.readthedocs.io/en/coverage-5.0.3/)
> Coverage.py is a tool for measuring code coverage of Python programs. It monitors your program, noting which parts of the code have been executed, then analyzes the source to identify code that could have been executed but was not.

## Profiling

### [cProfile](https://docs.python.org/2/library/profile.html)
> cProfile and profile provide deterministic profiling of Python programs. A profile is a set of statistics that describes how often and for how long various parts of the program executed. These statistics can be formatted into reports via the pstats module.

### [With PyCharm](https://www.jetbrains.com/help/pycharm/profiler.html#)
> If you have a yappi profiler installed on your interpreter, PyCharm starts the profiling session with it by default, otherwise it uses the standard cProfile profiler. 


## Fast computing

Beware of premature optimization! [Profile](#profiling) first.

### [pypy](https://www.pypy.org/)
> "If you want your code to run faster,
> you should probably just use PyPy."
> -- Guido van Rossum (creator of Python)

### [cython](https://cython.org/)
>  Cython is an optimising static compiler for both the Python programming language and the extended Cython programming language (based on Pyrex). It makes writing C extensions for Python as easy as Python itself.
> Cython gives you the combined power of Python and C to let you
> - write Python code that calls back and forth from and to C or C++ code natively at any point.
> - easily tune readable Python code into plain C performance by adding static type declarations, also in Python syntax.

### [numba](http://numba.pydata.org/numba-doc/latest/user/5minguide.html)
> Numba translates Python functions to optimized machine code at runtime using the industry-standard LLVM compiler library. Numba-compiled numerical algorithms in Python can approach the speeds of C or FORTRAN.
> You don't need to replace the Python interpreter, run a separate compilation step, or even have a C/C++ compiler installed. Just apply one of the Numba decorators to your Python function, and Numba does the rest.

```python
from numba import jit
import random

@jit(nopython=True)
def monte_carlo_pi(nsamples):
    acc = 0
    for i in range(nsamples):
        x = random.random()
        y = random.random()
        if (x ** 2 + y ** 2) < 1.0:
            acc += 1
    return 4.0 * acc / nsamples
```

## Build and Interpreter

### [Remote interpreter with PyCharm](https://www.jetbrains.com/help/pycharm/configuring-remote-interpreters-via-ssh.html#)
- Handles automatic ssh upload/download
- Runs the remote python kernel locally (console, debugging, etc.)

### [make](https://en.wikipedia.org/wiki/Make_(software))

* [Makefiles in python projects](https://krzysztofzuraw.com/blog/2016/makefiles-in-python-projects.html)
* [Automation and Make](https://swcarpentry.github.io/make-novice/02-makefiles/)


## Continuous integration

### [Travis](https://travis-ci.org/)
>  Test and Deploy with Confidence. Easily sync your projects with Travis CI and you’ll be testing your code in minutes! 

### [Github Actions](https://github.com/features/actions)
> Automate your workflow from idea to production. GitHub Actions makes it easy to automate all your software workflows, now with world-class CI/CD. Build, test, and deploy your code right from GitHub. Make code reviews, branch management, and issue triaging work the way you want.

[Marketplace](https://github.com/marketplace?type=actions)

Useful actions:
* [Starter Python application](https://github.com/actions/starter-workflows/blob/master/ci/python-app.yml): install, lint with flake8, pytest
* [LaTeX](https://github.com/marketplace/actions/github-action-for-latex)
* [Sphinx](https://github.com/marketplace/actions/sphinx-build) documentation


# Cool libraries

## Visualisation

### [tqdm](https://github.com/tqdm/tqdm)
> A Fast, Extensible Progress Bar for Python and CLI

### [celluloid](https://github.com/jwkvam/celluloid/)
> Matplotlib animations made easy

### [binder](https://mybinder.org/)
> Turn a Git repo into a collection of interactive notebooks

## Automatic differentiation

### [autograd](https://github.com/HIPS/autograd)
> Efficiently computes derivatives of numpy code

### [jax](https://github.com/google/jax)
> JAX is Autograd and XLA, brought together for high-performance machine learning research.
> What’s new is that JAX uses XLA to compile and run your NumPy programs on GPUs and TPUs

# Resources
- [Python Tricks: The Book](https://b-ok.cc/book/3525476/83453b), Dan Bader.


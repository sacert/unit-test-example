# unit-test-example
### A Brief Testing Guide

This project includes some examples of how to write unit tests using [pytest](https://docs.pytest.org/en/latest/) 
and check test coverage using [pytest-cov](https://pypi.python.org/pypi/pytest-cov).

#### Benefits of Testing

Testing is widely used in the software industry and is known to have the following benefits: 

1. Find bugs early
2. Facilitate change
3. Simplify integration
4. Improve code quality
5. Refactor confidently
6. Provides documentation
7. Create better code design
8. Reduce costs

(Adapted from this [site](https://dzone.com/articles/top-8-benefits-of-unit-testing))


#### Installation
First, install the dependencies of this project with pip:

```bash
$ pip install -r requirements.txt
```

#### How to Run Tests With Coverage

Checking test coverage allows you to verify whether your tests are really covering every line and branch in your code.  

To run the tests with coverage, type the following at the command line:

```bash
$ pytest --cov=. tests.py
```

This should give you the following output (```*``` represents particular information on your system):

```bash
========================================================= test session starts ==========================================================
platform * -- Python *, pytest-*, py-*, pluggy-*
rootdir: */unit-test-example, inifile:
plugins: cov-*
collected 4 items

tests.py ....  
  
---------- coverage: platform darwin, python * -----------
Name       Stmts   Miss  Cover
------------------------------
maths.py       8      0   100%

======================================================= 4 passed in 0.01 seconds =======================================================

```

If a test passes, you will see a `.` printed on the screen. If a test fails, you will see an `F` printed on the screen.

Each line in the test coverage report has four columns:
1. `Name`: the name of the file that was checked for coverage
2. `Stmts`: the number of statements (lines of code) in the file
3. `Miss`: the number of statements (lines of code) in the file that were not tested
4. `Cover`: the percentage of lines that were covered by unit tests

You can exclude files or folders in your `.coveragerc` file. 
This is why `tests.py` is not included in the coverage report.

#### How to Run Tests Without Coverage

To run the tests without coverage, type the following at the command line:

```bash
$ pytest tests.py
```

This should give you the following output (```*``` represents particular information on your system):

```bash
========================================================= test session starts ==========================================================
platform * -- Python *, pytest-*, py-*, pluggy-*
rootdir: */unit-test-example, inifile:
plugins: cov-*
collected 4 items

tests.py ....                                                                                                                    [100%]

======================================================= 4 passed in 0.01 seconds =======================================================

```

#### Notes

##### Unit vs. Integration vs. Functional Tests?
This [article](https://codeutopia.net/blog/2015/04/11/what-are-unit-testing-integration-testing-and-functional-testing/) 
provides a good overview of the differences between these types of tests.

##### 100% Test Coverage?

Full test coverage is ideal but not always practical. 
Some parts of the code are difficult to test or are not part of the critical functionality of the system.
Less than 100% test coverage is often acceptable. A rule of thumb is to shoot for at least 80% test coverage 
and have functional tests for the critical operation of the entire system. 

##### Humble Objects 

Developers often run into the problem of writing code that is difficult to test. 
This most commonly happens at the external interfaces, such as the database or UI. 
Testing these interfaces can involve mocking objects or external services, which is time consuming.
To combat this problem, you can use the 
[Humble Objects](https://ieftimov.com/tdd-humble-object) pattern. 
This boils down to making the difficult-to-test parts of the code do as little as possible.

##### TDD for Scientific Computing

This is a great overview of test-driven development for scientific computing.

[Clune, Test Driven Development of Scientific Models, NASA Goddard Space Flight Center, 2012](https://sea.ucar.edu/sites/default/files/TDD_For_Scientists.pdf)

##### Testing Approximate Results
 
Functions that use floating-point numbers often do not produce the results you expect to full precision. 
Floating-point results that originate from different processes may be off in the last few decimal places, 
causing tests for strict equality to fail. Numpy offers a great 
[test support suite](https://docs.scipy.org/doc/numpy-1.13.0/reference/routines.testing.html) to handle these cases.

##### Testing API

As systems evolve, production code gets refactored. If you have written tests for all of your production code, then there is often
resistance to refactoring code, as this will also require modifying your tests. To assist with this problem, it's often a good idea to
decouple your tests from your production code with a Testing API. The general idea is explained in [this article]
(http://blog.cleancoder.com/uncle-bob/2017/03/03/TDD-Harms-Architecture.html) by "Uncle Bob" Martin and is hashed out in this [StackExchange question]
(https://softwareengineering.stackexchange.com/questions/353149/tdd-decouple-test-code-from-production-code-avoiding-one-to-tone-correspondenc?newreg=17869c0fd96d4be2b230fbff277c387a).

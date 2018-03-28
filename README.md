# unit-test-example
###Examples of Python unit tests

This project includes some examples of how to write unit tests using [pytest](https://docs.pytest.org/en/latest/) and check test coverage using [pytest-cov](https://pypi.python.org/pypi/pytest-cov).



First, install the dependencies of this project with pip:

```bash
$ pip install -r requirements.txt
```

####How to Run Tests Without Coverage

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

If a test passes, you will see a `.` printed on the screen. If a test fails, you will see an `F` printed on the screen.

####How to Run Tests With Coverage

To run the tests without coverage, type the following at the command line:

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

Each line in the test coverage report has four columns:
1. Name: the name of the file that was checked for coverage
2. Stmts: the number of statements (lines of code) in the file
3. Miss: the number of statements (lines of code) in the file that were not tested
4. Cover: the percentage of lines that were covered by unit tests



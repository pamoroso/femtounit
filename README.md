# Femtounit

Femtounit is a unit test framework for [Medley Interlisp](https://interlisp.org) based on the PCL unit test framework by [Peter Seibel](https://gigamonkeys.com) described in [Chapter 9](https://gigamonkeys.com/book/practical-building-a-unit-test-framework.html) of his book [Practical Common Lisp](https://gigamonkeys.com/book).

![Defining and executing unit tests with Femtounit.](https://raw.githubusercontent.com/pamoroso/femtounit/main/femtounit.png)


## Installation

Download the file `FEMTOUNIT` from the project repo, copy it to a file system location your Medley Interlisp installation has access to, and optionally compile the source by evaluating the following expression from the Lisp executive:

```
(TCOMPL 'FEMTOUNIT)
```

Provide these answers to the questions the compiler asks:

* listing? no
* redefine? yes
* save exprs? no

Finally, to load the framework evaluate:

```lisp
(FILESLOAD FEMTOUNIT)
```


## Usage

Suppose you want to test this function that returns the square of its argument:

```lisp
(DEFINEQ (SQUARE (X) (TIMES X X)))
```

Assuming Femtounit is loaded, you may define a test function like this by evaluating:

```lisp
(DEFTEST TEST.SQUARE ()
  (CHECK.EXPECT (EQP (SQUARE 1) 1)
                (EQP (SQUARE 2) 4)
                (EQP (SQUARE 3) 9)
                (EQP (SQUARE 4) 16)))
```

To run the tests call the test function by evaluating:

```lisp
(TEST.SQUARE)
```

which will print a dot character for every passed test:

```
....
```


### Reference

You can use the following Lisp forms to create and run unit tests and test suites.

`(DEFTEST NAME PARAMETERS BODY)` (macro): Define a test function called `NAME` with a list of `PARAMETERS` and a sequence of forms as the `BODY`. The test function has a syntax similar to `defun` in Common Lisp.

A test function can call other test functions or use `CHECK.EXPECT` to run individual test cases. 

`(CHECK.EXPECT FORMS)` (macro): Run each expression in the sequence of `FORMS` as a test case.

`(COMBINE.RESULTS FORMS)` (macro): Combine the results as booleans of evaluating the sequence of `FORMS` in order. Similar to `AND` but all the forms are evaluated.


## Release history

See the [list of releases](https://github.com/pamoroso/femtounit/releases) for notes on the changes in each version.


## Learn more

- [Femtounit project updates](https://journal.paoloamoroso.com/tag:femtounit)
- [Medley Interlisp](https://interlisp.org)


## Author

Femtounit is developed by [Paolo Amoroso](https://github.com/pamoroso).


## License

This code is distributed under the MIT license, see the `LICENSE` file.

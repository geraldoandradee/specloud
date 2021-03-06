SpecLoud
========

Use nosetests and plugins to take BDD specifications easier.


Installation
------------

The easiest way to install specloud is using pip and requirements file::

    $ pip install specloud


Usage
=====

Get a python file with BDD-style test names (starting with it, ensure, should, must, spec, example, deve) and add them to the test suite


For example::

    $ cat example.py

    import unittest


    class CalculatorSpec(unittest.TestCase):

        def it_should_sum_integers(self):
            # ...
            pass

        def should_not_divide_by_zero(self):
            # ...
            pass

        def must_accept_floats(self):
            # ...
            pass

        def ensure_it_work_with_fractions(self):
            # ...
            pass

        def test_subtract_positive_from_negative_numbers(self):
            # ...
            pass

        def deve_calcular_raizes_quadradas(self):
            # ...
            pass


The command line tool `specloud` colorizes **green** for tests with no failures and no errors and **red** for tests with failures and/or errors::

    $ specloud example.py

    Calculator spec
    - ensure it work with fractions
    - it should sum integers
    - must accept floats
    - should not divide by zero
    - subtract positive from negative numbers
    - deve calcular raizes quadradas

    ----------------------------------------------------------------------
    Ran 5 tests in 0.003s

    OK


How It Works
------------

SpecLoud is a python package that install `nose`, `pinocchio` and `figleaf` packages, so it can call `nosetests` with `pinocchio` and `figleaf` plugins. `nosetests` is called with some default options to find test methods and `pinocchio` to show pretty and colored messages. `figleaf` is just `pinocchio` dependency.

A call to::

    $ specloud FILE


is the same doing::

    $ nosetests -i '^(it|ensure|must|should|specs?|examples?|deve)' -i '(specs?(.py)?|examples?(.py)?)$' '--with-spec' '--spec-color'

Old Name
--------

The project was born as a proof of concept and I named it firstly `pyunitbdd`. But that's a terrible name. So I renamed the project to `specloud`.


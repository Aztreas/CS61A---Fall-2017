This file holds the tests that you create. Remember to import the python file(s)
you wish to test, along with any other modules you may need.
Run your tests with "python3 ok -t --suite SUITE_NAME --case CASE_NAME -v"
--------------------------------------------------------------------------------

Suite 1

    >>> from scheme_reader import *

    Case Example
        >>> scheme_read(Buffer(tokenize_lines(['nil'])))
        nil

Suite 2
    >>> from scheme_reader import *

    Test 1 basic
        >>> read_line('(1 2 3 . 4)')
        Pair(1, Pair(2, Pair(3, 4)))

    Test 2 nested lists
        >>> read_line('((1 . 2) 3 . 4)')
        Pair(Pair(1, 2), Pair(3, 4))

Suite 3
    >>> from scheme import *
    >>> global_frame = create_global_frame()

   Test 1 back to back
        >>> global_frame.define('fake_variables', 7)
        >>> global_frame.lookup('fake_variables')
        7

    Test 2 built ins
        >>> type(global_frame.lookup('+'))
        <class 'scheme.PrimitiveProcedure'>

Suite 4
    >>> from scheme import *

    Test 1 use_env
        >>> env = create_global_frame()
        >>> two = Pair(7, nil)
        >>> eval = PrimitiveProcedure(scheme_eval, True)
        >>> scheme_apply(eval, two, env)
        7

    Test 1 checks eval for list
        >>> env = create_global_frame()
        >>> two = Pair(7, Pair (8, nil))
        >>> eval = PrimitiveProcedure(scheme_eval, True)
        >>> scheme_apply(eval, two, env)
        7
        >>> scheme_apply(eval, two, env)
        7

Suite 5
    >>> from scheme import *

    Test 1 basics
        >>> expr = read_line('(+ 2 9)')
        >>> scheme_eval(expr, create_global_frame())
        11

        >>> expr = read_line('(even? (+ 2 9))')
        >>> scheme_eval(expr, create_global_frame())
        False

    Test 2 parameters
        >>> expr = read_line('(+ 2 0 1 7)')
        >>> scheme_eval(expr, create_global_frame())
        10

        >>> expr = read_line('(+)')
        >>> scheme_eval(expr, create_global_frame())
        0

        >>> expr = read_line('(* 2 0 1 7)')
        >>> scheme_eval(expr, create_global_frame())
        0

        >>> expr = read_line('(*)')
        >>> scheme_eval(expr, create_global_frame())
        1

    Test 1 nests
        >>> expr = read_line('(- (* 99 72) (+ 2 9))')
        >>> scheme_eval(expr, create_global_frame())
        7117

Suite 6
    >>> from scheme import *

    Test 1 basic defining
        >>> env = create_global_frame()
        >>> do_define_form(Pair('name', Pair(10, nil)), env)
        'name'
        >>> env.lookup('name')
        10






Suite 7
    >>> from scheme import *

    Test 1 basic quoting
        >>> env = create_global_frame()
        >>> do_quote_form(Pair( Pair(1, Pair(2, nil)), nil), env)
        Pair(1, Pair(2, nil))

Suite 8
    >>> from scheme import *
    >>> env = create_global_frame()

    Test 1 basic begins
        >>> eval_all(Pair(6, Pair(7, Pair(8, nil))), env)
        8

Suite 9
    >>> from scheme import *
    >>> env = create_global_frame()

    Test 1 creating lambdas
        >>> function = Pair(Pair('x', Pair('y', nil)), Pair(Pair(scheme_add, Pair('x', Pair('y', nil))), nil))
        >>> a = do_lambda_form(function, env)
        >>> type(a)
        <class 'scheme.LambdaProcedure'>

Suite 10
    >>> from scheme import *
    >>> env = create_global_frame()

    Test 1 basic assignment
    >>> 'code': r"""
         scm> (define (f) (+ 2 2))
         f

Suite 11
    >>> from scheme import *
Suite 12
    >>> from scheme import *
Suite 13
    >>> from scheme import *
Suite 14
    >>> from scheme import *
Suite 15
    >>> from scheme import *
Suite 16
    >>> from scheme import *
Suite 17
    >>> from scheme import *
Suite 18
    >>> from scheme import *
Suite 19
    >>> from scheme import *

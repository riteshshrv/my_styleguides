# Python Style Guide <sup>β</sup>

This is my Python Style Guide.

## Table of Contents
  1. [Whitespace](#whitespace)
    1. [Indentation](#indentation)
    1. [Inline](#inline)
    1. [Newlines](#newlines)
  1. [Line Length](#line-length)
  1. [Commenting](#commenting)
    1. [File/class-level comments](#fileclass-level-comments)
    1. [Function comments](#function-comments)
    1. [Block and inline comments](#block-and-inline-comments)
    1. [Punctuation, spelling, and grammar](#punctuation-spelling-and-grammar)
    1. [TODO comments](#todo-comments)
    1. [FIXME comments](#fixme-comments)
    1. [Commented-out code](#commented-out-code)
  1. [Methods](#methods)
    1. [Method definitions](#method-definitions)
    1. [Method calls](#method-calls)
  1. [Conditional Expressions](#conditional-expressions)
    1. [Conditional keywords](#conditional-keywords)
    1. [Ternary operator](#ternary-operator)
    1. [Nested Conditionals](#nested-conditionals)
  1. [Syntax](#syntax)
  1. [Naming](#naming)
  1. [Exceptions](#exceptions)
  1. [Collections](#collections)
  1. [Strings](#strings)
  1. [Be Consistent](#be-consistent)


## Whitespace

### Indentation

* <a name="default-indentation"></a>Use soft-tabs with a four
    space-indent.<sup>[[link](#default-indentation)]</sup>

* <a name="align-function-params"></a>Align function parameters either all on
    the same line or one visual indent block per line.<sup>[[link](#align-function-params)]</sup>

    ```Python
    # okay
    def create_translation(phrase_id, phrase_key, target_locale,
                value, user_id, do_xss_check, allow_verification):
        ...
        ...

    # good
    def create_translation(
        phrase_id, phrase_key, target_locale, value,
        user_id, do_xss_check, allow_verification
    ):
        ...
        ...

    ```

### Inline

* <a name="trailing-whitespace"></a>Never leave trailing whitespace.
    <sup>[[link](#trailing-whitespace)]</sup>

* <a name="space-before-comments"></a>When making inline comments, include two
    space between the end of the code and the start of your comment and one space
    after pound sign. <sup>[[link](#space-before-comments)]</sup>

    ```Python
    # bad
    result = func(a, b)# we might want to change b to c

    # good
    result = func(a, b)  # we might want to change b to c
    ```

* <a name="spaces-operators"></a>Use spaces around operators; after commas, and
    colons.
    <sup>[[link](#spaces-operators)]</sup>

    ```Python
    nsum = 1 + 2
    a, b = 1, 2
    True if 1 > 2 else 'hi'
    ```

* <a name="no-space-before-commas"></a>Never include a space before a comma.
    <sup>[[link](#no-space-before-commas)]</sup>

    ```Python
    # unacceptable
    result = func(a , b)

    # good
    result = func(a, b)
    ```

* <a name="no-spaces-braces"></a>No spaces after `(`, `[` or before `]`, `)`.
    <sup>[[link](#no-spaces-braces)]</sup>

    ```Python
    some(arg).other
    [1, 2, 3].index(2)
    ```

* <a name="no-spaces-string-interpolation"></a>Omit whitespace when doing
    string interpolation.<sup>[[link](#no-spaces-string-interpolation)]</sup>

    ```Python
    # bad
    var = "This { foobar } is interpolated.".format(foobar='foo')

    # good
    var = "This {foobar} is interpolated.".format(foobar='foo')
    ```

### Newlines

* <a name="multiline-if-newline"></a>Enclose all `if` conditions within braces
    and break after every operator if there are too many or long conditions to
    help differentiate between the conditions and the body.
    <sup>[[link](#multiline-if-newline)]</sup>

    ```Python
    if (
        reservation_alteration.checkin == reservation.start_date and
        reservation_alteration.checkout == 24
    ):
        # do cool stuff
        redirect_to_alteration(reservation_alteration)
    ```

* <a name="newline-after-conditional"></a>Add a new line after conditionals,
    blocks, case statements, etc.<sup>[[link](#newline-after-conditional)]</sup>

    ```Python
    robot = CreateRobot("I'm a robot")
    if robot.is_awesome():
        send_robot_present()

    robot.add_trait(human_like_intelligence)
    ```

* <a name="newline-different-indent"></a>Don’t include newlines between areas
    of different indentation (such as around class or module bodies).
    <sup>[[link](#newline-different-indent)]</sup>

    ```Python
    # bad
    class Foo:

        def bar(self):
            # body omitted

    # good
    class Foo:
        def bar(self):
            # body omitted
    ```

* <a name="newline-between-methods"></a>Include one newline between methods in
    a class and two newlines otherwise.
    <sup>[[link](#newline-between-methods)]</sup>

    ```Python
    class Foo(object):
        def a(self):
            ...
            ...

        def b(self):
            ...
            ...
    ```

    ```Python
    def a(self):
        ...
        ...


    def b(self):
        ...
        ...
    ```

* <a name="method-def-empty-lines"></a>Use a single empty line to break between
    statements to break up methods into logical paragraphs internally.
    <sup>[[link](#method-def-empty-lines)]</sup>

    ```Python
    def transformorize_car():
        car = manufacture(options)
        t = transformer(robot, disguise)

        car.after_market_mod!()
        t.transform(car)
        car.assign_cool_name()

        fleet.add(car)
    ```

* <a name="trailing-newline"></a>End each file with a newline. Don't include
    multiple newlines at the end of a file.
    <sup>[[link](#trailing-newline)]</sup>

## Line Length

* Keep each line of code to a readable length. Unless
  you have a reason to, keep lines to fewer than 80 characters.
  <sup>[[link](#line-length)]</sup>

## Commenting

> Though a pain to write, comments are absolutely vital to keeping our code
> readable. The following rules describe where, how and what you should comment.
> But remember: while comments are very important, the best code is
> self-documenting. Giving sensible names to types and variables is much better
> than using obscure names that you must then explain through comments.

> When writing your comments, write for your audience: the next contributor who
> will need to understand your code. Be generous — the next one may be you!

**Use double quotes for docstrings everywhere**

### File/class-level comments

* Every class definition should have an accompanying docstring that describes what
  it is for and how it should be used.

* A file should have a shebang line, encoding information and a short docstring
  explaining about the content of file along with license information and may be
  name of author as well.

```Python
#!/usr/bin/env python
# -*- coding: utf-8 -*-
"""
A collection of helper classes to translate text

Copyright (c) 2017, Ritesh and contributors
For license information, please see license.txt
"""
# import block omitted

class AmericanToColonial:
    """
    Applies transforms to American English that are common to
    variants of all other English colonies.
    """
    ...
    ...


class AmericanToBritish(AmericanToColonial):
    """
    Converts American to British English.
    In addition to general Colonial English variations, changes "apartment"
    to "flat".
    """
    ...
    ...
```

* All files should define `__all__` variable which is a list of functions/methods,
  classes and other variables that you expect others to import. This is needed
  because without the `__all__` variable everything gets imported for a `*` statement
  which may cause spectacular problems. Though, avoid using `*` imports.

```Python
#!/usr/bin/env python
# -*- coding: utf-8 -*-
"""
A collection of helper classes to translate text

Copyright (c) 2017, Ritesh and contributors
For license information, please see license.txt
"""
from collections import defaultdict

__all__ = ['AmericanToColonial', 'AmericanToBritish']


class AmericanToColonial:
    """
    Applies transforms to American English that are common to
    variants of all other English colonies.
    """
    ...
    ...


class AmericanToBritish(AmericanToColonial):
    """
    Converts American to British English.
    In addition to general Colonial English variations, changes "apartment"
    to "flat".
    """
    ...
    ...
```

### Function comments

Every function declaration should have comments immediately after the definition
such that it describeis what the function does and how to use it. These comments
should be descriptive ("Opens the file") rather than imperative ("Open the file");
the comment describes the function, it does not tell the function what to do. In
general, these comments do not describe how the function performs its task.
Instead, that should be left to comments interspersed in the function's code.

Every function should mention what the inputs and outputs are, unless it meets
all of the following criteria:

* not externally visible
* very short
* obvious

```Python
def fallbacks_for(the_locale, opts={})
    """
    Returns the fallback locales for the_locale.
    If opts['exclude_default'] is set, the default locale, which is otherwise
    always the last one in the returned list, will be excluded.

    For example:
      fallbacks_for("pt-BR")
        => ["pt-BR", pt, en]
      fallbacks_for("pt-BR", opts={'exclude_default': True})
        => ["pt-BR", pt]

    :param the_locale: Locale Object
    :param opts: Dictionary (Optional)
    :returns: Boolean
    """
    ...
    ...
```

### Block and inline comments

The final place to have comments is in tricky parts of the code. If you're
going to have to explain it at the next code review, you should comment it now.
Complicated operations get comments prefixed with `# XXX: ` before the
operations commence.

```Python
def fallbacks_for(the_locale, opts={})
    """
    Define fallbacks for locales
    """
    # dup() to produce an array that we can mutate.
    ret = fallbacks[the_locale]

    # XXX: We make two assumptions here:
    # 1) There is only one default locale (that is, it has no less-specific
    #    children).
    # 2) The default locale is just a language. (Like 'en', and not "en-US".)
    if opts['exclude_default']:
        ret['last'] == default_locale
        ret['last'] != language_from_locale(the_locale)
        ret.pop()

    ...
    ...
```

On the other hand, never describe the code. Assume the person reading the code
knows the language (though not what you're trying to do) better than you do.

<a name="no-block-docstring-comments"></a>Related: do not use docstring-type block comments.
  They cannot be preceded by whitespace and are not as easy to spot as regular comments.
  <sup>[[link](#no-block-docstring-comments)]</sup>

  ```Python
  # unacceptable
  '''
  comment line
  another comment line
  '''

  # unacceptable
  """
  comment line
  another comment line
  """

  # good
  # comment line
  # another comment line
  ```

### Punctuation, spelling and grammar

Pay attention to punctuation, spelling, and grammar; it is easier to read
well-written comments than badly written ones.

Comments should be as readable as narrative text, with proper capitalization
and punctuation. In many cases, complete sentences are more readable than
sentence fragments. Shorter comments, such as comments at the end of a line of
code, can sometimes be less formal, but you should be consistent with your
style.

Although it can be frustrating to have a code reviewer point out that you are
using a comma when you should be using a semicolon, it is very important that
source code maintain a high level of clarity and readability. Proper
punctuation, spelling, and grammar help with that goal.

### TODO comments

* Use TODO comments for code that is temporary, a short-term solution, or
  good-enough but not perfect.

* TODOs should include the string TODO in all caps, followed by a colon.
  A comment explaining what there is to do is required.

```Python
  # bad
  # TODO Use proper namespacing for this constant.

  # good
  # TODO: Use proper namespacing for this constant.
```

### FIXME comments

* Use FIXME comments for code that needs to be replaced/fixed as soon as a better
  solution is availabe. This should be used sparingly as there will always be room
  to improve a piece of code.

* FIXMEs should include the string FIXME in all caps, followed by a colon.
  A comment explaining what there is to fix is required.

```Python
  # bad
  # FIXME Use itertools.ifilter instead of filter for python v2 code.

  # good
  # FIXME: Use itertools.ifilter instead of filter for python v2 code.
```

### Commented-out code

* <a name="commented-code"></a>Never leave commented-out code in codebase.
  Commenting code is a bad practice; the only reason someone can come up
  with to have code commented is to have the ability to quickly refer what
  or how the code looked like previously. Well, thats the whole point of
  using a version control system like Git.
    <sup>[[link](#commented-code)]</sup>


## Methods

### Method definitions

* <a name="no-single-line-methods"></a>Avoid single-line methods and conditionals.
    Although they are somewhat popular in the wild, there are a few peculiarities
    about their definition syntax that make their use undesirable.
    <sup>[[link](#no-single-line-methods)]</sup>

    ```Python
    # bad
    def too_much(): return something

    # bad
    if i > 1: print('hi')

    # good
    if i > 1:
        print('hi')

    # good
    def some_method()
      # body

    ```

### Method calls

* <a name="space-method-call"></a>Never put a space between a method name and
    the opening parenthesis.<sup>[[link](#space-method-call)]</sup>

    ```Python
    # bad
    def foo (a, b):
        # body

    # bad
    print ('Hi')

    # good
    def foo(a, b):
        # body

    # good
    print('Hi')
    ```


## Conditional Expressions

### Conditional keywords

* <a name="no-unless-with-else"></a>Never lead a conditional with negation.
They sabotage the usual flow evaluating a boolean to True to execute the
enclosing block. Rewrite these with the positive case first.
<sup>[[link](#no-unless-with-else)]</sup>

    ```Python
    # extremely bad
    if not 1 > 2:
        print('1 is not greater than 2')
    else:
        print('1 is greater than 2')

    # good
    if 1 > 2:
        print('1 is greater than 2')
    else:
        print('1 is not greater than 2')
    ```

* <a name="unless-with-multiple-conditions"></a>Avoid `not` with multiple
    conditions. But, if you have to have this then enclose the conditions
    in braces.<sup>[[link](#unless-with-multiple-conditions)]</sup>

    ```Python
    # bad
    if not 1 and 2:
        ...

    # okay
    if not(1 and 2):
        ...
    ```

* <a name="parens-around-conditions"></a>Don't use parentheses around the
    condition of a single line `if`.
    <sup>[[link](#parens-around-conditions)]</sup>

    ```Python
    # bad
    if (x > 10):
        ...

    # good
    if x > 10:
        ...

    ```

### Ternary operator

* <a name="avoid-complex-ternary"></a>Avoid the ternary operator except
    in cases where all expressions are extremely trivial. However, do use the
    ternary operator over `if/then/else/end` constructs for single line
    conditionals.<sup>[[link](#avoid-complex-ternary)]</sup>

    ```Python
    # okay
    result = something if some_condition else something_else
    ```

* <a name="no-nested-ternaries"></a>Avoid nested ternaries.
    <sup>[[link](#no-nested-ternaries)]</sup>

* <a name="single-condition-ternary"></a>Avoid multiple conditions in ternaries.
    Ternaries are best used with single conditions.
    <sup>[[link](#single-condition-ternary)]</sup>

* <a name="no-multiline-ternaries"></a>Avoid multi-line ternary
    operator, use `if/then/else` construct instead.
    <sup>[[link](#no-multiline-ternaries)]</sup>


### Nested conditionals

* <a name="no-nested-conditionals"></a>
  Avoid the use of nested conditionals for flow of control.
  ([More on this][avoid-else-return-early].) <sup>[[link](#no-nested-conditionals)]</sup>

  Prefer a guard clause when you can assert invalid data. A guard clause
  is a conditional statement at the top of a function that returns as soon
  as it can.

  The general principles boil down to:
  * Return immediately once you know your function cannot do anything more.
  * Reduce nesting and indentation in the code by returning early. This makes
  the code easier to read and requires less mental bookkeeping on the part
  of the reader to keep track of `else` branches.
  * The core or most important flows should be the least indented.

  ```Python
    # bad
    def compute()
        server = find_server()
        if server:
            client = server.client
            if client:
                request = client.make_request
                if request
                    process_request(request)
                else:
                    return
            else:
                return
        else:
            return

    # good
    def compute()
        server = find_server()
        if not server:
            return

        client = server.client()
        if not client:
            return

        request = client.make_request()
        if not request:
            return

        process_request(request)
  ```

## Syntax

* <a name="self-assignment"></a>Use shorthand self assignment operators
    whenever applicable.<sup>[[link](#self-assignment)]</sup>

    ```Python
    # bad
    x = x + y
    x = x * y
    x = x**y
    x = x / y

    # good
    x += y
    x *= y
    x **= y
    x /= y
    ```

* <a name="const-use"></a>Name the variable in all caps if the value is constant.
    <sup>[[link](#const-use)]</sup>

* <a name="redundant-return"></a>Avoid `return` where not required.
    <sup>[[link](#redundant-return)]</sup>

    ```Python
    # bad
    def some_method(some_arr)
        ...
        ...
        return

    # good
    def some_method(some_arr)
        ...
        ...
    ```

* <a name="group-imports"></a>Group import statements into logical blocks. All `import`
    statements should be grouped together, `from` imports in a different group. Further
    sort them with internal libraries first and then external or internal third-party
    libraries. <sup>[[link](#group-imports)]</sup>

    ```Python
    import os
    import sys
    import my_awesome_library

    from itertools import chain, tee
    from dateutil.relativedelta import relativedelta
    ```
* <a name="club-imports"></a>Do not club multiple imports in a single line.
    <sup>[[link](#club-imports)]</sup>

    ```Python
    # bad
    import os, sys

    # good
    import os
    import sys
    ```

* <a name="cls"></a>Use `cls` over `self` when defining a reference to current object
    in case of class methods.<sup>[[link](#redundant-self)]</sup>

    ```Python
    # unacceptable
    @classmethod
    def do_something(self):
        return something

    # good
    @classmethod
    def do_something(cls):
        return something

    ```

## Naming

* <a name="snake-case"></a>Use `snake_case` for methods and variables.
    <sup>[[link](#snake-case)]</sup>

* <a name="camel-case"></a>Use `CamelCase` for classes and modules. (Keep
    acronyms like HTTP, RFC, XML uppercase.)
    <sup>[[link](#camel-case)]</sup>

* <a name="screaming-snake-case"></a>Use `SCREAMING_SNAKE_CASE` for other
    constants.<sup>[[link](#screaming-snake-case)]</sup>

* <a name="throwaway-variables"></a>Name throwaway variables `_`. They are the
    values that are not required for current use case.
    <sup>[[link](#throwaway-variables)]</sup>

    ```Python
    version = '3.2.1'
    major_version, minor_version, _ = version.split('.')
    ```

## Exceptions

* <a name="dont-rescue-exception"></a>Avoid excepting the `Exception` class.
    <sup>[[link](#dont-rescue-exception)]</sup>

    ```Python
    # bad
    try:
        # an exception occurs here
    except Exception:
        # exception handling

    # good
    try:
        # an exception occurs here
    except ValueError:
        # exception handling

    # unacceptable
    try:
        # an exception occurs here
    except:
        # exception handling
    ```

* <a name="redundant-exception"></a>Don't use bases error class to raise your own
    exceptions. Prefer error sub-classes for clarity and
    explicit error creation.<sup>[[link](#redundant-exception)]</sup>

    ```Python
    # bad
    raise ValueError('message')

    # bad
    raise TypeError('message')

    # best
    class MyExplicitError(Exception):
        pass

    raise MyExplicitError('message')
    ```


## Collections

**Use internal library functions instead of reinventing the wheels**

* <a name="internal-libraries"></a>Check functions offered by `collections` &
    `itertools` library.

* <a name="internal-library-functions"></a>Check documentation of `map`, `filter`,
    `lambda`, `groupby`, `defaultdict`, `chain`.

* <a name="else-block"></a>Understand the `else` block of `try..except`
    and `for`.<sup>[[link](#else-block)]</sup>

* <a name="array-trailing-comma"></a>Use a trailing comma in a `List` and `Dictionary`
    that spans more than 1 line. One of the reasons to have trailing comma is that
    it does not create a diff on the last line in cases more items are added to the
    container and so, its easier to comprehend for the reviewer. Prefer visual
    indent blocks over logical indents<sup>[[link](#array-trailing-comma)]</sup>

    ```Python
    # good
    array = [1, 2, 3]

    # okay
    array = [
        "car",
        "bear",
        "plane",
        "zoo",
    ]

    # good (this is preferring visual indent block)
    array = [
        "car", "bear",
        "plane", "zoo",
    ]

    # good
    map = {
        'foo': 'bar',
        'bar': 'foo',
    }
    ```

## Strings

* <a name="string-interpolation"></a>Prefer string interpolation instead of
    string concatenation:<sup>[[link](#string-interpolation)]</sup>

    ```Python
    # bad
    email_with_name = user.name + ' <' + user.email + '>'

    # good
    email_with_name = "{name} <{email}>".format(name=user.name, email=user.email)
    ```

* <a name="multi-line-strings"></a>Break the long string into smaller chunks and enclose
    them in a tupple or use tripple quotes (single quote). Keep in mind that using triple
    quote will preserve all the whitespace inside quotes.<sup>[[link](#multi-line-strings)]</sup>

    ```Python
    # bad
    large_text = "Some string is really long and " + \
        "spans multiple lines."

    # okay
    large_text = """
        Some string is really long and
        spans multiple lines.
    """

    # good
    large_text = (
        "Some string is really long and "
        "spans multiple lines."
    )
    ```

## Be Consistent

* If you're editing code, take a few minutes to look at the code around you and
  determine its style. If they use spaces around all their arithmetic
  operators, you should too. If their comments have little boxes of hash marks
  around them, make your comments have little boxes of hash marks around them
  too.

* The point of having style guidelines is to have a common vocabulary of coding
  so people can concentrate on what you're saying rather than on how you're
  saying it. If code you add to a file looks drastically different from the
  existing code around it, it throws readers out of their rhythm when they go
  to read it. Avoid this.


* Most of this styleguide is inspired from these:
  * http://pycodestyle.pycqa.org/en/latest/
  * http://flake8.pycqa.org/en/latest/

* Use `flake8 .` to quickly check for compliance.

> Happy Coding!

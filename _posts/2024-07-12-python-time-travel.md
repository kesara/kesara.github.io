---
layout:       post
title:        Time travel with Python
description:  How to test datetime logic with Python
date:         2024-07-12 00:00:00
categories:   python time testing unittest development
---

Testing time is crucial in software development, especially for applications
that rely on time-based functionality. Time-based tests ensure that features
like scheduling, expiration, and logging work correctly across different time
zones and daylight-saving changes.

To test that your time-based logic works correctly, you need to do time travel.
This blog post lists a few ways to test time-based logic with Python in other
words, **How to time travel with Python**. After all, Python comes with
**antigravity**. Just `import antigravity`. :)
So time travel should be a breeze.

For testing, let's say we have a file called `new_year.py` with the following
code. It is a simple function that returns whether the current day is the
new year or not.

##### Source code for `new_year.py`:
```
from datetime import datetime


def is_new_year():
    """
    Returns True when it's new year
    """
    now = datetime.now()
    return now.month == 1 and now.day == 1
```

Our objective is to write tests to validate `is_new_year()` function.


## Mocking datetime

This is one of the straightforward ways to change the time for your tests.
All you need to do is `patch` `datetime.datetime` to do set desired datetime.
Let's say our tests are in `test_new_year.py`.

##### Source code for `test_new_year.py`:
```
from datetime import datetime
from unittest import TestCase
from unittest.mock import patch

from new_year import is_new_year


class TestNewYear(TestCase):
    @patch("new_year.datetime")
    def test_is_new_year_true(self, mock_datetime):
        # test if is_new_year() returns True for first of January
        mock_datetime.now.return_value = datetime(2024, 1, 1)
        self.assertTrue(is_new_year())

    @patch("new_year.datetime")
    def test_is_new_year_false(self, mock_datetime):
        # test if is_new_year() returns False for second of January
        mock_datetime.now.return_value = datetime(2025, 1, 2)
        self.assertFalse(is_new_year())
```

You can run tests with the following command:

```
python3 -m unittest test_new_year
```

In both of the test cases [`unittest.mock`][unittest_mock] is used to change
the `datetime` of the `new_year` module. But this can be cumbersome and
limiting when you use this in complex applications because this doesn't change
the time across the whole application.

## Freezegun

[Freezegun][freezegun] is a third-party Python library that allows test code
with time travelling. So, make sure that you install `freezegun` with
```
pip install freezegun
```

##### Source code for `test_new_year.py` with `freezegun`:
```
from freezegun import freeze_time
from unittest import TestCase

from new_year import is_new_year


class TestNewYear(TestCase):
    @freeze_time("2024-01-01")
    def test_is_new_year_true(self):
        # test if is_new_year() returns True for first of January
        self.assertTrue(is_new_year())

    @freeze_time("2024-01-02")
    def test_is_new_year_false(self):
        # test if is_new_year() returns False for second of January
        self.assertFalse(is_new_year())

```

You can run tests with the following command similar to the above example:
```
python3 -m unittest test_new_year
```

## Conclusion

Testing time-based functionality in Python can be done in a few different ways.
Using [`unittest.mock`][unittest_mock] to patch `datetime` is a basic method
but can be limiting for more complex applications. On the other hand,
[Freezegun][freezegun] provides a more robust solution for time travel in your
tests.

Happy testing, and may your code be ever on time! :)

[unittest_mock]:  https://docs.python.org/3/library/unittest.mock.html
[freezegun]:      https://github.com/spulec/freezegun

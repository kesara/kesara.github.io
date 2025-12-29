---
layout:       post
title:        Python Necromancy
description:  Check list for reviewing an old Python project
date:         2025-12-29 23:23:23
categories:   python python2 python3 pypi pyproject
---

This year I had deal with reviewing two old projects.
Both projects had Python 2 support and Python 3 compatibility with [six][six].
Both had been using `setup.py` for installation and can not be installed on any
of the modern & currently supported Python versions.
But I was fortunate that both projects had tests.
Here's my action plan for Python necromancy.

1. If projects are on PyPI and test PyPI, make sure that you have maintainer/
owner access to the old project. If you don't you will have to create separate
projects on PyPI and test PyPI.

2. Convert old setup systems to `pyproject.toml`.

3. With the above step you will have to update the dependencies as well.

4. Drop support for any unsupported Python versions. This will make your life
easier with dealing with dependencies and not having to support Python 2 or
older versions.

5. When possible drop any dependencies. Less dependencies to worry about is
always a plus.

6. When possible drop any features that doesn't require. Try to get the MVP
(Minimal Viable Product), you can always look to add any missing features later
on.

7. When the package is installable, do some manual tests to see the intended
features are working as intended.

8. Delete any special Python 2 checks and Python 2 specific logic. Lot of
projects that have transitioned Python 3 will have checks for the Python
version.

9. If you are lucky to have tests, use [tox][tox] to run tests for all
supported Python versions.

10. Work on fixing tests, you might have to make judgement calls about keeping
some tests or making complex tests simpler.

11. Add tests as a CI/CD test.

12. Add [PyPI Trusted Publisher][pypi-trusted] to your projects.

Optional steps:

13. Remove [six][six] logic.

14. Use [black][black] or [ruff][ruff] to format code.


[six]: https://six.readthedocs.io/
[tox]: https://tox.wiki/en/4.32.0/
[pypi-trusted]: https://docs.pypi.org/trusted-publishers/using-a-publisher/
[black]: https://black.readthedocs.io/en/stable/
[ruff]: https://docs.astral.sh/ruff/

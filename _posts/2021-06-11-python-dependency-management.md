---
layout:       post
title:        Python Dependency Management
description:  Python dependency management best practices.
date:         2021-06-11 20:09:23
categories:   python programming development security
---

Dependency management in any language is hard, best way to avoid a dependency
hell is to avoid any dependencies. :) But that's never practical.

These are few suggestions to make dependency management easier. This blog
post is mainly focused on dependency management in a web applications.
Hope this will be useful.

> ## TL;DR
> Use venv and split out requirements similar to:
>
> Requirements file | Use
> ----------------- | ---
> `requirements.txt` | Direct dependencies of the application.
> `requirements.txt.lock` | Version locked list of direct dependncies and their dependencies
> `requirements.test.txt` | Dependencies for testing
> `requirements.sec.txt` | Dependencies for security audits and tests
> `requirements.dev.txt` | Development tools and libraries for the project

## Always use venv
[Python virtual environment (venv)](https://docs.python.org/3/library/venv.html)
module comes with your standard Python installation.
venv helps you to keep your development environment clean without leaking
Python libraries to other projects or environments. This also allows you to keep
different versions of Python and dependencies for testing.

To create a new Python virtual environment use following command, this will
create a Python venv in `venv` directory.

```
python -m venv venv
```

To activate your python venv:

```
. venv/bin/activate
```

If you want to deactivate your venv, use `deactivate` command.

> I thought it's good idea to mention about
> [tox](https://tox.readthedocs.io/en/latest/) here. `tox` is very useful tool
> run tests for different Python environments. When you have a properly
> configured `tox.ini` file and all the required Python versions that you need
> to support installed. Just running `tox` command will take care of things.

## Use requirements.txt file for direct dependencies
Use a [requirements.txt](https://pip.pypa.io/en/latest/user_guide/#requirements-files)
file for your direct dependencies, depending on your project requirements you
may add version information as well. But I like to keep the requirements.txt
file without any version information. Let's call this *main requirements* file
because there'll be more.

You can use `pip` inside venv to install your dependencies.

```
pip install -r requirements.txt
```

It's important to keep only the libraries that required to run your
application in this main requirements file. So don't include libraries that's
required for testing, deployment etc in this one.

## What about dependencies of direct dependencies?
Now it's important to version lock dependencies for a production release.
It's a bad idea to let your production environment decide which version to
install because that can lead to breaking changes or unintended side effects.
For that use `requirements.txt.lock` file.

Create this file after installing all your main requirements. You can use
`pip freeze` command for that.

```
pip freeze > requirements.txt.lock
```

This `requirements.txt.lock` must be used when you are deploying to a
production or test server or running tests on a CI/CD pipeline.
If you have to debug a production issue use this file to install dependencies,
so you have same versions of libraries as your production environment has.

> Note that, some libraries depends on operating system and other external
> ibraries, so this does not guarantee that your work environment will be 100%
> imilar to production.
> 
> imilar to python version, pip version matters too. So it's important to make
> ure all environments use same pip version, and keep that up to date.

## What about testing and other tools?
Keep your dependencies for testing in a seperate requirements file. Let's call
that `requirements.test.txt`. Your test dependencies like
[hypothesis](https://hypothesis.readthedocs.io/en/latest/),
[faker](https://github.com/joke2k/faker) can go to that file.

Keep other tools that you use for development like
[ipython](https://ipython.org/) in `requirements.dev.txt` file.

I like to keep tools used for security vulnerability test in a seperate file
called `requirements.sec.txt`, but this could be part of
`requirements.test.txt` as well. I like to keep it seperate because that allows
me to set up a seperate pipeline that only checks for security vulnerabilities
and dependency audits daily.

## Security frist!
Talking about security, it's important audit your `requirements.txt.lock` file
daily. You can use [safety](https://pyup.io/safety/) for that. When `safety`
is installed it's simple as running:

```
safety check -r requirements.txt.lock
```

Another good habit is to keep [pip](https://pip.pypa.io/en/stable/) up to
date. `pip` will let you know if there's an update. You can upgrade `pip`
with following command.

```
pip install --upgrade pip
```

## Constraints files
I haven't used
[Constraint files](https://pip.pypa.io/en/latest/user_guide/#constraints-files)
in my projects so far. These files allows you to main a certain version of
a dependency through out.

If you have a constraint file, you can use that with `pip install` as follow.

```
pip install -c constraints.txt -r requirements.txt
```

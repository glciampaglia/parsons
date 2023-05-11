======================
Parsons Problem Webapp
======================
Parsons programming puzzles are a type of scaffolded program
construction tasks where the learner is given a set of code fragments,
blocks of a single or multiple lines of code,
and the task is to piece together a program from these.
Learners not only select and order but also indent code fragments.

They are challenging problems that reduces the cognitive load
and time spent for students.

This variant of Parsons programming puzzles is called two-dimensional (2D) Parsons problems.
In Python, code indentation has a semantic meaning, as an indented statement falls into
the surrounding control structure, which has lower indentation.
That is, code blocks are deﬁned by indentation instead of start and end symbols like curly braces.

(from *js-parsons*)

The use of Parsons puzzles is an evidence-based teaching practice.

Based on `js-parsons <https://js-parsons.github.io/>`_ and inspired by `Python Tutor <http://pythontutor.com>`_.

Installation
------------

This assumes you have [pyenv](https://github.com/pyenv/pyenv) and
[pipenv](https://github.com/pypa/pipenv) installed. The first step is to create
a new project. The project requires a particular Python version. Currently, the
dependencies are based on Python 3.7.12, so we use pipenv.

Note that building Python will likely require [some additional
packages](https://github.com/pyenv/pyenv#suggested-build-environment) to make
sure the build environment is correct: ::

    pipenv --python 3.7.12

Next, we sync up the environment using the provided lockfile. Since one of the
packages is SQLAlchemy, on my Ubuntu machine (Pop Os! 22.04 LTS), I needed to
install the `libpq-dev` package to provide `pg_config`: ::

    sudo apt install libpq-dev

Then we can sync: ::

    pipenv sync

This will install all dependencies along with the `parsons` package itself.

To run the program, this is just a Flask app, so we need specify what Python object will provide it. It turns out that this is provided by function `create_app()` in the `parsons` package ([source](parsons/__init__.py). So we set an environment variable: ::

    export FLASK_APP=parsons:create_app

Now we can create the database (by default using sqlite): ::

    flask init-db

And finally we can run the Web app: ::

    flask run -h localhost -p 8000

This will spin the Web app locally and have it listen on port 8000.


Example
-------
``find_max`` function:
http://parsons.problemsolving.io/puzzle/cbb39952d55a4be38f935c573a065f9f

Embedded in Jupyter Notebook (you need to run it locally):
https://github.com/ProblemSolvingIO/parsons/blob/master/demo/find-max.ipynb

References
----------
1. Parsons, D., & Haden, P. (2006, January).
   `Parson's programming puzzles: a fun and effective learning tool for first programming courses <http://crpit.com/confpapers/CRPITV52Parsons.pdf>`_.
   In Proceedings of the 8th Australasian Conference on Computing Education-Volume 52 (pp. 157-163).
   Australian Computer Society, Inc.
2. Ihantola, P., & Karavirta, V. (2011).
   `Two-dimensional parson’s puzzles: The concept, tools, and first observations <http://jite.org/documents/Vol10/JITEv10IIPp119-132Ihantola944.pdf>`_.
   Journal of Information Technology Education, 10, 119-132.
3. `CS Teaching Tips - Use Parson’s Puzzles to help students engage with a concept without writing code or experiencing frustrating syntax errors <http://csteachingtips.org/tip/use-parson%E2%80%99s-puzzles-help-students-engage-concept-without-writing-code-or-experiencing>`_.

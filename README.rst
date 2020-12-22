********
pyblanco
********

This is an empty Python project. The purpose is to note down the steps to
create a fresh Python project with a modern layout, using modern tools. Don't
follow these instructions blindly.

Basic setup using ``poetry`` and ``git``
========================================

.. code-block:: bash

    $ poetry new pyblanco
    $ cd pyblanco
    $ sed -i '0,/^$/s/^$/license = "BSL-1.0"\n&/' pyproject.toml
    $ sed -i '0,/^description =/s/""/"An empty Python project"/' pyproject.toml
    $ curl -o LICENSE https://www.boost.org/LICENSE_1_0.txt
    $ curl -o .gitignore https://www.toptal.com/developers/gitignore/api/python
    $ poetry config --local virtualenvs.in-project true
    $ poetry install --no-root
    $ git init
    $ git add .
    $ git commit -m "Initial import"

When creating the virtualenv, use the ``--no-root`` option to leave out the
project itself.

Add and configure ``black``
===========================

.. code-block:: bash

    $ poetry add --dev black

Then add the section ``[tool.black]`` as shown in file `pyproject.toml
<pyproject.toml>`_.

Add and configure ``flake8``
============================

.. code-block:: bash

    $ poetry add --dev flake8

Then add the file `.flake8 <.flake8>`_ to make ``flake8`` compatible with
``black``. See the `black documentation
<https://black.readthedocs.io/en/stable/the_black_code_style.html#line-length>`_
for details.

Add ``rope``
============

``rope`` is used for refactoring in Visual Studio Code, so install it as a
development dependency.

.. code-block:: bash

    $ poetry add --dev rope

Add and install an executable
=============================

Let's say you want to install an executable. ``poetry`` gives you the tooling
to do so easily. Add the following section to your `pyproject.toml
<pyproject.toml>`_:

.. code-block:: toml

    [tool.poetry.scripts]
    blanco = "pyblanco.console:main"

Here, ``blanco`` refers to the executable name, e.g., ``/usr/bin/blanco``.
``pyblanco.console`` is the module within the project and ``main`` refers to
the entry function of the executable ``blanco``.

You may or may not want to install the project now into your virtualenv in
``.venv``.

.. code-block:: bash

    $ poetry install
    $ source .venv/bin/activate
    (.venv) $ which blanco
    ~/some/path/pyblanco/.venv/bin/blanco

For fun, look at the generated executable.

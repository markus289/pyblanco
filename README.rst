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
    $ sed -i '0,/^$/s/^$/license = "EUPL-1.2"\n&/' pyproject.toml
    $ sed -i '0,/^description =/s/""/"An empty Python project"/' pyproject.toml
    $ curl -o LICENSE https://joinup.ec.europa.eu/sites/default/files/custom-page/attachment/2020-03/EUPL-1.2%20EN.txt
    $ curl -o .gitignore https://www.toptal.com/developers/gitignore/api/python
    $ poetry config --local virtualenvs.in-project true
    $ git init
    $ git add .
    $ git commit -m "Initial import"

You may now create a virtual environment that contains all the dependencies.

.. code-block:: bash

    $ poetry install --no-root

When creating the virtual environment, the ``--no-root`` option is used to
leave out the project itself, i.e. ``pyblanco``. Otherwise, the project itself
is installed into the virtual environment. This may or may not be what you
want.

Add and install an executable
=============================

Let's say you want to install an executable. ``poetry`` gives you the tooling
to do so. Add the following section to your `pyproject.toml <pyproject.toml>`_:

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
    $ poetry shell
    (pyblanco-py3.X) $ which blanco
    ~/some/path/pyblanco/.venv/bin/blanco

For fun, look at the generated executable.

Using GitHub Codespaces or Visual Studio Code
=============================================

You may want to use GitHub Codespaces or Visual Studio Code. For this, take a
look at the sample configurations in `.devcontainer <.devcontainer>`_ and
`.vscode <.vscode>`_.

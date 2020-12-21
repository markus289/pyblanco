# pyblanco

This is an empty Python project. The purpose is to note down the steps to
create a fresh Python project with a modern layout, using modern tools. Don't
follow these instructions blindly.

## Basic setup using `poetry` and `git`

    $ poetry new pyblanco
    $ cd pyblanco
    $ sed -i '0,/^$/s/^$/license = "BSL-1.0"\n&/' pyproject.toml
    $ sed -i '0,/^description =/s/""/"An empty Python project"/' pyproject.toml
    $ curl -o LICENSE https://www.boost.org/LICENSE_1_0.txt
    $ curl -o .gitignore https://www.toptal.com/developers/gitignore/api/python
    $ poetry install --no-root
    $ git init
    $ git add .
    $ git commit -m "Initial import"

When creating the virtualenv, use the `--no-root` option to leave out the
project itself.

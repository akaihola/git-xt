====================================================
                       git-xt
====================================================
Utilities for extracting files from git repositories
----------------------------------------------------

-----------
 gitxtract
-----------

Use gitxtract to copy all or some files from a git or mercurial
repository.

Examples
========

This command would copy the most current versions ``gitxtract`` and
``gitxternals`` scripts from the ``git-xt`` repository master branch
to your ``$HOME/bin`` directory::

  gitxtract --branch master --partial gitxtract --partial gitxternals \
            git://github.com/akaihola/git-xt.git ~/bin/


-------------
 gitxternals
-------------

Copy all or some files from multiple git or mercurial repositories.
Specify arguments to successive ``gitxtract`` calls in a
``.gitxternals`` file.  ``gitxtract`` will be executed in the same
directory with the ``.gitxternals`` file.

Examples
========

Let's assume we have a text file ``project/.gitxternals``::

  git://github.com/akaihola/git-xt.git whole-repository
  git://github.com/akaihola/git-xt.git -p gitxtract
  git://github.com/akaihola/git-xt.git -p README.rst -c 609fd8b2331fccc62d9d30a5ebad60716f4cb787

If we now run::

  gitxternals project/

we'll end up with
 * the root of the repository as the ``project/whole-repository`` directory, 
 * the ``gitxtract`` script saved in ``project/gitxtract``
 * the initial version of this ``README.rst`` file as ``project/README.rst``

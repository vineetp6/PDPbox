Tools
=====

For clarity and understanding, here is a list of the tools utilized for this project.


Setuptools
----------

`Setuptools <https://setuptools.pypa.io/en/latest/index.html>`_ is a fully-featured, actively-maintained, 
and stable library designed to facilitate packaging Python projects.

-  :code:`setup.py`: Setuptools offers first class support for :code:`setup.py` files as a configuration mechanism. 
   The file is a sort of "recipe" that includes information like the name of your project, the version, 
   and any packages or modules it needs to work properly.

-  :code:`setup.cfg`: To avoid executing arbitrary scripts and boilerplate code, we are transitioning into a full-fledged :code:`setup.cfg` 
   to declare your package information instead of running :code:`setup()`. 

-  :code:`setup.py` is a Python script used to define setup details and can execute arbitrary code. 
   :code:`setup.cfg` is a configuration file in INI format that also defines setup details, but in a safer, static way. 
   If both files are present, :code:`setup.py` can read from :code:`setup.cfg`. 
   The packaging community is moving towards favoring :code:`setup.cfg` and :code:`pyproject.toml` for a more standardized process.

-  :code:`MANIFEST.in`: Setuptools offers three ways to specify data files to be included in your packages. For the simplest use, 
   you can simply use the :code:`include_package_data` keyword in :code:`setup.cfg`. 
   This tells setuptools to install any data files it finds in your packages. 
   The data files must be specified via the :code:`MANIFEST.in` file or automatically added by a Revision Control System plugin.

-  :code:`requirements.txt`: Specifies the set of dependencies needed for the Python project.
   It can be created manually, but it is recommended to use `pipreqs <https://github.com/bndr/pipreqs>`_ to generate it automatically.
   In this project, we directly get the :code:`install_requires` for :code:`setup.py` from :code:`requirements.txt` file to reduce redundancy. 
   We also reuse the :code:`requirements.txt` file for :code:`readthedocs.xml`.


Documentation
-------------   

``````
Sphinx
``````

`Sphinx <https://www.sphinx-doc.org/en/master/index.html>`_ makes it easy to create intelligent and beautiful documentation.

-  :code:`docs`: The source documentation files in reStructuredText format. 
   To generate docs in html format, simply run: :code:`sphinx-build -b html docs/source docs/build` 
   and you can find the generated html files under :code:`docs/build`.

`````````````
Read the Docs
`````````````

`Read the Docs <https://readthedocs.org/>`_ simplifies software documentation by automating building, versioning, and hosting of your docs for you.

-  :code:`readthedocs.yml`: Read the Docs supports configuring your documentation builds with a YAML file. 
   The configuration file must be in the root directory of your project and be named :code:`.readthedocs.yaml`.

-  `numpydoc <https://numpydoc.readthedocs.io/en/latest/>`_ : Numpy's Sphinx extensions.

-  `sphinx-rtd-theme <https://pypi.org/project/sphinx-rtd-theme/>`_ : Read the Docs theme for Sphinx.

```````````````
Design Diagrams
```````````````

-  **Pyreverse**: Part of the PyLint tool, Pyreverse analyzes your Python code and generates UML diagrams from it. 
   Simply run :code:`pyreverse -o plantuml -d assets/diagrams pdpbox` to generate the UML diagrams.

-  `PlantText <https://www.planttext.com/>`_: PlantText is an online tool that quickly generates images from text. 
   Primarily, it is used to generate UML (Unified Modeling Language) diagrams.


Test & CI
---------

```
Tox
```

`Tox <https://tox.wiki/en/latest/>`_ aims to automate and standardize testing in Python.

-  :code:`tox.ini`: Put basic information about your project and the test environments you want your project to run in 
   into a :code:`tox.ini` file that should reside next to your :code:`setup.py` file.


`````````
Travis CI
`````````

`Travis CI <https://www.travis-ci.com/>`_ is a continuous integration tool that test and deploy your projects with ease.

-  :code:`.travis.yml`: Builds on Travis CI are configured mostly through the build configuration 
   stored in the file :code:`.travis.yml` in your repository. This allows your configuration to be version controlled and flexible.


`````````````
GitHub Action
`````````````

`GitHub Actions <https://docs.github.com/en/actions>`_ is a feature of GitHub that allows you to automate software workflows. 
It's effectively a CI/CD system that's built into GitHub. In the latest refactor, I migrated from Travis CI to GitHub Actions.

-  :code:`.github/workflows/tox-test.yml`: Workflows configuration. 
   Workflows are custom automated processes that you can set up in your repository to build, test, package, release, 
   or deploy any code project on GitHub. 


``````
Others
``````

-  `pipconflictchecker <https://github.com/ambitioninc/pip-conflict-checker>`_ : A tool that checks installed packages 
   against all package requirements to ensure that there are no dependency version conflicts.

-  `coverage <https://coverage.readthedocs.io/en/6.6.0b1/>`_ : A tool for measuring code coverage of Python programs.

   -  :code:`.coveragerc`: A configuration file for :code:`Coverage.py`, a tool for measuring code coverage in Python. 
      The default name for configuration files is :code:`.coveragerc`, in the same directory :code:`coverage.py` is being run in. 

   -  :code:`codecov.yml`: A configuration file for **Codecov**, a tool that collects coverage reports and provides visualizations, 
      analytics, and various other features.

   -  In other words, :code:`.coveragerc` is used to control how coverage data is collected, 
      and :code:`codecov.yml` is used to control how that data is interpreted and presented.

-  `diff-cover <https://github.com/Bachmann1234/diff_cover>`_ : Automatically find diff lines that need test coverage. 
   Also finds diff lines that have violations (according to tools such as pycodestyle, pyflakes, flake8, or pylint). 
   This is used as a code quality metric during code reviews.

   -  :code:`.flake8`: flake8 config for :code:`diff-quality`.

-  `versioneer <https://github.com/python-versioneer/python-versioneer>`_ : A tool for managing a recorded version number in setuptools-based python projects.

   -  :code:`versioneer.py`: To allow :code:`setup.py` to compute a version too, a :code:`versioneer.py` is added to the top level of your source tree, 
      next to :code:`setup.py` and the :code:`setup.cfg` that configures it.


Git
---

-  :code:`.gitattributes`: If the attribute :code:`export-subst` is set for a file then Git will expand several placeholders 
   when adding this file to an archive. 

-  :code:`.gitignore`: Specifies intentionally untracked files to ignore.

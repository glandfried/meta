# Release Your Project on pypi

Releasing your project’s versions on the Python Packaging Index is a great way to keep your users up-to-date, and a convenient way to make your project installable with one easy pip install <yourproject> command. Here are the instructions to make that release happen.
Git

Make sure everything you want for the release is merged in on Github and has tested successfully on your CI. Get your local git repo’s master clean and up to date with username/projectname@master; run tests locally. If you pass, great, move on.

Build a source distribution, so from the top level, where setup.py lives:

    python setup.py sdist

This will create a dist/ directory, in which lies a file, projectname-1.0.0.tar.gz.

Finally, you will upload this file to pypi using twine (you may need to pip install twine if you don’t have it in your current environment). Here’s an example upload command:

    twine upload dist/projectname-1.0.0.tar.gz

You should be able to watch the progress as the dist file uploads. Once the upload completes, go to your page at pypi.org, and make sure the new release is visible there.

Finally, tell the team and users that your release is done. Wait for everything to fall apart.

# Software

[Tips for releasing research code in Machine Learning (with official NeurIPS 2020 recommendations)](https://github.com/paperswithcode/releasing-research-code)


## [Semantic Versioning](https://semver.org/)

Given a version number MAJOR.MINOR.PATCH, increment the:

0. MAJOR version when you make incompatible API changes,
0. MINOR version when you add functionality in a backwards compatible manner, and
0. PATCH version when you make backwards compatible bug fixes.

Additional labels for pre-release and build metadata are available as extensions to the MAJOR.MINOR.PATCH format.

## Style

0. [PEP-8](https://www.python.org/dev/peps/pep-0008/)

### Checkers

0. [flake8](http://flake8.pycqa.org/en/latest/)
0. [pylint](https://www.pylint.org/)

### Auto-formater

0. [black](https://black.readthedocs.io/en/stable/)

##  Documentation

0. [numpy style](https://numpydoc.readthedocs.io/en/latest/format.html)

# molgenis-template-py
A template with boilerplate and pre-made configuration for Python projects

## What's in the box
Using this template will give you out of the box:
- A correctly configured Python package under the `molgenis` namespace
- Automatic code formatting & linting
- A multitude of other checks that are run at commit-time
- A `pipenv` virtual environment with essential dev dependencies pre-installed
- A building and versioning strategy that uses `tox`
- A testing framework with automatically generated coverage and junit reports
- Pre-configured Sonar integration
- Pre-configured Jenkins builds and GitHub integration
- A release strategy that publishes to TestPyPi first and to PyPi when you're ready
- Detailed instructions for your developers on how to start
- ... more!

## How to use
1. Click on the "Use this template" and name your repo. Choose _molgenis_ as owner.
2. Go to the repository's settings. Under _Manage access_, add the following teams:
   * `molgenis/bot` (Admin)
   * `molgenis/development` (Maintain)
   * `molgenis/data-management` (Maintain)
   > Note: You need (to be) an admin to set these permissions.
3. Fork the repository and clone the fork locally
5. In your favorite IDE:
   * Search for all occurrences of `<#CHANGE-ME#>` and replace them individually with something sensible
   * Search for all occurrences of `<#REPO-NAME#>` and replace them all with the name of your new repo (e.g. `molgenis-py-foo`)
   * Rename (refactor) the package `src/molgenis/PROJECT` to your project's name (e.g. `src/molgenis/foo`)
   * Search for `<#PACKAGE-NAME#>` and replace it with the name you gave the package in the previous step
   * Rename `RENAME-Jenkinsfile` to `Jenkinsfile` to activate the build pipeline
6. Commit.
7. Execute the commands described in [For developers](#for-developers) to get yourself up and running.
8. Commit the newly created `Pipfile.lock`.
9. The `example.py` file under the `src` folder contains an example of how to set up the
entry points of your library, application or command-line interface. You can use it as
a starting point, or you can safely remove it. It's up to you!
7. Remove/edit this file :)

## PyScaffold
This project has been set up with PyScaffold 4.1.1. To know more about the standards and
best practices it configures, read [the documentation](https://pyscaffold.org/). Here are
some key points:
- All the configuration for your project should go in `setup.cfg`
- Development is done in a virtual environment. We use [pipenv](https://pipenv.pypa.io/en/latest/).
- Development dependencies should be added to the `Pipfile` (with `pipenv install --dev <package>`),
  normal dependencies should go in `setup.cfg`. `pipenv` will automatically pick these
  up when developing.
- You can use `tox` to build your project and run tests. Just run `tox` to run all tests.
  Take a look at `tox.ini` for the possibilities.
- Code styles are enforced at commit-time. Developers that have not installed the `pre-commit` hooks
will probably see their pull request build fail, so make sure to make that clear to them.
  There are developer instructions that you can use in your README further below. The
  actual checks are configured in `.pre-commit-config.yaml`.

## Other info
Here's some other useful information:
- By default, the project is configured to use Python 3.10. This can be changed in `setup.cfg`
- A build pipeline for Jenkins is added. If you want to add your own build pipeline,
feel free to put up a pull request!
- The Jenkinsfile contains a release flow that uses `tox` to build and release to PyPi.
  The release can be triggered on Jenkins. A build is first published to TestPyPi, where
  you can try out the release before committing to the real thing.
- Your repository and its pull requests are automatically checked by Sonar.



## Docs below this part can be used in your own README:


## For developers
This project uses [pre-commit](https://pre-commit.com/) and [pipenv](https://pypi.org/project/pipenv/)
for the development workflow.

Install pre-commit and pipenv if you haven't already:
```
pip install pre-commit
pip install pipenv
```

Clone or check out this repository with git and install the git commit hooks:
```
pre-commit install
```

Create an environment and install the package including all (dev) dependencies:
```
pipenv install --dev
```

Activate the virtual environment:
```
pipenv shell
```

Build and run the tests:
```
tox
```

>Note: If you want automatic code formatting in your IDE, you need to configure file watchers
  for `black` (the code formatter) and `isort` (the formatter for import statements). Here
  are some examples of how to configure them in `PyCharm`:
>
> ![img.png](.img/example_black_config.png)
> ![img_1.png](.img/example_isort_config.png)

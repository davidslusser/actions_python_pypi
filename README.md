# actions_python_pypi
A Github action for building a python package and publishing to pypi


<br/>

## How to use
In your .github/workflows directory, create a yaml file (such as main.yaml). Add a job for each desired workflow with the `uses` keyword. Use the `with` keyword to pass any desired variables.

Example:

```
on:
  release:
    types: [created]
  workflow_dispatch:
  push:
    tags:
      - '[0-9]+.[0-9]+.[0-9]+'

jobs:
  pypi:
    runs-on: ubuntu-latest
    name: "pypi"
    steps:
      - uses: davidslusser/actions_python_pypi@v1.0.0
        with:
          pypi_username: ${{ secrets.PYPI_USERNAME }}
          pypi_password: ${{ secrets.PYPI_PASSWORD }}
```
<br/>

## Inputs
  - **build_command:** command used to build python package (defaults to "`python -m build`")
  - **pip_install_command:** pip install command (defaults to "`pip install build setuptools setuptools_scm wheel twine`")
  - **pypi_username:** pypi username
  - **pypi_password:** pypi password
  - **python_version:** version of python to run workflow with (defaults to "`3.x`")

<br/>

## Requirements
 - pypi account
 - `PYPI_USERNAME` secret available in your Github actions secrets and variables
 - `PYPI_PASSWORD` secret available in your Github actions secrets and variables

[![Test](https://github.com/cucumber/action-publish-pypi/actions/workflows/test.yaml/badge.svg)](https://github.com/cucumber/action-publish-pypi/actions/workflows/test.yaml)

# action-publish-pypi

Publishes a Python package to https://pypi.org/

Needs Python to be installed first.

## Inputs

* `pypi-token`
* `working-directory` (optional, default `.`)

## Example

```yaml
name: Publish

on:
  push:
    branches:
      - "release/*"

jobs:
  publish-ui:
    name: Publish to PyPI
    runs-on: ubuntu-latest
    environment: Release
    steps:
      - uses: actions/checkout@v2
      - uses: actions/setup-python@v4
        with:
          python-version: "3.10"
      - uses: cucumber/action-publish-pypi@v1.0.0
        with:
          npm-token: ${{ secrets.PYPI_TOKEN }}
          working-directory: "python"
```

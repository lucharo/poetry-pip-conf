# poetry-pip-conf

## Description

*poetry-pip-conf* is a
[plugin](https://python-poetry.org/docs/master/plugins/) for
[poetry](https://python-poetry.org/), the Python packaging and dependency
manager. It enables poetry to use the indices in your pip config file (`pip.conf` in unix based systems).
This makes it simpler to use poetry in corporate environments or environments where access to pypi.org 
is limited. 

This plugin is a fork of [arcesium/poetry-plugin-pypi-mirror](https://github.com/arcesium/poetry-plugin-pypi-mirror)
that fits my use case best. I invite you to read about the limitations of setting up secondary pypi mirrors using poetry 
in the [arcesium/poetry-plugin-pypi-mirror](https://github.com/arcesium/poetry-plugin-pypi-mirror) repo. 

## Usage

### Installation

```
poetry self add poetry-pip-conf
```

Read more about managing plugins in [poetry's documentation](https://python-poetry.org/docs/master/plugins/#using-plugins)

No further setup is required. The plugin will look for a pip.conf/pip.ini
under the locations displayed by `pip config list -v`.

## Example custom pip.conf/pip.ini

```ini
[global]
trusted-host = test.pypi.org

[install]
index-url = https://test.pypi.org/simple
extra-index-url = https://pypi.org/simple
		https://mirrors.sustech.edu.cn/pypi/simple

[search]
index = https://test.pypi.org/simple
```

## Compatibility

*poetry-pip-conf* depends on poetry internals which can change between
poetry releases. *poetry-pip-conf* only works
with poetry 1.3.0 and above.

## See also

* [python-poetry/poetry#1632](https://github.com/python-poetry/poetry/issues/1632) - poetry feature request to add support for global repository URL replacement

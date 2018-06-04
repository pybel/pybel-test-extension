# pybel-test-extension

An example of a PyBEL extension.

**Warning:** PyBEL v0.11.2 is the last version of PyBEL to support extension loading; the functionality was removed in [commit `c845c66`](https://github.com/pybel/pybel/commit/c845c66eba844aaed23aec16a8d70c2024424ed9) on 4 June 2018. In place of the `pybel.ext` namespace, just create your extensions as normal packages and import them under their own names. This repository will remain, in its deprecated state, for historical preservation and to ensure any old tests remain functional.

## Usage

This package has not been uploaded to PyPI, so you'll have to get it from GitHub.

```sh
$ git clone https://github.com/pybel/pybel-test-extension.git
$ cd pybel-test-extension
$ pip install .
```

or

```sh
pip install git+https://github.com/pybel/pybel-test-extension.git@master
```

Once installed, all you need to do to access the extension is import `pybel`:

```python
>>> import pybel
>>> pybel.ext.test.an_extension_function()
42
```

## Creating Your Own Extension

The magic happens in your `setup.py`:

```python
setuptools.setup(
    ...
    entry_points = {
        'pybel.ext':
            ['name_of_extension = package.module']
    }
    ...
)
```

The group `pybel.ext` must be used in order for the extension to be recognized by PyBEL. You can name your extension whatever you want, but attempt to avoid name collisions. The string after the equals sign must point to an importable module which contains your extension--it works just like the standard `console_scripts` entry point.


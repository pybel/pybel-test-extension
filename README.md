# pybel-test-extension

An example of a PyBEL extension.

## Usage

This package has not been uploaded to PyPI, so you'll have to get it from GitHub.

```sh
$ git clone https://github.com/pybel/pybel-test-extension.git
$ cd pybel-test-extension
$ pip install .
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

The group `pybel.ext` must be used in order for the extension to be recognized by PyBEL. You can name your extension whatever you want, but attempt to avoid name collisions. PyBEL will issue a warning if a collision is detected and only the first extension imported will be available. The string after the equals sign must point to an importable module which contains your extension--it works just like the standard `console_scripts` entry point.


# Example Package with Nim

This is a simple example package with Nim module.

See blog post for more info: [Python packages using Nim](https://domaindriven.dev/2020/08/30/python-packages-using-nim/).

## Build steps

NOTE: These build steps are using Linux/macOS or similar. For Windows, the Nim
module will be compiled to `mymodule.pyd` instead of `mymodule.so`.

```bash
cd py_module_nim/example_pkg/
nimble install nimpy
nim compile --threads:on --app:lib --out:mymodule.so mymodule
cd ..
virtualenv venv
source venv/bin/activate
python setup.py sdist bdist_wheel
```

## Publish steps

```bash
cd py_module_nim/
pip install twine
twine upload dist/*
```

## Example using package

Write the following Python script to file named `try.py`:

```python
from example_nim_pkg import mymodule
print(mymodule.greet("World"))
```

Install the `example-nim-pkg-stever` package and run the script:

```bash
pip install example-nim-pkg-stever
python try.py
```

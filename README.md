# Example Package with Nim

This is a simple example package with Nim module.

## Build steps

```bash
cd py_module_nim/example_pkg/
nimble install nimpy
nim compile --threads:on --app:lib --out:mymodule.so mymodule
cd ..
virtualenv venv
source venv/bin/activate
python main.py
```

```bash
python setup.py sdist bdist_wheel
```

```bash
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

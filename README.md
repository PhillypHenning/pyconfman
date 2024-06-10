# pyconfman2

pyconfman2 is a configurable Python package for managing configurations. It allows loading, adding, removing, and iterating over configuration properties from dictionaries or YAML files.

## Project Structure

```
pyconfman2/
  src/
    pyconfman2/
      __init__.py
      Schema.py
      Exceptions.py
  tests/
    __init__.py
    test_schema.py
    test_exceptions.py
```

## Installation

To use `pyconfman2` in your project, you can clone the repository and install the necessary dependencies with:

```bash
pip install pyconfman2
```

## Usage

### ConfigSchema

The `ConfigSchema` class allows you to manage configuration properties.

#### Initialization

You can initialize a `ConfigSchema` object with a default schema dictionary, a filepath to a YAML configuration file, or a default configuration file.

```python
from src.pyconfman2.Schema import ConfigSchema

default_schema = {'key1': 'value1', 'key2': 'value2'}
config_schema = ConfigSchema(default_schema=default_schema)

# Or from a file
config_schema = ConfigSchema(filepath="path/to/config.yaml")
```

#### Adding Properties

Add properties using a dictionary or key-value pair.

```python
config_schema.add({'key3': 'value3'})
config_schema.add('key4', 'value4')
config_schema.add('key4', 'new_value4', override=False)  # Won't override existing key
```

#### Getting Properties

Get the value of a specific property.

```python
value = config_schema.get('key1')
```

#### Removing Properties

Remove a property.

```python
config_schema.remove('key1')
```

#### Iteration

Iterate over the properties.

```python
for key, value in config_schema:
    print(key, value)
```

### Loading Configuration from File

Load properties from a YAML file.

```python
config_schema.load('path/to/config.yaml')
```

### Exceptions

pyconfman2 defines custom exceptions to handle specific error scenarios.

- `InvalidPropertyError`
- `EmptyValueProperty`
- `KeyExistsError`

## Running Tests

The project includes unit tests for `ConfigSchema` and the custom exceptions using the `unittest` framework. To run the tests, set the `PYTHONPATH` and use `unittest`.

On Unix-based systems (Linux/macOS):
```bash
export PYTHONPATH=$(pwd)/src
python -m unittest discover -s tests
```

On Windows:
```bash
set PYTHONPATH=%cd%\src
python -m unittest discover -s tests
```

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

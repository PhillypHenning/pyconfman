# pyconfman

pyconfman is designed to handle schema configurations by loading properties from a dictionary or a YAML configuration file. It provides methods for adding, getting, and removing properties from the schema.

### Local Setup and Testing
Set up Python virtual environment

```bash
python -m venv local
source local/bin/activate
```

Install the project requirements
```bash
python -m pip install -r requirements.txt
```

Run the unit tests
```bash
cd tests
python -m unittest
```

## Installation
```bash
python -m pip install pyconfman
```

## Usage

### Basic
In it's most basic form, a Schema can be created which will load a local "config.yaml" or "config.yml" file present.

```python
from pyconfman import Schema

config=Schema()
```

### Provide a default config
```python
from pyconfman import Schema

config=Schema({"foo": "bar"})
```

### Specify the default config file to load
```python
from pyconfman import Schema

config=Schema(default_config="default_config.yaml")
```


### Specify the config file to load
```python
from pyconfman import Schema

config=Schema(filepath="another_config.yaml")
```


## Schema Loading breakdown
__init__
  1. Load the hard-coded defaults
  2. Load (and override) using the "default config" file if present
  3. Load (and override) using the config file if present

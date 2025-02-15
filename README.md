# ByteSize: A Simple Library for Byte Size Operations

ByteSize takes the pain out of data-size conversions—efficiently handle metric/binary units, block alignment, and more, all from a single, Pythonic interface.

[![pixi-badge](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/prefix-dev/pixi/main/assets/badge/v0.json&style=flat-square)](https://github.com/prefix-dev/pixi)
[![Ruff](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/astral-sh/ruff/main/assets/badge/v2.json&style=flat-square)](https://github.com/astral-sh/ruff)
[![Built with Material for MkDocs](https://img.shields.io/badge/mkdocs--material-gray?logo=materialformkdocs&style=flat-square)](https://github.com/squidfunk/mkdocs-material)

<!-- ![Python Version from PEP 621 TOML](https://img.shields.io/python/required-version?file=https://raw.githubusercontent.com/jjjermiah/ByteSize/main/pyproject.toml) -->

![GitHub last commit](https://img.shields.io/github/last-commit/jjjermiah/ByteSize?style=flat-square)
![GitHub issues](https://img.shields.io/github/issues/jjjermiah/ByteSize?style=flat-square)
![GitHub pull requests](https://img.shields.io/github/issues-pr/jjjermiah/ByteSize?style=flat-square)

![GitHub contributors](https://img.shields.io/github/contributors/jjjermiah/ByteSize?style=flat-square)
![GitHub stars](https://img.shields.io/github/stars/jjjermiah/ByteSize?style=flat-square)
![GitHub forks](https://img.shields.io/github/forks/jjjermiah/ByteSize?style=flat-square)

![GitHub release (latest by date)](https://img.shields.io/github/v/release/jjjermiah/ByteSize?style=flat-square)

`ByteSize` is a Python library that simplifies operations with file sizes, offering dynamic unit conversions, string parsing, formatting, and more.

## Features

- Parse human-readable size strings (e.g., `"10MB"`, `"1.5GiB"`) into raw bytes.
- Convert between metric (e.g., `MB`) and binary units (e.g., `MiB`).
- Arithmetic operations while preserving byte units.
- Block-aligned size calculations.
- User-friendly formatting with customizable precision.
- No dependencies, lightweight, and easy to use.

## Installation

Clone the repository and install the package:

```bash
pip install pybytesize
```

## Quickstart Guide

### Creating a `ByteSize` Object

Create a `ByteSize` object from integers or human-readable strings.

```python
from bytesize import ByteSize

size1 = ByteSize(1048576)  # From bytes
size2 = ByteSize("1MB")    # From a string
print(size1)  # Outputs: '1.00 MiB'
# Output: 1.00 MiB
```

### Unit Conversion

Access size in different units dynamically.

```python
print(size1.MB)       # Metric: 1.048576 MB
# Output: 1.048576
print(size1.MiB)      # Binary: 1.00 MiB
# Output: 1.00
print(size1.readable_metric)  # ('MB', 1.05)
# Output: ('MB', 1.05)
print(size1.readable_binary)  # ('MiB', 1.00)
# Output: ('MiB', 1.00)
```

## Advanced Usage

### Arithmetic with Sizes

Perform addition, subtraction, multiplication, and division.

```python
size3 = ByteSize("1GB") + ByteSize("512MB")
print(size3)  # '1.50 GiB'
# Output: 1.50 GiB

size4 = ByteSize("1TB") - ByteSize("500GB")
print(size4)  # '0.50 TiB'
# Output: 0.50 TiB
```

### Formatting Sizes

Customize formatting for specific units or precision.

```python
size = ByteSize(123456789)
print(f"{size:.2f:MB}")  # '123.46 MB'
# Output: 123.46 MB
print(f"{size:.2f:GiB}") # '0.11 GiB'
# Output: 0.11 GiB
```

### Block Alignment

Calculate the apparent size with block alignment.

```python
aligned_size = size.apparent_size(4096)
print(aligned_size)  # Example: ByteSize(123456768)
# Output: ByteSize(123456768)
```

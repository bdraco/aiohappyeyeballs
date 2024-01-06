# aiohappyeyeballs

<p align="center">
  <a href="https://github.com/aio-libs/aiohappyeyeballs/actions/workflows/ci.yml?query=branch%3Amain">
    <img src="https://img.shields.io/github/actions/workflow/status/aio-libs/aiohappyeyeballs/ci.yml?branch=main&label=CI&logo=github&style=flat-square" alt="CI Status" >
  </a>
  <a href="https://aiohappyeyeballs.readthedocs.io">
    <img src="https://img.shields.io/readthedocs/aiohappyeyeballs.svg?logo=read-the-docs&logoColor=fff&style=flat-square" alt="Documentation Status">
  </a>
  <a href="https://codecov.io/gh/aio-libs/aiohappyeyeballs">
    <img src="https://img.shields.io/codecov/c/github/aio-libs/aiohappyeyeballs.svg?logo=codecov&logoColor=fff&style=flat-square" alt="Test coverage percentage">
  </a>
</p>
<p align="center">
  <a href="https://python-poetry.org/">
    <img src="https://img.shields.io/badge/packaging-poetry-299bd7?style=flat-square&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA4AAAASCAYAAABrXO8xAAAACXBIWXMAAAsTAAALEwEAmpwYAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAJJSURBVHgBfZLPa1NBEMe/s7tNXoxW1KJQKaUHkXhQvHgW6UHQQ09CBS/6V3hKc/AP8CqCrUcpmop3Cx48eDB4yEECjVQrlZb80CRN8t6OM/teagVxYZi38+Yz853dJbzoMV3MM8cJUcLMSUKIE8AzQ2PieZzFxEJOHMOgMQQ+dUgSAckNXhapU/NMhDSWLs1B24A8sO1xrN4NECkcAC9ASkiIJc6k5TRiUDPhnyMMdhKc+Zx19l6SgyeW76BEONY9exVQMzKExGKwwPsCzza7KGSSWRWEQhyEaDXp6ZHEr416ygbiKYOd7TEWvvcQIeusHYMJGhTwF9y7sGnSwaWyFAiyoxzqW0PM/RjghPxF2pWReAowTEXnDh0xgcLs8l2YQmOrj3N7ByiqEoH0cARs4u78WgAVkoEDIDoOi3AkcLOHU60RIg5wC4ZuTC7FaHKQm8Hq1fQuSOBvX/sodmNJSB5geaF5CPIkUeecdMxieoRO5jz9bheL6/tXjrwCyX/UYBUcjCaWHljx1xiX6z9xEjkYAzbGVnB8pvLmyXm9ep+W8CmsSHQQY77Zx1zboxAV0w7ybMhQmfqdmmw3nEp1I0Z+FGO6M8LZdoyZnuzzBdjISicKRnpxzI9fPb+0oYXsNdyi+d3h9bm9MWYHFtPeIZfLwzmFDKy1ai3p+PDls1Llz4yyFpferxjnyjJDSEy9CaCx5m2cJPerq6Xm34eTrZt3PqxYO1XOwDYZrFlH1fWnpU38Y9HRze3lj0vOujZcXKuuXm3jP+s3KbZVra7y2EAAAAAASUVORK5CYII=" alt="Poetry">
  </a>
  <a href="https://github.com/ambv/black">
    <img src="https://img.shields.io/badge/code%20style-black-000000.svg?style=flat-square" alt="black">
  </a>
  <a href="https://github.com/pre-commit/pre-commit">
    <img src="https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit&logoColor=white&style=flat-square" alt="pre-commit">
  </a>
</p>
<p align="center">
  <a href="https://pypi.org/project/aiohappyeyeballs/">
    <img src="https://img.shields.io/pypi/v/aiohappyeyeballs.svg?logo=python&logoColor=fff&style=flat-square" alt="PyPI Version">
  </a>
  <img src="https://img.shields.io/pypi/pyversions/aiohappyeyeballs.svg?style=flat-square&logo=python&amp;logoColor=fff" alt="Supported Python versions">
  <img src="https://img.shields.io/pypi/l/aiohappyeyeballs.svg?style=flat-square" alt="License">
</p>

---

**Documentation**: <a href="https://aiohappyeyeballs.readthedocs.io" target="_blank">https://aiohappyeyeballs.readthedocs.io </a>

**Source Code**: <a href="https://github.com/aio-libs/aiohappyeyeballs" target="_blank">https://github.com/aio-libs/aiohappyeyeballs </a>

---

Happy Eyeballs

## Use case

This library exists to allow connecting with Happy Eyeballs when you
already have a list of addrinfo and not a DNS name.

The stdlib version of `loop.create_connection()`
will only work when you pass in an unresolved name which
is not a good fit when using DNS caching or resolving
names via another method such was `zeroconf`.

## Installation

Install this via pip (or your favourite package manager):

`pip install aiohappyeyeballs`

## Example usage

```python

addr_infos = await loop.getaddrinfo("example.org", 80)

socket = await start_connection(addr_infos)
socket = await start_connection(addr_infos, local_addr_infos=local_addr_infos, happy_eyeballs_delay=0.2)

transport, protocol = await loop.create_connection(
    MyProtocol, sock=socket, ...)

# Remove the first address for each family from addr_info
pop_addr_infos_interleave(addr_info, 1)

# Remove all matching address from addr_info
remove_addr_infos(addr_info, "dead::beef::")

# Convert a local_addr to local_addr_infos
local_addr_infos = addr_to_addr_infos(("127.0.0.1",0))
```

## Credits

This package contains code from cpython and is licensed under the same terms as cpython itself.

This package was created with
[Copier](https://copier.readthedocs.io/) and the
[browniebroke/pypackage-template](https://github.com/browniebroke/pypackage-template)
project template.

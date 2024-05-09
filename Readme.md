# laszip-python

Unofficial bindings between [Python][python-site] and [LASzip][laszip-github] made
using [pybind11][pybind11-github].

The main purpose is for integration within [laspy][laspy-github].

# Building

Building can be done using cmake or pip.

First `pybind11` needs to be installed. You can install it via `vcpkg` or `conda` or other means.

By default a vendored version of LASZip is used, to use the system installed version
pass `-DUSE_VENDORED_LASZIP=OFF`
```
set -gx SKBUILD_CMAKE_ARGS "-DUSE_VENDORED_LASZIP=OFF"
pip wheel .
```

To help cmake find Laszip you may have to use `-DCMAKE_TOOLCHAIN_FILE=/some/path/vcpg.cmake`
if you used vcpkg to install laszip, or `-DCMAKE_PREFIX_PARTH`
(or `-DCMAKE_INCLUDE_PATH=...` and `-DCMAKE_LIBRARY_PATH=...` in rare cases).


As setup.py calls cmake the same options make need to be given:
```shell
set -gx SKBUILD_CMAKE_ARGS -DCMAKE_PREFIX_PATH=...
pip install .
```

## Source distribution
```
pip install build
python -m build . --sdist
```

[laszip-github]: https://github.com/LASzip/LASzip
[python-site]: https://www.python.org/ 
[pybind11-github]: https://github.com/pybind/pybind11
[laspy-github]: https://github.com/laspy/laspy
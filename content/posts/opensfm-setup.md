---
title: "Structure from Motion : How to Setup OpenSfM"
date: 2018-12-04T13:57:56+07:00
author: "Watchanan Chantapakul"
tags: ["opensfm"]
---
Hi folks!

As I was assigned to do the preliminary about an interesting computer vision algorithm named **Structure from Motion**, so I am going be breaking the process down a bit as it can ease your process getting into SfM.

<!--more-->

There are people who already implemented SfM algorithm in many languages such as MATLAB, C++, and Python. I have done some searches and found out that `OpenSfM` library is a potential library to be used mainly because it is an open-source project, so I can see how the code works.

Let's get started with how to setup the library.

## Building
This part is going to be about how to build the library from its source codes.
First of all, we have to clone the project from GitHub using `--recursive` option.
```bash
git clone --recursive https://github.com/mapillary/OpenSfM
```
Then we need to make sure that the submodules are updated.
```bash
cd OpenSfM && git submodule update --init --recursive
```

### Installing Dependencies
The main dependencies we have to install are:
1. OpenCV
1. OpenGV
1. Ceres Solver
1. NumPy, SciPy, Networkx, PyYAML, exifread

### opensfm
If you only want to build the source codes to bin/ directory, it will automatically build all codes for you.
```bash
python3 setup.py build
```
Just in case that you need to install the `opensfm` package, then use install command through `setup.py` file.
```bash
python3 setup.py install
```

## Troubleshooting
This section is dedicated to some issues you might be encountering during the setup process.

### HTTP Server
As the library utilizes Python simeple HTTP server, in Python 3, you have to use this command instead of the indicated command in the document.
```bash {linenos=table}
#python3 -m SimpleHTTPServer
python3 -m http.server
```

### Python Version
#### Running Python Scripts
On `Linux`, if you are running the OpenSfM scripts with your default python command, it is going to call your `python`, which means Python version 2 by default. So you have to change some files to make it works normally.
##### bin/opensfm
```python {linenos=table}
#!/usr/bin/env python3
# the very first line, change it from `python` to `python3`
```
##### bin/opensfm_run_all
```bash {linenos=table}
# PYTHON=${2:-python}
PYTHON=${2:-python3}
```

### Python Packages
#### pyproj
The required dependency of `pyproj` is `cython`, so just install it before installing pyproj.
```bash
pip3 install cython
```
The default remote url is sometimes unavailable, so you can use this link instead.
```bash
pip3 install git+https://github.com/jswhit/pyproj.git
```

### Building Document
#### Sphinx
The document is written on the `Sphinx` tool and `sphinx_rtd_theme`. If you don't have these packages, just install them through *pip*.
```bash {linenos=table}
pip3 install Sphinx
pip3 install sphinx_rtd_theme
```

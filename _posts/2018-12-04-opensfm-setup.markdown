---
layout: post
title:  "Structure from Motion : How to Setup OpenSfM"
date:   2018-12-04 13:57:56 +0700
categories: opensfm cv
---
Hi folks!

As I was assigned to do the preliminary about an interesting computer vision algorithm named **Structure from Motion**, so I am going be breaking the process down a bit as it can ease your process getting into SfM.

There are people who already implemented SfM algorithm in many languages such as MATLAB, C++, and Python. I have done some searches and found out that `OpenSfM` library is a potential library to be used mainly because it is an open-source project, so I can modify its codes arbitrarily.

Let's get started with how to setup the library.

## Building
This part is going to be about how to build the library from its source codes.
First of all, we have to clone the project from GitHub using `--recursive` option.
{% highlight bash %}
git clone --recursive https://github.com/mapillary/OpenSfM
{% endhighlight %}
Then we need to make sure that the submodules are updated.
{% highlight bash %}
cd OpenSfM && git submodule update --init --recursive
{% endhighlight %}

### Installing Dependencies
The main dependencies we have to install are:
1. OpenCV
1. OpenGV
1. Ceres Solver
1. NumPy, SciPy, Networkx, PyYAML, exifread

### opensfm
If you only want to build the source codes to bin/ directory, it will automatically build all codes for you.
{% highlight bash %}
python3 setup.py build
{% endhighlight %}
Just in case that you need to install the `opensfm` package, then use install command through `setup.py` file.
{% highlight bash %}
python3 setup.py install
{% endhighlight %}

## Troubleshooting
This section is dedicated to some issues you might be encountering during the setup process.

### HTTP Server
As the library utilizes Python simeple HTTP server, in Python 3, you have to use this command instead of the indicated command in the document.
{% highlight python %}
#python3 -m SimpleHTTPServer
python3 -m http.server
{% endhighlight %}

### Python Packages
#### pyproj
The required dependency of `pyproj` is `cython`, so just install it before installing pyproj.
{% highlight bash %}
pip3 install cython
{% endhighlight %}
The default remote url is sometimes unavailable, so you can use this link instead.
{% highlight bash %}
pip3 install git+https://github.com/jswhit/pyproj.git
{% endhighlight %}

### Building Document
### Sphinx
The document is written on the `Sphinx` tool and `sphinx_rtd_theme`. If you don't have these packages, just install them through *pip*.
{% highlight bash %}
pip3 install Sphinx
pip3 install sphinx_rtd_theme
{% endhighlight %}

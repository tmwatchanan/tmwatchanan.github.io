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


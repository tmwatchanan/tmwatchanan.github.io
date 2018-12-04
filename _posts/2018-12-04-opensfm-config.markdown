---
layout: post
title:  "Structure from Motion : OpenSfM Configuration"
date:   2018-12-04 14:21:33 +0700
categories: opensfm cv
---
Hi folks!

Before reading this post, I hope that you have already read the former post about [How to Setup OpenSfM]({% post_url 2018-12-04-opensfm-setup %}).

There are lots of configs we can change inside the OpenSfM library. The main file that contains this configuration is `config.yaml`.
Each `config.yaml` file will be placed inside each dataset folder. For instance, the config file of an example dataset named `berlin` is located in `ROOT/berlin/config.yaml`.

The full options we can configure is provided [here][opensfm-config].

## Features
The library has the file that indicates which feature we will use. The file is located in `opensfm/features.py`.
There are a number of feature types provided out-of-the-box:
+ SIFT
+ SURF
+ AKAZE
+ HAHOG (default)
+ ORB

<span style="color:red">Note that `opencv_contrib` is required to be able to use SIFT or SURF.</span>
So if you want to change the feature algorithm within these algorithms, you can change the `config.yaml` file with this line.
{% highlight yaml %}
feature_type: SIFT
{% endhighlight %}
And each feature extraction algorithm also has its parameters, for example, in the case of SIFT.
{% highlight yaml %}
# Params for SIFT
sift_peak_threshold: 0.1     # Smaller value -> more features
sift_edge_threshold: 10       # See OpenCV doc
{% endhighlight %}

[opensfm-config]: https://github.com/mapillary/OpenSfM/blob/master/opensfm/config.py

---
layout: post
title:  "Structure from Motion : OpenSfM Configuration"
date:   2018-12-04 14:21:33 +0700
categories: opensfm cv
---
Hi folks!

Before reading this post, I hope that you have already read the former post about [How to Setup OpenSfM]({% post_url 2018-12-04-opensfm-setup %}).

First of all, I am going to give you an instruction of running the library. But actually, it is pretty simple and straightforward because it is a library, so a lot of abstraction is working for us.
Assume that the dataset's name is `berlin`.
1. Simply run this command
{% highlight bash %}
bin/opensfm_run_all data/berlin
{% endhighlight %}
2. If you want to generate a denser point cloud in `.ply` file format, then run these commands
{% highlight bash %}
bin/opensfm undistort data/berlin
bin/opensfm compute_depthmaps data/berlin
{% endhighlight %}
3. The created file will be located in `data/berlin/depthmaps/merged.ply`.

To create a new dataset, for example, `tommy`, go to `data/` folder and create a new folder with your dataset name. Then create another `images` folder inside the folder. All images will be placed in `data/tommy/images` as shown below.
```
.
├── config.yaml
├── images
    ├── 001.jpg
    ├── 002.jpg
    ├── 003.jpg
```


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

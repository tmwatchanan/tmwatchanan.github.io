---
title: "Ubuntu 18.04 + CUDA + Nvidia : How to Set Them Up"
date: 2018-12-18T14:07:56+07:00
author: "Watchanan Chantapakul"
tags: ["ubuntu", "cuda", "nvidia"]
---
Hi folks!

To make the CUDA works on a computer might be a pain for someone including me, so I just want to memorise the way I make the system work without any problem. In this post, it is based on these requirements:
<!--more-->
- Ubuntu 18.04
- Nvidia graphic card


## Compatibility

The first thing you need to do is to check the compability between `Cuda Toolkit version` and `Linux x86_64 driver version`. You can quickly look up the table [here][cuda-compatibility-table]. In the case that you want to look at other details, you can go to [CUDA Compatibility :: GPU Deployment and Management Documentation][cuda-compatibility].

For instance, now (2018-12-18), the most up-to-date CUDA version is 10.1, so I will stick to this version, then I check the aforementioned table. As a result, I have to install Nvidia driver for Linux 410, as It says (CUDA 10.0 (10.0.130) >= 410.48).

## Nvidia Driver

To install the Nvidia driver 410, just type this (debian-based):
```bash
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt install nvidia-driver-410
```
And do not forget to reboot your Linux with `sudo reboot` command.

## CUDA
Firstly, you have to download the [CUDA Toolkit installer][cuda-installer]. Note that the version of CUDA Toolkit must be matched with your Nvidia driver version, and vice versa. There are about 4 different ways to install it, so you can easily follow its instruction, but the one that I recommend is to use **runfile (local)** approach as there are only 2 steps to complete it.

## Test

```bash {lineon=true}
cp /usr/local/cuda/cuda-testing/samples
make
```
You can make the make comamnd run faster by adding a flag `-j?`. The `?` is the number of parallel threads you want it to operate, so the more threads, the more processors you assign it to use. For instance, if my CPU has 8 cores, I can run make command as `make -j8`.

Let's run an example to check whether it works flawlessly with this command:
```bash
./bin/x86_64/linux/release/vectorAdd
```

<!-- ## Caffe -->
<!-- {% highlight bash %} -->
<!-- sudo apt install libprotobuf-dev libleveldb-dev libsnappy-dev libopencv-dev libhdf5-serial-dev protobuf-compiler -->
<!-- sudo apt install --no-install-recommends libboost-all-dev -->
<!-- sudo apt install liblmdb-dev -->
<!-- sudo apt install libatlas-base-dev -->
<!-- {% endhighlight %} -->

[cuda-compatibility]: https://docs.nvidia.com/deploy/cuda-compatibility/index.html
[cuda-compatibility-table]: https://docs.nvidia.com/deploy/cuda-compatibility/index.html#binary-compatibility__table-toolkit-driver
[cuda-installer]: https://developer.nvidia.com/cuda-downloads
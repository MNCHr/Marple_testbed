# testbed
Testing infrastructure for needlstk

Mininet
=============================

Launch an EC2 instance with Ubuntu 14.04 as the operating system.
Unfortunately, the default Ubuntu 14.04 AMI on EC2 has kernel version 3.13.0-105-generic,
which has an error when setting net.ipv4.neigh.default.gc_thresh1/2/3,
as documented here (https://bugs.launchpad.net/ubuntu/+source/linux-lts-trusty/+bug/1634892)

Mininet needs to set net.ipv4.neigh.default.gc_thresh1/2/3 as part of its boot up
(https://github.com/mininet/mininet/blob/3284b04f2bbfae83636105ff1dcab5d026f75825/mininet/util.py#L447)

The mininet VM image has a later version of the kernel:
3.19.0-78-generic, which fixed this issue

You can upgrade to a 3.19 kernel using the command:
sudo apt-get install linux-generic-lts-vivid
, followed by rebooting the machine

Spark Streaming
==============================
Get Spark Streaming from http://d3kbcqa49mib13.cloudfront.net/spark-2.1.0-bin-hadoop2.7.tgz

UDP ON/OFF traffic and HTTP client
==============================
Consider using Rust for this: https://doc.rust-lang.org/1.14.0/std/net/index.html
May be more adventurous than required.

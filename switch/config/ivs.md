---
layout: default
title: Ryu Certification - ivs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ivs

# OpenFlow related configuration
<pre>
$ /usr/sbin/ivs --pipeline=standard-1.3 -c 10.24.150.30:6633 --dpid 0000000000000001 -i eth21 -i eth22 -i eth23
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 6878160b5c2036b339f060f6f3fc4711bb9fafbb
Merge: a239e5f a8dfb75
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Thu Oct 2 18:20:22 2014 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Thu Oct 2 18:20:22 2014 -0700

    Merge into master from pull request #207:
    increase maximum number of file descriptors to 4096 (https://github.com/floodlight/ivs/pull/207)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     3723E7CFB3400337BB56317
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

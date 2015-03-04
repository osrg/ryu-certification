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
commit 18076eb936a93414119065c1789e9f7787b766a1
Merge: 6247e5f 7ad2dee
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Tue Mar 3 17:05:41 2015 -0800
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Tue Mar 3 17:05:41 2015 -0800

    Merge into master from pull request #256:
    build Ubuntu 14.04 packages using Docker, and other build system improvements (https://github.com/floodlight/ivs/pull/256)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     AD40B500DD5C28718A043A4
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

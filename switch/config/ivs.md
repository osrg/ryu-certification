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
commit 1e6a7cdb5ad7235b4e0ba722e46817973c28b08c
Merge: 127f0c7 b80c02e
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Tue Mar 31 15:13:27 2015 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Tue Mar 31 15:13:27 2015 -0700

    Merge into master from pull request #285:
    packet_trace: fix logging bug (https://github.com/floodlight/ivs/pull/285)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     20B4C851BF1F0F70A9AED29
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

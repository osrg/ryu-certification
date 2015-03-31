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
commit a5a5b3166dd6b171432898e90f458612c133f2c1
Merge: 7c405a7 90dbfa8
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Tue Mar 31 09:40:33 2015 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Tue Mar 31 09:40:33 2015 -0700

    Merge into master from pull request #284:
    cleanup getting the vport MAC address (https://github.com/floodlight/ivs/pull/284)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     20B4C851BF1F0F70A9AED29
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

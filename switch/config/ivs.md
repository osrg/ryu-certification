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
commit bcdff77481eb9bc9bd6733668ea662c2daeb0f5e
Merge: c3b944d 30d6460
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Mon Mar 30 15:59:40 2015 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Mon Mar 30 15:59:40 2015 -0700

    Merge into master from pull request #282:
    OVSDriver: reuse kernel datapath (https://github.com/floodlight/ivs/pull/282)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     20B4C851BF1F0F70A9AED29
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

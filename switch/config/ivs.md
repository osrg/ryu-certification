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
commit 670adb72f34bb7f8f6d692d19f5f5a6d9ccf4990
Merge: 5cb535d 3afe922
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Tue Nov 18 11:00:28 2014 -0800
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Tue Nov 18 11:00:28 2014 -0800

    Merge into master from pull request #222:
    Fix multicast socket overrun (https://github.com/floodlight/ivs/pull/222)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     E7E5DFE64E79BDBFF178C1A
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

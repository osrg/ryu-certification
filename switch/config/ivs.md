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
commit 3edf731524623b8a24e2a6e1b1015f0ab4382acb
Merge: f17b384 becc5f3
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Fri Mar 6 18:03:31 2015 -0800
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Fri Mar 6 18:03:31 2015 -0800

    Merge into master from pull request #263:
    set BUILD_ID when building packages using Docker (https://github.com/floodlight/ivs/pull/263)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     AD40B500DD5C28718A043A4
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

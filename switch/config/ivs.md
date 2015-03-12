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
commit 92669baae7c08e60f22f09142a61ca36c13d4897
Merge: a97780b 2964e95
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Wed Mar 11 17:26:30 2015 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Wed Mar 11 17:26:30 2015 -0700

    Merge into master from pull request #267:
    ivs: continue startup after failing to add a port (https://github.com/floodlight/ivs/pull/267)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     AD40B500DD5C28718A043A4
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

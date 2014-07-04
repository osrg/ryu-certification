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
commit 73205fb4c836b10930ea7b23e1b5c0e8b3f59ef6
Merge: 1981a30 a094fdc
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Thu Jul 3 15:14:49 2014 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Thu Jul 3 15:14:49 2014 -0700

    Merge into master from pull request #183:
    support port counters in ivs (https://github.com/floodlight/ivs/pull/183)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     F59B363F4F274FB51AE1897
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

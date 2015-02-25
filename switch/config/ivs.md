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
commit 53b9f6828aa31f59d062bf1231d66d4cb588e58e
Merge: f6a00bf a8d442a
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Tue Feb 24 16:21:15 2015 -0800
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Tue Feb 24 16:21:15 2015 -0800

    Merge into master from pull request #248:
    speed up pre-checkin builds (https://github.com/floodlight/ivs/pull/248)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     98151CAB4899109D6F5C5EC
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

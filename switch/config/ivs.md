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
commit bd34b279535a80cb41ea13ae3134db3ef9373bfb
Merge: 16b7b28 d0a6fe4
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Wed Feb 25 16:58:30 2015 -0800
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Wed Feb 25 16:58:30 2015 -0800

    Merge into master from pull request #252:
    add userspace actions (https://github.com/floodlight/ivs/pull/252)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     98151CAB4899109D6F5C5EC
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

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
commit 0e3982a209784ed3b5f44acd020f5ee473c01ee8
Merge: 14ad9a5 1e034ec
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Thu Jan 22 15:46:15 2015 -0800
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Thu Jan 22 15:46:15 2015 -0800

    Merge into master from pull request #236:
    update submodules (https://github.com/floodlight/ivs/pull/236)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     9F2C3F79F744BDAA2DCF4F1
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

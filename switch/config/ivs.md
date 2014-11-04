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
commit 107107dff47dde003ab124849e3f3564a0da20f2
Merge: dfd8d13 64d64e0
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Tue Nov 4 12:09:39 2014 -0800
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Tue Nov 4 12:09:39 2014 -0800

    Merge into master from pull request #213:
    update submodules (https://github.com/floodlight/ivs/pull/213)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     38C4554629C53B68A04DA3C
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

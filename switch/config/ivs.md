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
commit 7101738160e2a7cafd88a160445f0df9428c2dc5
Merge: 5288ea9 012f327
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Mon Jan 5 15:50:37 2015 -0800
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Mon Jan 5 15:50:37 2015 -0800

    Merge into master from pull request #231:
    Use new OpenFlow message to upload Lua (https://github.com/floodlight/ivs/pull/231)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     7572C1DF4F2C8D11796B350
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

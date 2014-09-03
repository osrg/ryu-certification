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
commit 6e834f145a5474ed75449cea5abf451df4b2c8aa
Merge: 4758b6c bfe6258
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Tue Sep 2 16:04:41 2014 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Tue Sep 2 16:04:41 2014 -0700

    Merge into master from pull request #199:
    update submodules (https://github.com/floodlight/ivs/pull/199)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     7E680184B8D2F1B7A50D929
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

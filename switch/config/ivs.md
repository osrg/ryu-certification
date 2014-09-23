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
commit 4a0309e5537d7e0b1c808968a042ade66d231366
Merge: d274451 ba4d7b5
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Tue Sep 23 14:42:41 2014 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Tue Sep 23 14:42:41 2014 -0700

    Merge into master from pull request #204:
    OVSDriver: allow adding a port without specifying the port number (https://github.com/floodlight/ivs/pull/204)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     AF7EFB43C655F98538C721A
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

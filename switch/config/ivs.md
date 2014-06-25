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
commit 70d341721131b93f4462d4dc911fad2e89b1857b
Merge: 55bfd01 259636f
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Wed Jun 25 12:21:33 2014 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Wed Jun 25 12:21:33 2014 -0700

    Merge into master from pull request #177:
    fix assert for vlan range (https://github.com/floodlight/ivs/pull/177)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     7F26AE3DFE7C2EE35093306
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

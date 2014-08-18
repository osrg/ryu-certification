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
commit 4758b6c0b49321cb92edbf077d53023f7a0a0e95
Merge: 64ab62e 31d7d75
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Mon Aug 18 11:10:22 2014 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Mon Aug 18 11:10:22 2014 -0700

    Merge into master from pull request #197:
    Uplink configuration (https://github.com/floodlight/ivs/pull/197)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     C39D5F6EED28F169AB40D8C
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

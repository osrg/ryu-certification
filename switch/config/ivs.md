---
layout: default
title: Ryu Certification - ivs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ivs

# OpenFlow related configuration
<pre>
$ /usr/sbin/ivs --pipeline=standard-1.3 -c 10.24.150.30:6633 --dpid 0000000000000001 -i eth7 -i eth8
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 4655c7a4ef9e32105b99ad921debc180f7442f77
Merge: 8b245d4 9261c8c
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Mon Jun 16 14:45:34 2014 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Mon Jun 16 14:45:34 2014 -0700

    Merge into master from pull request #172:
    update submodules (https://github.com/floodlight/ivs/pull/172)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     5E11CF567A61626DAAFFCFD
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

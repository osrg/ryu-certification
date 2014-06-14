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
commit 8b245d481aee9fabf229e1c31a82f0736736d208
Merge: e04fc9a 5e3c721
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Fri Jun 13 15:58:21 2014 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Fri Jun 13 15:58:21 2014 -0700

    Merge into master from pull request #170:
    inital support for tcp_flags (https://github.com/floodlight/ivs/pull/170)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     5E11CF567A61626DAAFFCFD
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

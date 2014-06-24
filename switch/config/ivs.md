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
commit 55bfd015467598dfcc232111961380d5db22ecec
Merge: ad86bb6 46eaa22
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Tue Jun 24 12:55:41 2014 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Tue Jun 24 12:55:41 2014 -0700

    Merge into master from pull request #176:
    initial support for bsn_vlan_counter (https://github.com/floodlight/ivs/pull/176)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     A39B8CE5704BC7C8F2F6CC4
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

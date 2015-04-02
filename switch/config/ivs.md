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
commit 65db0163ae07ae6b18429623d8dbd4c612a1b59b
Merge: 58f5ead 9fd5596
Author:     Big Switch Networks &lt;abat@bigswitch.com&gt;
AuthorDate: Wed Apr 1 17:09:34 2015 -0700
Commit:     Big Switch Networks &lt;abat@bigswitch.com&gt;
CommitDate: Wed Apr 1 17:09:34 2015 -0700

    Merge pull request #290 from rlane/test-jenkins2

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     20B4C851BF1F0F70A9AED29
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

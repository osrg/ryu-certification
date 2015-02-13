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
commit 7e4cce8bcd7a244abb9c4d4ef4db79e689cfcf75
Merge: 1e966da f79ef7b
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Thu Feb 12 16:06:45 2015 -0800
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Thu Feb 12 16:06:45 2015 -0800

    Merge into master from pull request #243:
    set skb priority for packets sent through pipeline (https://github.com/floodlight/ivs/pull/243)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     D2CA8DBF1FEA4A00E76E211
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

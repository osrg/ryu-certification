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
commit 956c6ea169a92c4a697489c69c4931be6ce18da2
Merge: 995e52d ecae914
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Fri Aug 8 17:43:28 2014 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Fri Aug 8 17:43:28 2014 -0700

    Merge into master from pull request #196:
    translate set-queue actions to setting skb-&gt;priority (https://github.com/floodlight/ivs/pull/196)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     2A2304F830A3CC0306E112A
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

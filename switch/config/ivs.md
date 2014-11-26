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
commit da195a8a1a5234f58fc785b9a45832a0ece56fe9
Merge: 432e72b af199aa
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Wed Nov 26 12:13:27 2014 -0800
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Wed Nov 26 12:13:27 2014 -0800

    Merge into master from pull request #225:
    update submodules (https://github.com/floodlight/ivs/pull/225)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     411944BF6ECC8B656C8757E
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

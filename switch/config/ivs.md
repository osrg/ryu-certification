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
commit 87fbdca27bbe89095169ef257937003e1601eaf1
Merge: 3e847a5 292b974
Author:     Big Switch Networks &lt;abat@bigswitch.com&gt;
AuthorDate: Tue Oct 6 12:13:34 2015 -0700
Commit:     Big Switch Networks &lt;abat@bigswitch.com&gt;
CommitDate: Tue Oct 6 12:13:34 2015 -0700

    Merge pull request #346 from kenchiang/submodule-update

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.4.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     41F30D3DA215085A5793FD4
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

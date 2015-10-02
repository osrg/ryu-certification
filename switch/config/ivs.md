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
commit 3e847a58e356638214f528cbef8289546fa6c938
Merge: d01ea97 5c9af52
Author:     Big Switch Networks &lt;abat@bigswitch.com&gt;
AuthorDate: Thu Aug 27 14:25:22 2015 -0700
Commit:     Big Switch Networks &lt;abat@bigswitch.com&gt;
CommitDate: Thu Aug 27 14:25:22 2015 -0700

    Merge pull request #345 from harshsin/ipv6-tlv

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.4.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     41F30D3DA215085A5793FD4
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

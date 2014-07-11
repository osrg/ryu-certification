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
commit bcd1a2c73adf67919fc1a7a182f51d94c4feac16
Merge: af2daff d00fa66
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Fri Jul 11 01:17:22 2014 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Fri Jul 11 01:17:22 2014 -0700

    Merge into master from pull request #189:
    update submodules and put version in sw_desc (https://github.com/floodlight/ivs/pull/189)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     F59B363F4F274FB51AE1897
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

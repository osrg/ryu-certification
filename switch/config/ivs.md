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
commit d1cd93d17a760155e9d1fd3090125f3149007d07
Merge: 3145c4c cfb10fc
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Sat Feb 28 12:06:30 2015 -0800
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Sat Feb 28 12:06:30 2015 -0800

    Merge into master from pull request #255:
    update submodules (https://github.com/floodlight/ivs/pull/255)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     AD40B500DD5C28718A043A4
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

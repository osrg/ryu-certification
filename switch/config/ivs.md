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
commit d2744519693f607ee2b7db8325a2a80626482383
Merge: 0a0aed3 227fc47
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Fri Sep 12 19:21:22 2014 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Fri Sep 12 19:21:22 2014 -0700

    Merge into master from pull request #201:
    initial support for building ivs rpm for centos7 (https://github.com/floodlight/ivs/pull/201)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     0CE5EA9F2D9CD8557A23985
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

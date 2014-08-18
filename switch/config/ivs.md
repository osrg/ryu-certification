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
commit 64ab62ebfab821dcc2fd7b5c861f5c9a72b9d03d
Merge: 66006ff 86fa1af
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Fri Aug 15 16:40:56 2014 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Fri Aug 15 16:40:56 2014 -0700

    Merge into master from pull request #198:
    automerge: replace oneiric with trusty (https://github.com/floodlight/ivs/pull/198)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     9ED1E52A7CF430BDA936194
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

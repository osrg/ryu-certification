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
commit fe1922c50eedd4c43a386c0a6adf4e5621d217aa
Merge: b103725 4e0c2c8
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Wed Mar 11 16:02:29 2015 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Wed Mar 11 16:02:29 2015 -0700

    Merge into master from pull request #266:
    shared debug counters (https://github.com/floodlight/ivs/pull/266)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     AD40B500DD5C28718A043A4
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

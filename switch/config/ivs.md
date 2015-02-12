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
commit 1e966da17b7c229b4dacc6bdde4c386a869fbd82
Merge: 3d94a50 6b4c213
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Wed Feb 11 16:54:31 2015 -0800
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Wed Feb 11 16:54:31 2015 -0800

    Merge into master from pull request #242:
    update submodules (https://github.com/floodlight/ivs/pull/242)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     EEADF5DA85FA84BEF538FB2
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

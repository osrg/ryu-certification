---
layout: default
title: Ryu Certification - ivs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ivs

# OpenFlow related configuration
<pre>
$ /usr/sbin/ivs --pipeline=standard-1.3 -c 10.24.150.30:6633 --dpid 0000000000000001 -i eth7 -i eth8
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 5254f81d92afe1090f30fa4f1c30346be619cd23
Merge: e1eeaf3 7915658
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Wed Jan 22 18:31:35 2014 -0800
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Wed Jan 22 18:31:35 2014 -0800

    Merge into master from pull request #93:
    Implement pluggable forwarding pipelines (https://github.com/floodlight/ivs/pull/93)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.2.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     C83D2CF3E042AC2E747B936
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

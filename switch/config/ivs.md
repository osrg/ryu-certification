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
commit bc393e2666c5db56330ff40fd082878fe50fba2b
Merge: 82fd879 07602e2
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Fri Jun 13 13:35:14 2014 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Fri Jun 13 13:35:14 2014 -0700

    Merge into master from pull request #165:
    Move standard OpenFlow forwarding to pipeline_standard (https://github.com/floodlight/ivs/pull/165)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     5E11CF567A61626DAAFFCFD
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

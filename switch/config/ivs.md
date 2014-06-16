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
commit eff697d39771eca6c06cbc9298eef07f1af0f94d
Merge: 4655c7a 46b6021
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Mon Jun 16 15:28:37 2014 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Mon Jun 16 15:28:37 2014 -0700

    Merge into master from pull request #171:
    move CFR into pipeline_standard (https://github.com/floodlight/ivs/pull/171)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     5E11CF567A61626DAAFFCFD
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

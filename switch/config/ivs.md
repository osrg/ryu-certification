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
commit b1037258581ebf90fd136d8cd0eee7e30a2ac69a
Merge: 3edf731 4a89b39
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Tue Mar 10 15:53:36 2015 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Tue Mar 10 15:53:36 2015 -0700

    Merge into master from pull request #264:
    OVSDriver: add debug counters (https://github.com/floodlight/ivs/pull/264)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     AD40B500DD5C28718A043A4
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

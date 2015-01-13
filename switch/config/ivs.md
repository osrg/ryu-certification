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
commit 15bef2fffac15bf351ad0bea2e84d505d40eb57d
Merge: 7101738 1cfd4a0
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Mon Jan 12 17:42:36 2015 -0800
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Mon Jan 12 17:42:36 2015 -0800

    Merge into master from pull request #232:
    Implement of_bsn_lua_command_request message (https://github.com/floodlight/ivs/pull/232)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     EABBF9402BC3C42298A5444
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>

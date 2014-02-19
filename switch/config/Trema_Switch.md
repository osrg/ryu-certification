---
layout: default
title: Ryu Certification - Trema Switch - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* Trema Switch

# OpenFlow related configuration
<pre>
$ sudo -E ./objects/switch/switch/switch -d --datapath_id=1 --server_ip=10.24.100.30 --server_port=6633 --switch_ports=eth1,eth2
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit cc9ac33cc8f7cce2ad4d0eb76a3672650c19f7e7
Author:     SUGYO &lt;sugyo@pb.jp.nec.com&gt;
AuthorDate: Wed Feb 19 13:00:11 2014 +0900
Commit:     SUGYO &lt;sugyo@pb.jp.nec.com&gt;
CommitDate: Wed Feb 19 13:00:11 2014 +0900

    fix warnings
</pre>

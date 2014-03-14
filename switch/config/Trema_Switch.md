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
commit 54d40d7b74a5162b30ec102c9bc517c16abdec1f
Merge: 08caf91 4a759b1
Author:     SUGYO &lt;sugyo@pb.jp.nec.com&gt;
AuthorDate: Fri Mar 14 18:01:25 2014 +0900
Commit:     SUGYO &lt;sugyo@pb.jp.nec.com&gt;
CommitDate: Fri Mar 14 18:01:25 2014 +0900

    Merge branch 'develop' of github.com:trema/trema-edge into develop
</pre>

---
layout: default
title: Ryu Certification - Trema Switch - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* Trema Switch

# OpenFlow related configuration
<pre>
$ sudo -E ./objects/switch/switch/switch -d --datapath_id=1 --server_ip=10.24.150.30 --server_port=6633 --switch_ports=eth21,eth22,eth23
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit bdda57057921d41cf0e727cdbd0c5077e451622b
Author:     Kazuya Suzuki &lt;kazuya@ax.jp.nec.com&gt;
AuthorDate: Sat Aug 23 14:04:13 2014 +0900
Commit:     Kazuya Suzuki &lt;kazuya@ax.jp.nec.com&gt;
CommitDate: Sat Aug 23 14:04:13 2014 +0900

    Fix README in examples/packet_in.
</pre>

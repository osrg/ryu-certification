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
commit 148acb9cd7f654020098a5e769bfedad273a687b
Merge: f5221f7 9bee681
Author:     Yasuhito Takamiya &lt;yasuhito@gmail.com&gt;
AuthorDate: Fri Nov 28 14:23:20 2014 +0900
Commit:     Yasuhito Takamiya &lt;yasuhito@gmail.com&gt;
CommitDate: Fri Nov 28 14:23:20 2014 +0900

    Merge pull request #132 from trema/feature/fix52
    
    Fix errors when passing :data option to send_packet_out (refs #52).
</pre>

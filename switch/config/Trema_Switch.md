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
commit f5221f754a5340bbc98b4c740a36007b4035d8b4
Author:     Yasuhito Takamiya &lt;yasuhito@gmail.com&gt;
AuthorDate: Fri Nov 14 13:46:06 2014 +0900
Commit:     Yasuhito Takamiya &lt;yasuhito@gmail.com&gt;
CommitDate: Fri Nov 14 13:46:06 2014 +0900

    More RuboCop.
</pre>

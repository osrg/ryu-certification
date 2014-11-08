---
layout: default
title: Ryu Certification - ofsoftswitch13 - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ofsoftswitch13

# OpenFlow related configuration
<pre>
$ /usr/local/bin/ofdatapath --datapath-id=000000000002 --interface=eth21,eth22,eth23 ptcp:3333
$ /usr/local/bin/ofprotocol tcp:127.0.0.1:3333 tcp:10.24.150.30:6633
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 01e5dd04022331615803cd49da00466a9398dce0
Merge: c532c31 5e5774d
Author:     Eder Leão Fernandes &lt;ederleaofernandes@gmail.com&gt;
AuthorDate: Sat Nov 8 15:37:08 2014 -0200
Commit:     Eder Leão Fernandes &lt;ederleaofernandes@gmail.com&gt;
CommitDate: Sat Nov 8 15:37:08 2014 -0200

    Merge pull request #129 from hdnivara/master
    
    128: Hex metadata is being displayed in decimal in flow statistics
</pre>

# Modified test scenario for switch restrictions
<pre>
$ rm ryu/tests/switch/of13/action/25_SET_FIELD/10_IP_PROTO_IPv6.json
</pre>

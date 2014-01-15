---
layout: default
title: Ryu Certification - ofsoftswitch13 - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ofsoftswitch13

# OpenFlow related configuration
<pre>
$ /usr/local/bin/ofdatapath --datapath-id=000000000002 --interface=eth1,eth2 ptcp:3333
$ /usr/local/bin/ofprotocol tcp:127.0.0.1:3333 tcp:10.24.100.30:6633
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 78a676f723c8d1ad543ffb9ddcb8bda0d36d9064
Merge: dcdefff 4a4e89a
Author:     Eder Leão Fernandes &lt;ederlf@cpqd.com.br&gt;
AuthorDate: Wed Jan 15 09:37:24 2014 -0800
Commit:     Eder Leão Fernandes &lt;ederlf@cpqd.com.br&gt;
CommitDate: Wed Jan 15 09:37:24 2014 -0800

    Merge pull request #82 from cloudysunny14/myFix2
    
    Fix caluculate inccorect checksum when Action Set-Field DSCP value and r...
</pre>

# Modified test scenario for switch restrictions
<pre>
$ rm ryu/tests/switch/of13/action/25_SET_FIELD/10_IP_PROTO_IPv6.json
</pre>

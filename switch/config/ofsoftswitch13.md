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
commit dcdefff896a22ecd6912acc17effb2a82cecee5f
Merge: 5e725fd fccc658
Author:     Eder Leão Fernandes &lt;ederlf@cpqd.com.br&gt;
AuthorDate: Thu Jan 9 09:00:22 2014 -0800
Commit:     Eder Leão Fernandes &lt;ederlf@cpqd.com.br&gt;
CommitDate: Thu Jan 9 09:00:22 2014 -0800

    Merge pull request #79 from codeshredder/master
    
    some bugs
</pre>

# Modified test scenario for switch restrictions
<pre>
$ rm ryu/tests/switch/of13/action/25_SET_FIELD/10_IP_PROTO_IPv6.json
</pre>

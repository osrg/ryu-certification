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
commit cea85b731e319feddf2744c59b9bacd996d4c2eb
Author:     ederlf &lt;ederlf@cpqd.com.br&gt;
AuthorDate: Tue Feb 18 17:23:40 2014 -0300
Commit:     ederlf &lt;ederlf@cpqd.com.br&gt;
CommitDate: Tue Feb 18 17:23:40 2014 -0300

    Correct mask to print MPLS BOS match field
</pre>

# Modified test scenario for switch restrictions
<pre>
$ rm ryu/tests/switch/of13/action/25_SET_FIELD/10_IP_PROTO_IPv6.json
</pre>

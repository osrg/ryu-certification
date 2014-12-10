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
commit 01baa960fdda19a1bf8701f508a501d1cf133f44
Author:     Eder Leão Fernandes &lt;ederleaofernandes@gmail.com&gt;
AuthorDate: Tue Dec 9 23:38:55 2014 -0200
Commit:     Eder Leão Fernandes &lt;ederleaofernandes@gmail.com&gt;
CommitDate: Tue Dec 9 23:38:55 2014 -0200

    Add tcp and udp checksum recalculation after ipv6 src and dst set_field.
    
    The addition fix wrong checksum error after a set_field action with
    ipv6 src or ipv6 dst.
</pre>

# Modified test scenario for switch restrictions
<pre>
$ rm ryu/tests/switch/of13/action/25_SET_FIELD/10_IP_PROTO_IPv6.json
</pre>

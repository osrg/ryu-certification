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
commit 41cb72dbbd40dd5418177bea22fea3d2f8802e09
Author:     Eder Leão Fernandes &lt;ederleaofernandes@gmail.com&gt;
AuthorDate: Tue May 19 21:02:02 2015 -0300
Commit:     Eder Leão Fernandes &lt;ederleaofernandes@gmail.com&gt;
CommitDate: Tue May 19 21:12:58 2015 -0300

    Fix segmentation fault when handling packets larger than MTU.
    
    This commit fixes the switch segmenation fault when packets
    larger than the interface MTU are received.
    
    The problem is caused mainly due to TCP segmentation offload, which
    enables the TCP stack to send an entire chunk of data to be break up by
    the network interface.
    
    While the switch does not break anymore, it still does not handle TSO,
    so larger packets might be dropped when sent to the switch causing
    loss of performance. For this reason is still recommended to disable
    TSO support on the interface.
</pre>

# Modified test scenario for switch restrictions
<pre>
$ rm ryu/tests/switch/of13/action/25_SET_FIELD/10_IP_PROTO_IPv6.json
</pre>

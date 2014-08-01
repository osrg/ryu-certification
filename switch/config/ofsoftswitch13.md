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
commit a54476ec91e929051c2a3789c8beb43264a0dfae
Author:     ederlf &lt;ederlf@cpqd.com.br&gt;
AuthorDate: Tue Jul 29 23:18:05 2014 -0300
Commit:     ederlf &lt;ederlf@cpqd.com.br&gt;
CommitDate: Tue Jul 29 23:18:05 2014 -0300

    Fix lots of ugly warnings
</pre>

# Modified test scenario for switch restrictions
<pre>
$ rm ryu/tests/switch/of13/action/25_SET_FIELD/10_IP_PROTO_IPv6.json
</pre>

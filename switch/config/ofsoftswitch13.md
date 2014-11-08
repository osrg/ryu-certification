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
commit c532c3167523564d4ea9f9754628900a0e96000f
Author:     Jean Tourrilhes &lt;jean.tourrilhes@hp.com&gt;
AuthorDate: Mon Oct 20 11:45:59 2014 -0700
Commit:     ederlf &lt;ederlf@cpqd.com.br&gt;
CommitDate: Sat Nov 8 12:47:30 2014 -0200

    Add simple validations to table feature request.
</pre>

# Modified test scenario for switch restrictions
<pre>
$ rm ryu/tests/switch/of13/action/25_SET_FIELD/10_IP_PROTO_IPv6.json
</pre>

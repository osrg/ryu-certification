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
commit b8e6a5592ce9d1dfb6dcab5168b8e159fc436828
Author:     Jean Tourrilhes &lt;jean.tourrilhes@hp.com&gt;
AuthorDate: Wed Feb 20 18:10:12 2013 -0800
Commit:     ederlf &lt;ederlf@cpqd.com.br&gt;
CommitDate: Mon Jul 7 23:57:02 2014 -0300

    EXT-258: Implement port liveness, as clarified by EXT-258
</pre>

# Modified test scenario for switch restrictions
<pre>
$ rm ryu/tests/switch/of13/action/25_SET_FIELD/10_IP_PROTO_IPv6.json
</pre>

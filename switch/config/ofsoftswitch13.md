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
commit f8cc42f8837ec287c8975fe56a595687d76e6faa
Author:     Eder Leão Fernandes &lt;ederlf@cpqd.com.br&gt;
AuthorDate: Fri Apr 25 08:23:15 2014 -0300
Commit:     Eder Leão Fernandes &lt;ederlf@cpqd.com.br&gt;
CommitDate: Fri Apr 25 08:23:15 2014 -0300

    Change Netbee version to the most recent
    
    The most recent Netbee version should fix the compilation issues on most recent Ubuntu versions.
</pre>

# Modified test scenario for switch restrictions
<pre>
$ rm ryu/tests/switch/of13/action/25_SET_FIELD/10_IP_PROTO_IPv6.json
</pre>

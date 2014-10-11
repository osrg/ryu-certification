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
commit 227ecaa4fb1319c9e3eff63abea9e2413f96f368
Author:     oftutorial &lt;ederleaofernandes@gmail.com&gt;
AuthorDate: Sat Oct 11 01:33:08 2014 -0300
Commit:     oftutorial &lt;ederleaofernandes@gmail.com&gt;
CommitDate: Sat Oct 11 01:33:08 2014 -0300

    Change IPv6 flow label and traffic class parsing.
    
    This commit changes the parsing specification of the fields:
    version, traffic class and flow label. Now they are parsed as
    only one field on customnetpdl.
</pre>

# Modified test scenario for switch restrictions
<pre>
$ rm ryu/tests/switch/of13/action/25_SET_FIELD/10_IP_PROTO_IPv6.json
</pre>

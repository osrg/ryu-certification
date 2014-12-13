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
commit 80ceb15b70fc7eeedb25380a2815c7b69bdb6b06
Author:     Eder Leão Fernandes &lt;ederleaofernandes@gmail.com&gt;
AuthorDate: Sat Dec 13 00:17:27 2014 -0200
Commit:     Eder Leão Fernandes &lt;ederleaofernandes@gmail.com&gt;
CommitDate: Sat Dec 13 00:20:45 2014 -0200

    Fix IPv6 neighbor discovery target pre requisites check.
    
    The check for icmp type was not working because of
    the order of insertion on the flow mod message parsing.
    
    Also it fixes the set_field action, calculating the
    checksum after change the neighbor discovery target field.
    
    This commit also removes unecessary debugging printf.
</pre>

# Modified test scenario for switch restrictions
<pre>
$ rm ryu/tests/switch/of13/action/25_SET_FIELD/10_IP_PROTO_IPv6.json
</pre>

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
commit c31d2a1c84dbb690aca4c99fdd7222fde712fba5
Author:     Eder Leão Fernandes &lt;ederleaofernandes@gmail.com&gt;
AuthorDate: Wed Mar 25 21:40:24 2015 -0300
Commit:     Eder Leão Fernandes &lt;ederleaofernandes@gmail.com&gt;
CommitDate: Wed Mar 25 21:40:24 2015 -0300

    Fix strict masked ip matching.
    
    Quick and dirty hack to stop different IP addresses, with equal masks,
    to match.
    The problem is caused because we work with IP addresses in the network
    byte order format and the function strict_match32 performs matching
    on values in the host byte order. Thus, in little endian machines,
    the function will not work.
    Problems like this show  that the match needs a
    huge refactoring.
</pre>

# Modified test scenario for switch restrictions
<pre>
$ rm ryu/tests/switch/of13/action/25_SET_FIELD/10_IP_PROTO_IPv6.json
</pre>

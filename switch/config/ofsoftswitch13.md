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
commit 8089471f75eb94bcbfcc6885d521e1407bddf661
Author:     Chris Kappler &lt;chrisk@mysticlabs.com&gt;
AuthorDate: Fri Apr 11 05:37:24 2014 -0700
Commit:     Eder Leão Fernandes &lt;ederleaofernandes@gmail.com&gt;
CommitDate: Thu May 21 18:18:04 2015 -0300

    Fixed masking logic for:
      masked ip range forwarding
      masked rule overlap detection
      masked rule overwrite detection
</pre>

# Modified test scenario for switch restrictions
<pre>
$ rm ryu/tests/switch/of13/action/25_SET_FIELD/10_IP_PROTO_IPv6.json
</pre>

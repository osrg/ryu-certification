---
layout: default
title: Netronome_NFPP-1U-AC-1001 - config
---

# OpenFlow related configuration
<pre>
$ cat /etc/netronome.conf
SDN_CONTROLLER=10.24.150.30
SDN_CONTROLLER_PORT=6633
SDN_DPID=0000000000000032
SDN_FIELDS=all
SDN_IPV6=y
SDN_FLOW_SNAPSHOT=/home/ruikubo/flow_snapshot.txt
SDN_MAX_BACKOFF=5000
SDN_INACTIVITY_PROBE=5000
SDN_SWITCH=10.24.32.1
SDN_OFCONFIG_USER=username
SDN_OFCONFIG_PORT=11111
</pre>

# Version information
<pre>
$ uname -a
Linux netronome 3.5.0-44-generic #67~precise1-Ubuntu SMP Wed Nov 13 16:16:57 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
$ sudo /opt/netronome/bin/ns-sdn version
Netronome SDN version 1.0-r2705:957b19f529f5.326:547b9cca7a97
</pre>


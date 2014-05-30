---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
3b01ba9e-ab0b-4aed-b9a8-b6a9a452a47a
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 58ff4298-082d-4e9a-8774-a4d0a68a5fc7
controller          : [5a902882-1cc4-46a1-bbd8-67330da21ade]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [a5d41d03-85d6-438a-9540-a905c4224f6d, c2193a90-c305-49d5-a06e-a9bc31e03da6, d23a9faa-19a8-422b-8dcf-e5ef79503b96, ffa5ace9-c085-4c0b-8f7d-4d88af7d027a]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 5a902882-1cc4-46a1-bbd8-67330da21ade
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=1002, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : c2193a90-c305-49d5-a06e-a9bc31e03da6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0fa72cf7-3099-4e08-9a16-59059f329658]
name                : eth22

_uuid               : ffa5ace9-c085-4c0b-8f7d-4d88af7d027a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a17583f1-8f79-47b4-9ef7-654c10b4d1dc]
name                : eth23

_uuid               : d23a9faa-19a8-422b-8dcf-e5ef79503b96
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f6d5c995-8e6d-4bb1-bab3-96b0245b9534]
name                : br0

_uuid               : a5d41d03-85d6-438a-9540-a905c4224f6d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [58f26fed-cac2-4802-a3bb-ba808240d79c]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 58f26fed-cac2-4802-a3bb-ba808240d79c
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=814545905, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=6310870, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : a17583f1-8f79-47b4-9ef7-654c10b4d1dc
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1550
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2763450704, tx_dropped=0, tx_errors=0, tx_packets=4705612}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : f6d5c995-8e6d-4bb1-bab3-96b0245b9534
admin_state         : down
duplex              : full
ifindex             : 308
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : 0fa72cf7-3099-4e08-9a16-59059f329658
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1550
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3708146344, tx_dropped=0, tx_errors=0, tx_packets=2486647}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 1481a7551da6893c08fb93bee9ac8293b90aa6a6
Author:     Ansis Atteka &lt;aatteka@nicira.com&gt;
AuthorDate: Fri May 23 14:15:28 2014 -0700
Commit:     Ansis Atteka &lt;aatteka@nicira.com&gt;
CommitDate: Fri May 30 10:06:10 2014 -0700

    process: block signals while spawning child processes
    
    Between fork&#40;&#41; and execvp&#40;&#41; calls in the process_start&#40;&#41;
    function both child and parent processes share the same
    file descriptors.  This means that, if a child process
    received a signal during this time interval, then it could
    potentially write data to a shared file descriptor.
    
    One such example is fatal signal handler, where, if
    child process received SIGTERM signal, then it would
    write data into pipe.  Then a read event would occur
    on the other end of the pipe where parent process is
    listening and this would make parent process to incorrectly
    believe that it was the one who received SIGTERM.
    Also, since parent process never reads data from this
    pipe, then this bug would make parent process to consume
    100% CPU by immediately waking up from the event loop.
    
    This patch will help to avoid this problem by blocking
    signals until child closes all its file descriptors.
    
    Signed-off-by: Ansis Atteka &lt;aatteka@nicira.com&gt;
    Reported-by: Suganya Ramachandran &lt;suganyar@vmware.com&gt;
    Issue: 1255110
</pre>

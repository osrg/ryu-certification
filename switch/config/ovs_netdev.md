---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
e8fef6bc-bbe9-43ce-9723-e7f88ad95aca
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : df66716b-5565-4003-b886-15694051ef24
controller          : [6b8be7d0-4d67-43d5-a9f9-9c1711b0f1f6]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [5b9160f5-d403-4afc-9e29-bc877d9eb179, 61abdb8b-2079-4197-b787-43bcfd11107f, 7e475d8b-57e6-4b3c-940a-9a16f900973b, e2f5380e-cd6b-45a9-947e-fbffe7d2f408]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 6b8be7d0-4d67-43d5-a9f9-9c1711b0f1f6
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=561, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 5b9160f5-d403-4afc-9e29-bc877d9eb179
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [99b290bd-3f7e-4a37-bf29-9ce56772a0b8]
name                : br0

_uuid               : e2f5380e-cd6b-45a9-947e-fbffe7d2f408
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [db6a88b7-a172-476f-8f63-5dc4ddcc9709]
name                : eth23

_uuid               : 7e475d8b-57e6-4b3c-940a-9a16f900973b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b8cfd09b-40fc-4b48-b3f3-4d777e668d79]
name                : eth22

_uuid               : 61abdb8b-2079-4197-b787-43bcfd11107f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d157ca31-d16a-4f30-a7f5-2969f07d4b96]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 99b290bd-3f7e-4a37-bf29-9ce56772a0b8
admin_state         : down
duplex              : full
ifindex             : 101
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

_uuid               : d157ca31-d16a-4f30-a7f5-2969f07d4b96
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
statistics          : {collisions=0, rx_bytes=2758127005, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=1846832, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : db6a88b7-a172-476f-8f63-5dc4ddcc9709
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1895559000, tx_dropped=0, tx_errors=0, tx_packets=1263706}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : b8cfd09b-40fc-4b48-b3f3-4d777e668d79
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1119421862, tx_dropped=0, tx_errors=0, tx_packets=749351}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 7a6cf343a410d77e05ebd7bf5b5ade52803879ae
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Tue May 20 14:16:54 2014 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Tue May 20 15:59:45 2014 -0700

    ovs-ctl: Raise the limit on the number of open file descriptors.
    
    Since the removal of dispatcher thread, OVS creates 'n-handler-threads'
    file descriptors for each bridge port.  To allow more bridge ports
    be supported, this commit raises the limit on the number of open file
    descriptors from 7500 to 65535.
    
    Bug #1254038.
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
</pre>

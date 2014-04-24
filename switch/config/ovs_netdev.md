---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
308bca70-2930-43a0-96c4-39dd26ef8c52
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 259ee460-ca92-4a46-9f9f-a76cb2ab1826
controller          : [b83cb47b-d38c-4c7c-b34f-f28e868cb38f]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [183246e6-a33b-4a85-bb27-25a1b075915d, 77acd78a-8189-4e7a-806b-f30c1bc74edb, 86429e3b-f69f-4721-b686-be598a2b243d, cdf6efe1-5894-49cc-a92a-f70b91d82ab3]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : b83cb47b-d38c-4c7c-b34f-f28e868cb38f
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=577, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : cdf6efe1-5894-49cc-a92a-f70b91d82ab3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [36d76409-1dd9-42fc-ba3e-1089a9854468]
name                : eth23

_uuid               : 183246e6-a33b-4a85-bb27-25a1b075915d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [12a68e0d-d5ef-43fd-ae27-100a2d0a0f39]
name                : br0

_uuid               : 77acd78a-8189-4e7a-806b-f30c1bc74edb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d24e5cb8-a43e-43a8-9919-570195a42522]
name                : eth22

_uuid               : 86429e3b-f69f-4721-b686-be598a2b243d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8735c39e-c3a3-456c-b419-b0b18bb421b1]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : d24e5cb8-a43e-43a8-9919-570195a42522
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1500
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1535732298, tx_dropped=0, tx_errors=0, tx_packets=1029862}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 12a68e0d-d5ef-43fd-ae27-100a2d0a0f39
admin_state         : down
duplex              : full
ifindex             : 1121
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

_uuid               : 36d76409-1dd9-42fc-ba3e-1089a9854468
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1500
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1293510000, tx_dropped=0, tx_errors=0, tx_packets=862340}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 8735c39e-c3a3-456c-b419-b0b18bb421b1
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=2557038787, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=1719439, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 73a3c4757e596ff156d40f41496a0264373e5bc4
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Wed Apr 23 15:31:17 2014 +1200
Commit:     Joe Stringer &lt;joestringer@nicira.com&gt;
CommitDate: Thu Apr 24 11:57:49 2014 +1200

    revalidator: Prevent handling the same flow twice.
    
    When the datapath flow table is modified while a flow dump operation is
    in progress, it is possible for the same flow to be dumped twice. In
    such cases, revalidators may perform redundant work, or attempt to
    delete the same flow twice.
    
    This was causing intermittent testsuite failures for test #670 -
    &quot;ofproto-dpif, active-backup bonding&quot; where a flow &#40;that had not
    previously been dumped&#41; was dumped, revalidated and deleted twice.
    
    The logs show errors such as:
    &quot;failed to flow_get &#40;No such file or directory&#41; skb_priority&#40;0&#41;,...&quot;
    &quot;failed to flow_del &#40;No such file or directory&#41; skb_priority&#40;0&#41;,...&quot;
    
    This patch adds a 'flow_exists' field to 'struct udpif_key' to track
    whether the flow is &#40;in progress&#41; to be deleted. After doing a ukey
    lookup, we check whether ukey-&gt;mark or ukey-&gt;flow indicates that the
    flow has already been handled. If it has already been handled, we skip
    handling the flow again.
    
    We also defer ukey cleanup for flows that fail revalidation, so that the
    ukey will still exist if the same flow is dumped twice. This allows the
    above logic to work in this case.
    
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Acked-by: Alex Wang &lt;alexw@nicira.com&gt;
</pre>

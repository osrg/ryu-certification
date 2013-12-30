---
layout: default
title: ovs_netdev - config
---

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
1a773690-34df-4af1-9b19-b866860e0fd2
    Bridge "br0"
        Controller "tcp:10.24.150.30"
        fail_mode: secure
        Port "eth7"
            Interface "eth7"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth8"
            Interface "eth8"

$ sudo ovs-vsctl list Bridge
_uuid               : 58d83675-42ac-45fb-baea-a820107aedf3
controller          : [1bf0ee2d-4b22-4774-a42e-7f382f6a7997]
datapath_id         : "0000000000000001"
datapath_type       : netdev
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [19989046-2ba5-47fa-a071-0c4b54795732, cc13429b-c799-4b06-a0c9-5d5666865c42, ebe8d8e7-ed9b-4513-815f-71a1df4766a3]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : 1bf0ee2d-4b22-4774-a42e-7f382f6a7997
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="297", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : 19989046-2ba5-47fa-a071-0c4b54795732
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [61039c06-879e-4d9c-9e62-bb8dcd91d0e3]
name                : "eth7"

_uuid               : ebe8d8e7-ed9b-4513-815f-71a1df4766a3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [667a1cb4-bf13-4c54-85b2-f291b5d6cc84]
name                : "eth8"

_uuid               : cc13429b-c799-4b06-a0c9-5d5666865c42
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5ebd8804-9c1a-4bc5-aafc-5e37c7f9c416]
name                : "br0"

$ sudo ovs-vsctl list Interface
_uuid               : 667a1cb4-bf13-4c54-85b2-f291b5d6cc84
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:ec"
mtu                 : 1550
name                : "eth8"
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=213760, tx_dropped=0, tx_errors=0, tx_packets=2310}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : 5ebd8804-9c1a-4bc5-aafc-5e37c7f9c416
admin_state         : up
duplex              : full
ifindex             : 49
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
mtu                 : 1500
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version="1.6", firmware_version="N/A"}
type                : internal

_uuid               : 61039c06-879e-4d9c-9e62-bb8dcd91d0e3
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
mtu                 : 1550
name                : "eth7"
ofport              : 1
statistics          : {collisions=0, rx_bytes=548215, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=5630, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 0cf3b0d0fd97c52822979fe7cf1e594be03324a9
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Fri Dec 20 15:12:58 2013 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon Dec 30 13:45:33 2013 -0800

    ofproto-dpif-monitor: Remove monitor_init().
    
    Commit 881d47a9fa9 (monitor: Replace monitor_seq with periodic
    wakeup.) removes the global "struct seq" in ofproto-dpif-monitor
    module.  This change makes the monitor_init() no longer needed.
    
    This commit removes the monitor_init() from ofproto-dpif-monitor.c.
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>

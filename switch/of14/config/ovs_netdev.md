---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
8474ec64-3e71-4db2-8ac0-56a3f4ba03e1
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 62da65b5-5a7a-4f77-852f-9615fe391716
controller          : [8962d6aa-3038-4f8b-9504-87ef556bd1c9]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [19634b3c-41f1-4254-9fae-e129edcdd46e, 40bd9a16-7ea7-47e3-8538-a9067a040882, 702baf3e-bf2a-4e70-9b51-d08b00b5e0c5, bd4d2ef9-3e90-459e-a4de-c5d0c46bf461]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 8962d6aa-3038-4f8b-9504-87ef556bd1c9
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="652", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 19634b3c-41f1-4254-9fae-e129edcdd46e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [14ae5df6-9969-4b73-af03-c5a9831edfc2]
name                : "eth22"

_uuid               : bd4d2ef9-3e90-459e-a4de-c5d0c46bf461
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0052616a-9b5e-4510-8912-4e613ff955b9]
name                : "eth23"

_uuid               : 702baf3e-bf2a-4e70-9b51-d08b00b5e0c5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [92d07657-184d-4b82-bd0b-27b4bc9e0668]
name                : "br0"

_uuid               : 40bd9a16-7ea7-47e3-8538-a9067a040882
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [47ecfc17-dc8f-48dc-8ea2-9b699064463d]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 0052616a-9b5e-4510-8912-4e613ff955b9
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5e"
mtu                 : 1550
name                : "eth23"
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=572988000, tx_dropped=0, tx_errors=0, tx_packets=381992}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 14ae5df6-9969-4b73-af03-c5a9831edfc2
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5d"
mtu                 : 1550
name                : "eth22"
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=9780281978, tx_dropped=0, tx_errors=0, tx_packets=6522465}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 92d07657-184d-4b82-bd0b-27b4bc9e0668
admin_state         : down
duplex              : full
ifindex             : 39
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1500
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version="1.6", firmware_version="N/A"}
type                : internal

_uuid               : 47ecfc17-dc8f-48dc-8ea2-9b699064463d
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1550
name                : "eth21"
ofport              : 1
statistics          : {collisions=0, rx_bytes=12045590096, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=8035651, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit c875bb948df059855c18b29bdfbfbfcb986e607a
Author:     Ethan Jackson &lt;ethan@nicira.com&gt;
AuthorDate: Thu Mar 26 12:52:42 2015 -0700
Commit:     Ethan Jackson &lt;ethan@nicira.com&gt;
CommitDate: Fri May 8 15:26:26 2015 -0700

    utilities: Add new pipeline generator script.
    
    When doing OVS performance testing, it's important to have both
    realistic traffic traces and OpenFlow pipelines on which to evaluate
    prospective changes.  As a first step in this direction, this patch
    adds a python script which generates an OpenFlow pipeline intended to
    simulate typical network virtualization workloads.
    
    Signed-off-by: Ethan Jackson &lt;ethan@nicira.com&gt;
    Acked-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
</pre>

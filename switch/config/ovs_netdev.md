---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
2e356d54-8365-43f0-9664-8abcc7930fd4
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 488e5fff-898f-41e9-a59c-d376ffe09847
controller          : [3ac3ca13-2f7d-4122-8695-5bd546d15c07]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [16055441-86f2-4779-afff-67f71e3acd24, 4555b856-a0b7-4938-9c53-a7a0cfda4109, bac94fa6-762d-4ac8-a34d-3cd30ab16971, c16c6d25-392a-47cb-98ba-a7e0c942b9ac]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 3ac3ca13-2f7d-4122-8695-5bd546d15c07
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="657", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 16055441-86f2-4779-afff-67f71e3acd24
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4f7e49b2-84aa-4310-9982-065402420872]
name                : "eth23"

_uuid               : c16c6d25-392a-47cb-98ba-a7e0c942b9ac
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [382bb41c-6991-47cb-9320-7a24d0a64a2c]
name                : "eth21"

_uuid               : 4555b856-a0b7-4938-9c53-a7a0cfda4109
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [54e6eb1d-81a6-4ac7-9bf8-beb89584397f]
name                : "eth22"

_uuid               : bac94fa6-762d-4ac8-a34d-3cd30ab16971
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e2cb0cb7-fedc-4c04-aa9c-09677def76f2]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 382bb41c-6991-47cb-9320-7a24d0a64a2c
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
statistics          : {collisions=0, rx_bytes=11928574271, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=7956998, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 54e6eb1d-81a6-4ac7-9bf8-beb89584397f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=9727656201, tx_dropped=0, tx_errors=0, tx_packets=6487077}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 4f7e49b2-84aa-4310-9982-065402420872
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=485235000, tx_dropped=0, tx_errors=0, tx_packets=323490}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : e2cb0cb7-fedc-4c04-aa9c-09677def76f2
admin_state         : down
duplex              : full
ifindex             : 37
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

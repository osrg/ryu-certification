---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
c5037d9d-dbe7-47b8-a7ad-a65450cb0f84
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
_uuid               : 7b99cba1-5069-444c-95c0-48fc27718af1
controller          : [0fc92cac-e908-4b4c-985f-803c08326b48]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [176045db-5144-4898-a2a0-26a700c2f0d6, 930c4a37-4e7b-4ad7-bd99-97d5fcd3ddc0, b1139747-5166-4c66-8b14-908f523559c5, d5afcb00-d481-48c1-8860-d7b80cc56db7]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 0fc92cac-e908-4b4c-985f-803c08326b48
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="12", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : d5afcb00-d481-48c1-8860-d7b80cc56db7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ce2134fe-ab3c-480b-a838-5de52678a538]
name                : "eth23"

_uuid               : 176045db-5144-4898-a2a0-26a700c2f0d6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c0b6f50c-14ee-49e3-b636-364b6c0e2043]
name                : "eth22"

_uuid               : b1139747-5166-4c66-8b14-908f523559c5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ee2c0bfd-4edf-49e3-ae90-d5a1cbf616b9]
name                : "br0"

_uuid               : 930c4a37-4e7b-4ad7-bd99-97d5fcd3ddc0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [add398c2-9943-432f-9320-2d032beaa679]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : c0b6f50c-14ee-49e3-b636-364b6c0e2043
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31753041581, tx_dropped=0, tx_errors=0, tx_packets=21205989}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : ee2c0bfd-4edf-49e3-ae90-d5a1cbf616b9
admin_state         : down
duplex              : full
ifindex             : 866
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

_uuid               : add398c2-9943-432f-9320-2d032beaa679
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
statistics          : {collisions=0, rx_bytes=47895750471, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=32011138, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : ce2134fe-ab3c-480b-a838-5de52678a538
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=10590709500, tx_dropped=0, tx_errors=0, tx_packets=7060473}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 79b4e6dc489fa4c082f8e056bee30a28129f61fc
Author:     Russell Bryant &lt;russell@ovn.org&gt;
AuthorDate: Mon Mar 7 10:47:21 2016 -0500
Commit:     Russell Bryant &lt;russell@ovn.org&gt;
CommitDate: Mon Mar 7 14:12:20 2016 -0500

    ovs-sandbox: Add note about OVN to initial output.
    
    When you run ovs-sandbox, it finishes with a note describing the dummy
    environment it has set up.  Add some additional text that indicates that
    OVN is also enabled when that is the case.
    
    Signed-off-by: Russell Bryant &lt;russell@ovn.org&gt;
    Acked-by: Ben Pfaff &lt;blp@ovn.org&gt;
    Acked-by: Ryan Moats &lt;rmoats@us.ibm.com&gt;
</pre>

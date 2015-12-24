---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
c89bfdb3-7db2-4f2b-bfb0-d69ad7a9c714
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 700bd7ce-92c0-43c7-ae01-c993a0b8f71e
controller          : [a15ac325-afe6-4d3f-8855-a4c517e83c7e]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [02029447-aa8c-4a82-8b02-51ea621f5d02, 67a25ea5-630a-49bf-a420-eecdb370ada6, 9f6b90f2-e5c2-4e0b-94bc-1fd7589c85e9, a53dd3ec-0d62-4ddd-868e-2ea954f97c89]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a15ac325-afe6-4d3f-8855-a4c517e83c7e
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="662", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : a53dd3ec-0d62-4ddd-868e-2ea954f97c89
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ce6820ff-9f85-426a-950b-e7c3884900f7]
name                : "eth21"

_uuid               : 67a25ea5-630a-49bf-a420-eecdb370ada6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2aea3eb0-44b4-45c9-9688-e2e446d6531d]
name                : "eth22"

_uuid               : 9f6b90f2-e5c2-4e0b-94bc-1fd7589c85e9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [151a2717-9af3-40d5-b718-882313f578be]
name                : "eth23"

_uuid               : 02029447-aa8c-4a82-8b02-51ea621f5d02
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ea302b21-73ab-490a-8234-708ee7b5fb2a]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 2aea3eb0-44b4-45c9-9688-e2e446d6531d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=29751154027, tx_dropped=0, tx_errors=0, tx_packets=19859209}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : ea302b21-73ab-490a-8234-708ee7b5fb2a
admin_state         : down
duplex              : full
ifindex             : 714
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

_uuid               : 151a2717-9af3-40d5-b718-882313f578be
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7258366500, tx_dropped=0, tx_errors=0, tx_packets=4838911}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : ce6820ff-9f85-426a-950b-e7c3884900f7
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
statistics          : {collisions=0, rx_bytes=43449123613, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=29021726, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit cefc655f3ed508becf18b5abcc4225262218e1cd
Author:     Ben Pfaff &lt;blp@ovn.org&gt;
AuthorDate: Wed Dec 23 14:24:32 2015 -0800
Commit:     Ben Pfaff &lt;blp@ovn.org&gt;
CommitDate: Wed Dec 23 14:28:51 2015 -0800

    Makefile.am: Fix Automake warning.
    
    The warning is as follows:
    
      Makefile.am:363: warning: .PHONY was already defined in condition TRUE,
        which includes condition VSTUDIO_DDK ...
      Makefile.am:200: ... '.PHONY' previously defined here
    
    Signed-off-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>

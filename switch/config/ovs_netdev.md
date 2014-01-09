---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
5d3d8cff-1939-47cc-8e48-5fb64cd26ea1
    Bridge "br0"
        Controller "tcp:10.24.150.30"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth8"
            Interface "eth8"
        Port "eth7"
            Interface "eth7"

$ sudo ovs-vsctl list Bridge
_uuid               : 0d40f3b4-e504-40aa-baaa-a4275e9fa8b3
controller          : [85c53f02-538a-4c54-aaae-61738b2bc6a0]
datapath_id         : "0000000000000001"
datapath_type       : netdev
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [12289f44-e3f6-4e29-8c2c-992c7565f108, 68574580-8174-4d9c-8981-30051d5d2b8d, a162acb5-cec8-44f0-b6df-9ede29746b05]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : 85c53f02-538a-4c54-aaae-61738b2bc6a0
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="296", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : 68574580-8174-4d9c-8981-30051d5d2b8d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0766286b-f835-4ff1-94b5-fe0b717dc402]
name                : "eth8"

_uuid               : 12289f44-e3f6-4e29-8c2c-992c7565f108
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2f4f9647-d03b-4f31-8bae-979720e92421]
name                : "br0"

_uuid               : a162acb5-cec8-44f0-b6df-9ede29746b05
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [550a8d16-7297-4a3c-8c61-7ac713d5858f]
name                : "eth7"

$ sudo ovs-vsctl list Interface
_uuid               : 550a8d16-7297-4a3c-8c61-7ac713d5858f
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
statistics          : {collisions=0, rx_bytes=2594921, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=26362, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : 2f4f9647-d03b-4f31-8bae-979720e92421
admin_state         : up
duplex              : full
ifindex             : 117
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

_uuid               : 0766286b-f835-4ff1-94b5-fe0b717dc402
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=871080, tx_dropped=0, tx_errors=0, tx_packets=9394}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 69630ea06ce4697369d257c47101be88b5b08e1d
Author:     Daniele Venturino &lt;daniele.venturino@m3s.it&gt;
AuthorDate: Wed Jan 8 16:03:07 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Jan 8 16:03:59 2014 -0800

    utilities: Wrong command syntax in ovs-vsctl manpage.
    
    The command shown in the man page to disable the STP protocol on a bridge
    is:
    
            ovs-vsctl clear Bridge br0 stp_enable
    
    Calling that, the following warning message is returned:
    
            ovs-vsctl: "clear" operation cannot be applied to column stp_enable
            of table Bridge, which is not allowed to be empty
    
    It seems correct to use the command:
    
            ovs-vsctl set Bridge br0 stp_enable=false
    
    Signed-off-by: Daniele Venturino &lt;daniele.venturino@m3s.it&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>

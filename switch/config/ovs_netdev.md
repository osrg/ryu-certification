---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
de234a07-a85a-48fd-9cbe-0432efe3a7ba
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b1ed0317-869c-4aa6-8598-18d75e8959c9
controller          : [2f63dad0-0d7a-4892-8de8-2c039b82a0e0]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0eed7b18-410e-42eb-832c-5336db669337, 6811d0e0-ac82-4ec2-9c43-13342f511ae9, 68f5fa22-0d82-4e27-8e53-ce03b22b6ed5, 9bf9deda-3287-4f70-99c4-bd995dde6b74]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 2f63dad0-0d7a-4892-8de8-2c039b82a0e0
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="762", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 6811d0e0-ac82-4ec2-9c43-13342f511ae9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [30c9841a-90ef-4de6-b8b3-2b3698858398]
name                : "eth23"

_uuid               : 0eed7b18-410e-42eb-832c-5336db669337
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d9b3fc72-6fd2-494d-882e-dd03fb9bc574]
name                : "eth22"

_uuid               : 68f5fa22-0d82-4e27-8e53-ce03b22b6ed5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [42f6b0f9-8ce1-4450-a717-dbf5df4210d8]
name                : "br0"

_uuid               : 9bf9deda-3287-4f70-99c4-bd995dde6b74
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [192f7499-aab0-4d7a-920b-bd1c0b572cda]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 42f6b0f9-8ce1-4450-a717-dbf5df4210d8
admin_state         : down
duplex              : full
ifindex             : 615
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

_uuid               : 192f7499-aab0-4d7a-920b-bd1c0b572cda
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
statistics          : {collisions=0, rx_bytes=40418362712, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=26984403, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 30c9841a-90ef-4de6-b8b3-2b3698858398
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=5023417500, tx_dropped=0, tx_errors=0, tx_packets=3348945}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : d9b3fc72-6fd2-494d-882e-dd03fb9bc574
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=28350338908, tx_dropped=0, tx_errors=0, tx_packets=18917270}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit ac79a98803dc2e02619bd2cea3241006bb75b03d
Author:     Sairam Venugopal &lt;vsairam@vmware.com&gt;
AuthorDate: Mon Nov 2 17:17:07 2015 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Nov 3 09:45:50 2015 -0800

    datapath-windows: Updating an External Adapter causes flow lookup failure
    
    This patch fixes an issue with updating the propeties of an external
    adapter in Windows. The issue causes flow lookups to fail until the
    kernel is reinstalled.
    
    Reported-at: https://github.com/openvswitch/ovs-issues/issues/102
    Signed-off-by: Sairam Venugopal &lt;vsairam@vmware.com&gt;
    Acked-by: Nithin Raju &lt;nithin@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>

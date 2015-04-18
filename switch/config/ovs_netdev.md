---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f8857b62-6609-4018-9208-1a6f2e5e716c
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : e3f2600c-c964-4989-b345-8a914264e0ce
controller          : [8bce027f-7353-4896-8006-9fcc277addc0]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [298a6123-0160-44e9-8610-68bbc134a761, 519df132-b0fc-430c-88b4-07261b0fd786, 7189b553-754a-477e-879f-08d0ae33b311, 7f59dd68-5976-4011-9233-b94bab2ea972]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 8bce027f-7353-4896-8006-9fcc277addc0
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="657", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 7f59dd68-5976-4011-9233-b94bab2ea972
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fbaf2854-d10a-4040-87f1-1093481910ae]
name                : "br0"

_uuid               : 519df132-b0fc-430c-88b4-07261b0fd786
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cfe403b9-f620-42c1-a351-050b3ed219c4]
name                : "eth22"

_uuid               : 7189b553-754a-477e-879f-08d0ae33b311
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [03c9517c-d197-48f7-9185-a7e72ec0e3b2]
name                : "eth23"

_uuid               : 298a6123-0160-44e9-8610-68bbc134a761
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f2f8a3f1-32d9-4d18-8130-fb93fa1f5dbe]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 03c9517c-d197-48f7-9185-a7e72ec0e3b2
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=41984853000, tx_dropped=0, tx_errors=0, tx_packets=27989902}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : fbaf2854-d10a-4040-87f1-1093481910ae
admin_state         : down
duplex              : full
ifindex             : 919
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

_uuid               : cfe403b9-f620-42c1-a351-050b3ed219c4
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=630784584622, tx_dropped=0, tx_errors=0, tx_packets=420690551}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : f2f8a3f1-32d9-4d18-8130-fb93fa1f5dbe
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
statistics          : {collisions=0, rx_bytes=1233011501236, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=822387686, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit f315ae4f469a44c3691057b541425da4d4f9cbdf
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Fri Apr 17 11:30:18 2015 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Sat Apr 18 00:56:18 2015 -0700

    dkms.conf.in: Install all kernel modules.
    
    With the latest change of separating vports into their own modules,
    we need to update the dkms.conf.in and make dkms install all vport
    modules.  So, this commit modifies the debian/rules to read all
    kernel module names and sets the dkms.conf correctly.
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
</pre>

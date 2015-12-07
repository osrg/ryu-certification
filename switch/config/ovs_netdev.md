---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
46c27540-37c3-406d-bb27-17372d8596f6
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 272575ac-d699-40f4-8d8f-f36c22f5ba70
controller          : [49d41bfc-b934-4fd2-8b32-de10af773ea8]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0f209c29-93f1-4fd5-8243-5cbdc07b7ab8, 1820a724-71e7-453b-aec9-733285ef3623, 4ea24aa1-8db4-4e5b-87a5-86bb59d8449e, 5e002653-9bfc-487d-a2f0-c8c7db4bc4d2]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 49d41bfc-b934-4fd2-8b32-de10af773ea8
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="667", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 1820a724-71e7-453b-aec9-733285ef3623
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4e0bacec-957e-42da-9a8e-0b1486bc4ed0]
name                : "eth21"

_uuid               : 4ea24aa1-8db4-4e5b-87a5-86bb59d8449e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4efb862e-9222-49b0-95a0-d36653fc8b2b]
name                : "eth23"

_uuid               : 0f209c29-93f1-4fd5-8243-5cbdc07b7ab8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [26f5483a-4245-480c-8eec-b3368fa89d83]
name                : "eth22"

_uuid               : 5e002653-9bfc-487d-a2f0-c8c7db4bc4d2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [29d55412-f54b-4d97-bd0f-c8124d59ff83]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 4e0bacec-957e-42da-9a8e-0b1486bc4ed0
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
statistics          : {collisions=0, rx_bytes=41693836006, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=27841671, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 4efb862e-9222-49b0-95a0-d36653fc8b2b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=5942491500, tx_dropped=0, tx_errors=0, tx_packets=3961661}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 29d55412-f54b-4d97-bd0f-c8124d59ff83
admin_state         : down
duplex              : full
ifindex             : 656
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

_uuid               : 26f5483a-4245-480c-8eec-b3368fa89d83
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=28961353540, tx_dropped=0, tx_errors=0, tx_packets=19327867}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit a6313b253a2a6b8d5fecc3967f8ab492575c5845
Author:     Ilya Maximets &lt;i.maximets@samsung.com&gt;
AuthorDate: Mon Dec 7 13:02:41 2015 +0300
Commit:     Ben Pfaff &lt;blp@ovn.org&gt;
CommitDate: Mon Dec 7 09:12:07 2015 -0800

    ofproto-dpif: add reply on error in ofproto/tnl-push-pop
    
    Fixes hang of 'ovs-appctl ofproto/tnl-push-pop' when an invalid
    argument passed.
    
    Signed-off-by: Ilya Maximets &lt;i.maximets@samsung.com&gt;
    Acked-by: Thadeu Lima de Souza Cascardo &lt;cascardo@redhat.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>

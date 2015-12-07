---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
76f555fb-e047-4c35-8adb-46ab6af8c222
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : dc96474a-b06f-4937-87d1-83271f03118f
controller          : [94a891d8-d6e1-4763-b891-fffa51307f8c]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [086e12f5-6af6-4236-9fe8-72c7756c7bbe, 33c52b36-60c6-42ca-9181-afb9a42754e3, 7c7e5234-e0fd-4ac0-beca-1fd775f036b6, e4abc542-5b2a-41e7-9b2c-2211d6e7b287]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 94a891d8-d6e1-4763-b891-fffa51307f8c
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="17", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 7c7e5234-e0fd-4ac0-beca-1fd775f036b6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bab91b36-9e13-402a-ae25-91ed9d0ae1e4]
name                : "eth22"

_uuid               : 086e12f5-6af6-4236-9fe8-72c7756c7bbe
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b70b8d07-5e12-4ac4-89c0-02dcf736d412]
name                : "eth23"

_uuid               : 33c52b36-60c6-42ca-9181-afb9a42754e3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [844786b7-84d3-4d0a-9e7c-b6728b053300]
name                : "eth21"

_uuid               : e4abc542-5b2a-41e7-9b2c-2211d6e7b287
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e9011f0e-06c1-41de-a50f-3299032180d9]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e9011f0e-06c1-41de-a50f-3299032180d9
admin_state         : down
duplex              : full
ifindex             : 658
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

_uuid               : bab91b36-9e13-402a-ae25-91ed9d0ae1e4
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=28961353798, tx_dropped=0, tx_errors=0, tx_packets=19327870}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : b70b8d07-5e12-4ac4-89c0-02dcf736d412
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

_uuid               : 844786b7-84d3-4d0a-9e7c-b6728b053300
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
statistics          : {collisions=0, rx_bytes=41693836264, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=27841674, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
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

---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f718b5c2-2196-4ca1-b7ae-66260f2f9e6b
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
_uuid               : 0aa64134-6f9f-437c-bbf9-3d65a20a944e
controller          : [beecf1ef-4819-4ac2-8b2c-4bf5a42265af]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [263db9a8-4a5c-4a41-9dc2-6649aafb93b6, 363f722a-7c32-4f4a-8ad5-e3e59d382a9c, 70b6945a-69a2-48af-9665-df20ceae9229, ba30f234-6f58-4b61-a8ad-0bfa9bdbfb5a]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : beecf1ef-4819-4ac2-8b2c-4bf5a42265af
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="652", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : ba30f234-6f58-4b61-a8ad-0bfa9bdbfb5a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1df1be28-699b-4d55-aa20-4887bd02e885]
name                : "eth21"

_uuid               : 263db9a8-4a5c-4a41-9dc2-6649aafb93b6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [25376609-4e28-4796-9efe-af87f17562b3]
name                : "eth22"

_uuid               : 70b6945a-69a2-48af-9665-df20ceae9229
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [faf66306-10db-48e6-9d74-e91292d11e52]
name                : "br0"

_uuid               : 363f722a-7c32-4f4a-8ad5-e3e59d382a9c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4428b6d7-9ae0-4f76-b071-683180cfe8ec]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 1df1be28-699b-4d55-aa20-4887bd02e885
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
statistics          : {collisions=0, rx_bytes=1218263207165, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=812535456, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 25376609-4e28-4796-9efe-af87f17562b3
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=619690793773, tx_dropped=0, tx_errors=0, tx_packets=413285418}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : faf66306-10db-48e6-9d74-e91292d11e52
admin_state         : down
duplex              : full
ifindex             : 859
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

_uuid               : 4428b6d7-9ae0-4f76-b071-683180cfe8ec
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=39395503500, tx_dropped=0, tx_errors=0, tx_packets=26263669}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 5a38795f5e6623b39004b53c7fede08399a09d79
Author:     Thomas Graf &lt;tgraf@noironetworks.com&gt;
AuthorDate: Sat Apr 4 08:24:13 2015 +0200
Commit:     Thomas Graf &lt;tgraf@noironetworks.com&gt;
CommitDate: Sat Apr 4 08:24:44 2015 +0200

    datapath: Turn vports with dependencies into separate modules
    
    Upstream commit:
        The internal and netdev vport remain part of openvswitch.ko. Encap
        vports including vxlan, gre, and geneve can be built as separate
        modules and are loaded on demand. Modules can be unloaded after use.
        Datapath ports keep a reference to the vport module during their
        lifetime.
    
        Allows to remove the error prone maintenance of the global list
        vport_ops_list.
    
        Signed-off-by: Thomas Graf &lt;tgraf@suug.ch&gt;
        Signed-off-by: David S. Miller &lt;davem@davemloft.net&gt;
    
    Also folds in the follow-up commits 9ba559d9ca3 to turned the non-GPL
    symbol exports to GPL exports, and fa2d8ff4e35 which fixes a module
    reference release bug.
    
    Exports various backwards compat functions linked into the main
    openvswitch module as GPL symbols to ensure vport modules can use them.
    
    Some fiddling with the Makefile was needed to work around the fact
    that Makefile variables can't contain '-' characters needed to define
    'vport-xxx' module sources. Also, Kbuild complains heavily if a
    $&#40;module&#41;-y = $&#40;module&#41;.o is defined which is actually backed with a .c
    file of the same name. Therefore, a new $&#40;build_multi_modules&#41; variable
    is defined which lists all module which consist of more than one source
    file.
    
    Upstream: 62b9c8d0372 &#40;&quot;ovs: Turn vports with dependencies into separate modules&quot;&#41;
    Upstream: 9ba559d9ca3 &#40;&quot;openvswitch: Export symbols as GPL symbols.&quot;&#41;
    Upstream: fa2d8ff4e35 &#40;&quot;openvswitch: Return vport module ref before destruction&quot;&#41;
    Signed-off-by: Thomas Graf &lt;tgraf@noironetworks.com&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>

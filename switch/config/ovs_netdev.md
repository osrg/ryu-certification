---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
4bc86a0d-91d1-4a56-8357-5401dbb9f142
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : ee31a35a-ce0c-407b-a809-eac29b202fcc
controller          : [37e09557-9205-4af5-a5ee-5dc7491c8f94]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1fd5f522-0f8b-4a57-9379-f7c011876acf, bf7c4834-c256-4691-a680-dc0e440e8b92, dca19dbb-8a2d-4694-87dd-35044b624dc4, f76d900c-f4ef-4952-9bb6-d7ad6d191189]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 37e09557-9205-4af5-a5ee-5dc7491c8f94
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=971, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f76d900c-f4ef-4952-9bb6-d7ad6d191189
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0a084270-7a62-45fd-b5c8-ed00a960d6fa]
name                : eth23

_uuid               : bf7c4834-c256-4691-a680-dc0e440e8b92
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9d8c93ba-b7ff-45e9-9eec-4e67adafd8ca]
name                : eth22

_uuid               : 1fd5f522-0f8b-4a57-9379-f7c011876acf
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4aec0fa9-e0bc-49e2-ba1a-010330433fe5]
name                : eth21

_uuid               : dca19dbb-8a2d-4694-87dd-35044b624dc4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [31bb6a36-81e4-401c-81e9-5bcc60572153]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 0a084270-7a62-45fd-b5c8-ed00a960d6fa
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1550
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3456317908, tx_dropped=0, tx_errors=0, tx_packets=8030835}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 4aec0fa9-e0bc-49e2-ba1a-010330433fe5
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=3132420550, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=27937901, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 9d8c93ba-b7ff-45e9-9eec-4e67adafd8ca
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1550
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2445269312, tx_dropped=0, tx_errors=0, tx_packets=13113109}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 31bb6a36-81e4-401c-81e9-5bcc60572153
admin_state         : down
duplex              : full
ifindex             : 496
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit f0e5aa1107407bbcabb3a816ee40a98b8ba2050c
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Fri Jun 13 14:52:59 2014 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Fri Jun 13 14:52:59 2014 -0700

    lib/classifier: Fix use of uninitialized memory.
    
    When reaching the end of a prefix trie, we checked one bit off the end
    to the intended data.  However, since the trie node in that case has
    NULLs for both edge links, this did not result in incorrect
    functionality.
    
    Found via check-valgrind.
    
    Reported-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>

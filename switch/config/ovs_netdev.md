---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ab0dae05-79a7-4a10-bb32-975ba06a8dcd
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 41325a17-17b7-43af-b112-60c4dc297fe3
controller          : [3fd6eb0c-73f9-4822-ba02-7b854a40f94b]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [08c09264-1e7d-4cb2-865f-49b5c0288e7c, 1500eff0-55df-46a3-8578-ddac3c6471c2, 25ae6186-4852-4b7c-b1e3-1afdea1d8ea3, bfe08bae-5ac5-48eb-91c8-3c0f038d7c8f]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 3fd6eb0c-73f9-4822-ba02-7b854a40f94b
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=557, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 08c09264-1e7d-4cb2-865f-49b5c0288e7c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [caf9297a-fb68-4638-8569-6f38a939d402]
name                : eth21

_uuid               : 1500eff0-55df-46a3-8578-ddac3c6471c2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e5920961-d784-4d2a-bdb2-c1d05851c869]
name                : eth22

_uuid               : 25ae6186-4852-4b7c-b1e3-1afdea1d8ea3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0dc9926f-87ba-48ac-b289-78e202d5fff6]
name                : eth23

_uuid               : bfe08bae-5ac5-48eb-91c8-3c0f038d7c8f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3a4ddd5c-2e80-4baa-b6cb-4befd6b3e588]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 3a4ddd5c-2e80-4baa-b6cb-4befd6b3e588
admin_state         : down
duplex              : full
ifindex             : 125
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

_uuid               : e5920961-d784-4d2a-bdb2-c1d05851c869
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1376054730, tx_dropped=0, tx_errors=0, tx_packets=921348}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : caf9297a-fb68-4638-8569-6f38a939d402
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
statistics          : {collisions=0, rx_bytes=3506146269, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=2348018, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 0dc9926f-87ba-48ac-b289-78e202d5fff6
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2480371500, tx_dropped=0, tx_errors=0, tx_packets=1653581}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 5e3a8607018daeb540cc91b7b7e4b4da3ee6f6eb
Author:     Anoob Soman &lt;anoob.soman@citrix.com&gt;
AuthorDate: Tue Mar 25 12:32:03 2014 +0000
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed May 21 07:46:35 2014 -0700

    rhel: Remove creation of fake bond interface
    
    fake-iface, option to add-bond, was added for compatibility
    reasons and need not be used otherwise.
    
    Signed-off-by: Anoob Soman &lt;anoob.soman@citrix.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>

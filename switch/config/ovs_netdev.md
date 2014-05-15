---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
4d6cf821-5a94-44b6-b07d-e1846c532997
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
_uuid               : d7d0745e-6250-4ab8-816f-75a3fac147f3
controller          : [9384991a-6a72-4cf0-b976-6113fafabbdd]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [25717344-bcfb-4c09-b42f-3dc7e21d2408, 81bb70d6-e3e5-461f-8d2b-94ebf5afaa00, a517c8ab-32ae-4200-a8cf-daecc8312327, e0214ab5-f39d-493b-85cd-cabb856f3852]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 9384991a-6a72-4cf0-b976-6113fafabbdd
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=551, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 25717344-bcfb-4c09-b42f-3dc7e21d2408
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3d661b8a-fe52-4a9a-8c90-60f6e3b02bd1]
name                : eth21

_uuid               : e0214ab5-f39d-493b-85cd-cabb856f3852
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [af56db2a-c86a-473d-a5c1-162289e25822]
name                : br0

_uuid               : 81bb70d6-e3e5-461f-8d2b-94ebf5afaa00
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [65d1dd23-049f-4de3-a01c-5294ca0c9d34]
name                : eth22

_uuid               : a517c8ab-32ae-4200-a8cf-daecc8312327
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [20d1fd67-58dd-4c77-8c83-d5b815764402]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : af56db2a-c86a-473d-a5c1-162289e25822
admin_state         : down
duplex              : full
ifindex             : 202
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

_uuid               : 3d661b8a-fe52-4a9a-8c90-60f6e3b02bd1
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
statistics          : {collisions=0, rx_bytes=4076440721, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=2734720, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 20d1fd67-58dd-4c77-8c83-d5b815764402
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2840431500, tx_dropped=0, tx_errors=0, tx_packets=1893621}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 65d1dd23-049f-4de3-a01c-5294ca0c9d34
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1625133894, tx_dropped=0, tx_errors=0, tx_packets=1089715}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit fbf4f74d8fb9184ebeceaf8338c834bcc839943a
Author:     Simon Horman &lt;horms@verge.net.au&gt;
AuthorDate: Thu May 15 09:05:03 2014 +0900
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Thu May 15 15:31:50 2014 -0700

    datapath: sample action without side effects
    
    The sample action is rather generic, allowing arbitrary actions to be
    executed based on a probability. However its use, within the Open vSwitch
    code-base is limited: only a single user-space action is ever nested.
    
    A consequence of the current implementation of sample actions is that
    depending on weather the sample action executed &#40;due to its probability&#41;
    any side-effects of nested actions may or may not be present before
    executing subsequent actions.  This has the potential to complicate
    verification of valid actions by the &#40;kernel&#41; datapath. And indeed adding
    support for push and pop MPLS actions inside sample actions is one case
    where such case.
    
    In order to allow all supported actions to be continue to be nested inside
    sample actions without the potential need for complex verification code
    this patch changes the implementation of the sample action in the kernel
    datapath so that sample actions are more like a function call and any side
    effects of nested actions are not present when executing subsequent
    actions.
    
    With the above in mind the motivation for this change is twofold:
    
    * To contain side-effects the sample action in the hope of making it
      easier to deal with in the future and;
    * To avoid some rather complex verification code introduced in the MPLS
      datapath patch.
    
    Some notes about the implementation:
    
    * This patch silently changes the behaviour of sample actions whose nested
      actions have side-effects. There are no known users of such sample
      actions.
    
    * sample&#40;&#41; does not clone the skb for the only known use-case of the sample
      action: a single nested userspace action. In such a case a clone is not
      needed as the userspace action has no side effects.
    
      Given that there are no known users of other nested actions and in order
      to avoid the complexity of predicting if other sequences of actions have
      side-effects in such cases the skb is cloned.
    
    * As sample&#40;&#41; provides a cloned skb in the unlikely case where there are
      nested actions other than a single userspace action it is no longer
      necessary to clone the skb in do_execute_actions&#40;&#41; when executing a
      recirculation action just because the keep_skb parameter is set: this
      parameter was only set when processing the nested actions of a sample
      action.  Moreover it is possible to remove the keep_skb parameter of
      do_execute_actions entirely.
    
    * As sample&#40;&#41; provides either a cloned skb or one that has had a
      reference taken &#40;using keep_skb&#41; to do_execute_actions&#40;&#41;
      the original skb passed to sample&#40;&#41; is never consumed. Thus the
      caller of sample&#40;&#41; &#40;also do_execute_actions&#40;&#41;&#41; can use its generic
      error handling to free the skb on error.
    
    Signed-off-by: Simon Horman &lt;horms@verge.net.au&gt;
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>

---
layout: default
title: Ryu Certification - NoviFlow NoviKit200 - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* NoviFlow NoviKit200

# OpenFlow related configuration
<pre>
prompt&gt; show config controller
        Controller [0] --&gt; 10.24.150.30:6633
prompt&gt; show config switch all
        Device name: eth
        IP address: 10.24.44.1
        Subnet Mask: 255.0.0.0
        -
        Device name: eth
        Destination     Gateway         Mask
        169.254.0.0     0.0.0.0         255.255.0.0
        -
        -
        Dhcp status: off
        -
        Miss send length: 128
        -
        Datapath id: 0x044
        -
        Mon Jun 9 6:52:8 2014 UTC+9:00
        -
        Switch to Controller Echo Interval : 15
prompt&gt; show config table tableid all
--------Table id: 0
        Match Fields (11):
          0             : OFPXMT_OFB_IN_PORT
          3             : OFPXMT_OFB_ETH_DST
          4             : OFPXMT_OFB_ETH_SRC
          5             : OFPXMT_OFB_ETH_TYPE
          6             : OFPXMT_OFB_VLAN_VID
          7             : OFPXMT_OFB_VLAN_PCP
          10            : OFPXMT_OFB_IP_PROTO
          11            : OFPXMT_OFB_IPV4_SRC
          12            : OFPXMT_OFB_IPV4_DST
          13, 15, 17    : OFPXMT_OFB_TCP/UDP/SCTP_SRC
          14, 16, 18    : OFPXMT_OFB_TCP/UDP/SCTP_DST
        Name: novi_table_0
        Metadata_match: 0x00000000ffffffff
        Metadata_write: 0x00000000ffffffff
        Max_entries: 4095

--------Table id: 1
        Match Fields (5):
          0             : OFPXMT_OFB_IN_PORT
          1             : OFPXMT_OFB_IN_PHY_PORT
          3             : OFPXMT_OFB_ETH_DST
          26            : OFPXMT_OFB_IPV6_SRC
          27            : OFPXMT_OFB_IPV6_DST
        Name: novi_table_1
        Metadata_match: 0x00000000ffffffff
        Metadata_write: 0x00000000ffffffff
        Max_entries: 4095

--------Table id: 2
        Match Fields (11):
          2             : OFPXMT_OFB_METADATA
          0             : OFPXMT_OFB_IN_PORT
          3             : OFPXMT_OFB_ETH_DST
          4             : OFPXMT_OFB_ETH_SRC
          5             : OFPXMT_OFB_ETH_TYPE
          6             : OFPXMT_OFB_VLAN_VID
          10            : OFPXMT_OFB_IP_PROTO
          11            : OFPXMT_OFB_IPV4_SRC
          12            : OFPXMT_OFB_IPV4_DST
          13, 15, 17    : OFPXMT_OFB_TCP/UDP/SCTP_SRC
          14, 16, 18    : OFPXMT_OFB_TCP/UDP/SCTP_DST
        Name: novi_table_2
        Metadata_match: 0x00000000ffffffff
        Metadata_write: 0x00000000ffffffff
        Max_entries: 4095

--------Table id: 3
        Match Fields (11):
          2             : OFPXMT_OFB_METADATA
          0             : OFPXMT_OFB_IN_PORT
          3             : OFPXMT_OFB_ETH_DST
          4             : OFPXMT_OFB_ETH_SRC
          5             : OFPXMT_OFB_ETH_TYPE
          6             : OFPXMT_OFB_VLAN_VID
          10            : OFPXMT_OFB_IP_PROTO
          11            : OFPXMT_OFB_IPV4_SRC
          12            : OFPXMT_OFB_IPV4_DST
          13, 15, 17    : OFPXMT_OFB_TCP/UDP/SCTP_SRC
          14, 16, 18    : OFPXMT_OFB_TCP/UDP/SCTP_DST
        Name: novi_table_3
        Metadata_match: 0x00000000ffffffff
        Metadata_write: 0x00000000ffffffff
        Max_entries: 4095

--------Table id: 4
        Match Fields (11):
          2             : OFPXMT_OFB_METADATA
          0             : OFPXMT_OFB_IN_PORT
          3             : OFPXMT_OFB_ETH_DST
          4             : OFPXMT_OFB_ETH_SRC
          5             : OFPXMT_OFB_ETH_TYPE
          6             : OFPXMT_OFB_VLAN_VID
          10            : OFPXMT_OFB_IP_PROTO
          11            : OFPXMT_OFB_IPV4_SRC
          12            : OFPXMT_OFB_IPV4_DST
          13, 15, 17    : OFPXMT_OFB_TCP/UDP/SCTP_SRC
          14, 16, 18    : OFPXMT_OFB_TCP/UDP/SCTP_DST
        Name: novi_table_4
        Metadata_match: 0x00000000ffffffff
        Metadata_write: 0x00000000ffffffff
        Max_entries: 4095

--------Table id: 5
        Match Fields (11):
          2             : OFPXMT_OFB_METADATA
          0             : OFPXMT_OFB_IN_PORT
          3             : OFPXMT_OFB_ETH_DST
          4             : OFPXMT_OFB_ETH_SRC
          5             : OFPXMT_OFB_ETH_TYPE
          6             : OFPXMT_OFB_VLAN_VID
          10            : OFPXMT_OFB_IP_PROTO
          11            : OFPXMT_OFB_IPV4_SRC
          12            : OFPXMT_OFB_IPV4_DST
          13, 15, 17    : OFPXMT_OFB_TCP/UDP/SCTP_SRC
          14, 16, 18    : OFPXMT_OFB_TCP/UDP/SCTP_DST
        Name: novi_table_5
        Metadata_match: 0x00000000ffffffff
        Metadata_write: 0x00000000ffffffff
        Max_entries: 4095

--------Table id: 6
        Match Fields (11):
          2             : OFPXMT_OFB_METADATA
          0             : OFPXMT_OFB_IN_PORT
          3             : OFPXMT_OFB_ETH_DST
          4             : OFPXMT_OFB_ETH_SRC
          5             : OFPXMT_OFB_ETH_TYPE
          6             : OFPXMT_OFB_VLAN_VID
          10            : OFPXMT_OFB_IP_PROTO
          11            : OFPXMT_OFB_IPV4_SRC
          12            : OFPXMT_OFB_IPV4_DST
          13, 15, 17    : OFPXMT_OFB_TCP/UDP/SCTP_SRC
          14, 16, 18    : OFPXMT_OFB_TCP/UDP/SCTP_DST
        Name: novi_table_6
        Metadata_match: 0x00000000ffffffff
        Metadata_write: 0x00000000ffffffff
        Max_entries: 4095

--------Table id: 7
        Match Fields (11):
          2             : OFPXMT_OFB_METADATA
          0             : OFPXMT_OFB_IN_PORT
          3             : OFPXMT_OFB_ETH_DST
          4             : OFPXMT_OFB_ETH_SRC
          5             : OFPXMT_OFB_ETH_TYPE
          6             : OFPXMT_OFB_VLAN_VID
          10            : OFPXMT_OFB_IP_PROTO
          11            : OFPXMT_OFB_IPV4_SRC
          12            : OFPXMT_OFB_IPV4_DST
          13, 15, 17    : OFPXMT_OFB_TCP/UDP/SCTP_SRC
          14, 16, 18    : OFPXMT_OFB_TCP/UDP/SCTP_DST
        Name: novi_table_7
        Metadata_match: 0x00000000ffffffff
        Metadata_write: 0x00000000ffffffff
        Max_entries: 4095

--------Table id: 8
        Match Fields (11):
          2             : OFPXMT_OFB_METADATA
          0             : OFPXMT_OFB_IN_PORT
          3             : OFPXMT_OFB_ETH_DST
          4             : OFPXMT_OFB_ETH_SRC
          5             : OFPXMT_OFB_ETH_TYPE
          6             : OFPXMT_OFB_VLAN_VID
          10            : OFPXMT_OFB_IP_PROTO
          11            : OFPXMT_OFB_IPV4_SRC
          12            : OFPXMT_OFB_IPV4_DST
          13, 15, 17    : OFPXMT_OFB_TCP/UDP/SCTP_SRC
          14, 16, 18    : OFPXMT_OFB_TCP/UDP/SCTP_DST
        Name: novi_table_8
        Metadata_match: 0x00000000ffffffff
        Metadata_write: 0x00000000ffffffff
        Max_entries: 8191

--------Table id: 9
        Match Fields (11):
          2             : OFPXMT_OFB_METADATA
          0             : OFPXMT_OFB_IN_PORT
          3             : OFPXMT_OFB_ETH_DST
          4             : OFPXMT_OFB_ETH_SRC
          5             : OFPXMT_OFB_ETH_TYPE
          6             : OFPXMT_OFB_VLAN_VID
          10            : OFPXMT_OFB_IP_PROTO
          11            : OFPXMT_OFB_IPV4_SRC
          12            : OFPXMT_OFB_IPV4_DST
          13, 15, 17    : OFPXMT_OFB_TCP/UDP/SCTP_SRC
          14, 16, 18    : OFPXMT_OFB_TCP/UDP/SCTP_DST
        Name: novi_table_9
        Metadata_match: 0x00000000ffffffff
        Metadata_write: 0x00000000ffffffff
        Max_entries: 8191

--------Table id: 10
        Match Fields (11):
          2             : OFPXMT_OFB_METADATA
          0             : OFPXMT_OFB_IN_PORT
          3             : OFPXMT_OFB_ETH_DST
          4             : OFPXMT_OFB_ETH_SRC
          5             : OFPXMT_OFB_ETH_TYPE
          6             : OFPXMT_OFB_VLAN_VID
          10            : OFPXMT_OFB_IP_PROTO
          11            : OFPXMT_OFB_IPV4_SRC
          12            : OFPXMT_OFB_IPV4_DST
          13, 15, 17    : OFPXMT_OFB_TCP/UDP/SCTP_SRC
          14, 16, 18    : OFPXMT_OFB_TCP/UDP/SCTP_DST
        Name: novi_table_10
        Metadata_match: 0x00000000ffffffff
        Metadata_write: 0x00000000ffffffff
        Max_entries: 4095

--------Table id: 11
        Match Fields (11):
          2             : OFPXMT_OFB_METADATA
          0             : OFPXMT_OFB_IN_PORT
          3             : OFPXMT_OFB_ETH_DST
          4             : OFPXMT_OFB_ETH_SRC
          5             : OFPXMT_OFB_ETH_TYPE
          6             : OFPXMT_OFB_VLAN_VID
          10            : OFPXMT_OFB_IP_PROTO
          11            : OFPXMT_OFB_IPV4_SRC
          12            : OFPXMT_OFB_IPV4_DST
          13, 15, 17    : OFPXMT_OFB_TCP/UDP/SCTP_SRC
          14, 16, 18    : OFPXMT_OFB_TCP/UDP/SCTP_DST
        Name: novi_table_11
        Metadata_match: 0x00000000ffffffff
        Metadata_write: 0x00000000ffffffff
        Max_entries: 4095

--------Table id: 12
        Match Fields (11):
          2             : OFPXMT_OFB_METADATA
          0             : OFPXMT_OFB_IN_PORT
          3             : OFPXMT_OFB_ETH_DST
          4             : OFPXMT_OFB_ETH_SRC
          5             : OFPXMT_OFB_ETH_TYPE
          6             : OFPXMT_OFB_VLAN_VID
          10            : OFPXMT_OFB_IP_PROTO
          11            : OFPXMT_OFB_IPV4_SRC
          12            : OFPXMT_OFB_IPV4_DST
          13, 15, 17    : OFPXMT_OFB_TCP/UDP/SCTP_SRC
          14, 16, 18    : OFPXMT_OFB_TCP/UDP/SCTP_DST
        Name: novi_table_12
        Metadata_match: 0x00000000ffffffff
        Metadata_write: 0x00000000ffffffff
        Max_entries: 4095

--------Table id: 13
        Match Fields (11):
          2             : OFPXMT_OFB_METADATA
          0             : OFPXMT_OFB_IN_PORT
          3             : OFPXMT_OFB_ETH_DST
          4             : OFPXMT_OFB_ETH_SRC
          5             : OFPXMT_OFB_ETH_TYPE
          6             : OFPXMT_OFB_VLAN_VID
          10            : OFPXMT_OFB_IP_PROTO
          11            : OFPXMT_OFB_IPV4_SRC
          12            : OFPXMT_OFB_IPV4_DST
          13, 15, 17    : OFPXMT_OFB_TCP/UDP/SCTP_SRC
          14, 16, 18    : OFPXMT_OFB_TCP/UDP/SCTP_DST
        Name: novi_table_13
        Metadata_match: 0x00000000ffffffff
        Metadata_write: 0x00000000ffffffff
        Max_entries: 4095

--------Table id: 14
        Match Fields (11):
          2             : OFPXMT_OFB_METADATA
          0             : OFPXMT_OFB_IN_PORT
          3             : OFPXMT_OFB_ETH_DST
          4             : OFPXMT_OFB_ETH_SRC
          5             : OFPXMT_OFB_ETH_TYPE
          6             : OFPXMT_OFB_VLAN_VID
          10            : OFPXMT_OFB_IP_PROTO
          11            : OFPXMT_OFB_IPV4_SRC
          12            : OFPXMT_OFB_IPV4_DST
          13, 15, 17    : OFPXMT_OFB_TCP/UDP/SCTP_SRC
          14, 16, 18    : OFPXMT_OFB_TCP/UDP/SCTP_DST
        Name: novi_table_14
        Metadata_match: 0x00000000ffffffff
        Metadata_write: 0x00000000ffffffff
        Max_entries: 4095

--------Table id: 15
        Match Fields (11):
          2             : OFPXMT_OFB_METADATA
          0             : OFPXMT_OFB_IN_PORT
          3             : OFPXMT_OFB_ETH_DST
          4             : OFPXMT_OFB_ETH_SRC
          5             : OFPXMT_OFB_ETH_TYPE
          6             : OFPXMT_OFB_VLAN_VID
          10            : OFPXMT_OFB_IP_PROTO
          11            : OFPXMT_OFB_IPV4_SRC
          12            : OFPXMT_OFB_IPV4_DST
          13, 15, 17    : OFPXMT_OFB_TCP/UDP/SCTP_SRC
          14, 16, 18    : OFPXMT_OFB_TCP/UDP/SCTP_DST
        Name: novi_table_15
        Metadata_match: 0x00000000ffffffff
        Metadata_write: 0x00000000ffffffff
        Max_entries: 8191

--------Table id: 16
        Match Fields (11):
          2             : OFPXMT_OFB_METADATA
          0             : OFPXMT_OFB_IN_PORT
          3             : OFPXMT_OFB_ETH_DST
          4             : OFPXMT_OFB_ETH_SRC
          5             : OFPXMT_OFB_ETH_TYPE
          6             : OFPXMT_OFB_VLAN_VID
          10            : OFPXMT_OFB_IP_PROTO
          11            : OFPXMT_OFB_IPV4_SRC
          12            : OFPXMT_OFB_IPV4_DST
          13, 15, 17    : OFPXMT_OFB_TCP/UDP/SCTP_SRC
          14, 16, 18    : OFPXMT_OFB_TCP/UDP/SCTP_DST
        Name: novi_table_16
        Metadata_match: 0x00000000ffffffff
        Metadata_write: 0x00000000ffffffff
        Max_entries: 8191

--------Table id: 17
        Match Fields (11):
          2             : OFPXMT_OFB_METADATA
          0             : OFPXMT_OFB_IN_PORT
          3             : OFPXMT_OFB_ETH_DST
          4             : OFPXMT_OFB_ETH_SRC
          5             : OFPXMT_OFB_ETH_TYPE
          6             : OFPXMT_OFB_VLAN_VID
          10            : OFPXMT_OFB_IP_PROTO
          11            : OFPXMT_OFB_IPV4_SRC
          12            : OFPXMT_OFB_IPV4_DST
          13, 15, 17    : OFPXMT_OFB_TCP/UDP/SCTP_SRC
          14, 16, 18    : OFPXMT_OFB_TCP/UDP/SCTP_DST
        Name: novi_table_17
        Metadata_match: 0x00000000ffffffff
        Metadata_write: 0x00000000ffffffff
        Max_entries: 4095

--------Table id: 18
        Match Fields (11):
          2             : OFPXMT_OFB_METADATA
          0             : OFPXMT_OFB_IN_PORT
          3             : OFPXMT_OFB_ETH_DST
          4             : OFPXMT_OFB_ETH_SRC
          5             : OFPXMT_OFB_ETH_TYPE
          6             : OFPXMT_OFB_VLAN_VID
          10            : OFPXMT_OFB_IP_PROTO
          11            : OFPXMT_OFB_IPV4_SRC
          12            : OFPXMT_OFB_IPV4_DST
          13, 15, 17    : OFPXMT_OFB_TCP/UDP/SCTP_SRC
          14, 16, 18    : OFPXMT_OFB_TCP/UDP/SCTP_DST
        Name: novi_table_18
        Metadata_match: 0x00000000ffffffff
        Metadata_write: 0x00000000ffffffff
        Max_entries: 4095

--------Table id: 19
        Match Fields (11):
          2             : OFPXMT_OFB_METADATA
          0             : OFPXMT_OFB_IN_PORT
          3             : OFPXMT_OFB_ETH_DST
          4             : OFPXMT_OFB_ETH_SRC
          5             : OFPXMT_OFB_ETH_TYPE
          6             : OFPXMT_OFB_VLAN_VID
          10            : OFPXMT_OFB_IP_PROTO
          11            : OFPXMT_OFB_IPV4_SRC
          12            : OFPXMT_OFB_IPV4_DST
          13, 15, 17    : OFPXMT_OFB_TCP/UDP/SCTP_SRC
          14, 16, 18    : OFPXMT_OFB_TCP/UDP/SCTP_DST
        Name: novi_table_19
        Metadata_match: 0x00000000ffffffff
        Metadata_write: 0x00000000ffffffff
        Max_entries: 4095

--------Table id: 20
        Match Fields (11):
          2             : OFPXMT_OFB_METADATA
          0             : OFPXMT_OFB_IN_PORT
          3             : OFPXMT_OFB_ETH_DST
          4             : OFPXMT_OFB_ETH_SRC
          5             : OFPXMT_OFB_ETH_TYPE
          6             : OFPXMT_OFB_VLAN_VID
          10            : OFPXMT_OFB_IP_PROTO
          11            : OFPXMT_OFB_IPV4_SRC
          12            : OFPXMT_OFB_IPV4_DST
          13, 15, 17    : OFPXMT_OFB_TCP/UDP/SCTP_SRC
          14, 16, 18    : OFPXMT_OFB_TCP/UDP/SCTP_DST
        Name: novi_table_20
        Metadata_match: 0x00000000ffffffff
        Metadata_write: 0x00000000ffffffff
        Max_entries: 4095

--------Table id: 21
        Match Fields (11):
          2             : OFPXMT_OFB_METADATA
          0             : OFPXMT_OFB_IN_PORT
          3             : OFPXMT_OFB_ETH_DST
          4             : OFPXMT_OFB_ETH_SRC
          5             : OFPXMT_OFB_ETH_TYPE
          6             : OFPXMT_OFB_VLAN_VID
          10            : OFPXMT_OFB_IP_PROTO
          11            : OFPXMT_OFB_IPV4_SRC
          12            : OFPXMT_OFB_IPV4_DST
          13, 15, 17    : OFPXMT_OFB_TCP/UDP/SCTP_SRC
          14, 16, 18    : OFPXMT_OFB_TCP/UDP/SCTP_DST
        Name: novi_table_21
        Metadata_match: 0x00000000ffffffff
        Metadata_write: 0x00000000ffffffff
        Max_entries: 4095

--------Table id: 22
        Match Fields (11):
          2             : OFPXMT_OFB_METADATA
          0             : OFPXMT_OFB_IN_PORT
          3             : OFPXMT_OFB_ETH_DST
          4             : OFPXMT_OFB_ETH_SRC
          5             : OFPXMT_OFB_ETH_TYPE
          6             : OFPXMT_OFB_VLAN_VID
          10            : OFPXMT_OFB_IP_PROTO
          11            : OFPXMT_OFB_IPV4_SRC
          12            : OFPXMT_OFB_IPV4_DST
          13, 15, 17    : OFPXMT_OFB_TCP/UDP/SCTP_SRC
          14, 16, 18    : OFPXMT_OFB_TCP/UDP/SCTP_DST
        Name: novi_table_22
        Metadata_match: 0x00000000ffffffff
        Metadata_write: 0x00000000ffffffff
        Max_entries: 4095

--------Table id: 23
        Match Fields (11):
          2             : OFPXMT_OFB_METADATA
          0             : OFPXMT_OFB_IN_PORT
          3             : OFPXMT_OFB_ETH_DST
          4             : OFPXMT_OFB_ETH_SRC
          5             : OFPXMT_OFB_ETH_TYPE
          6             : OFPXMT_OFB_VLAN_VID
          10            : OFPXMT_OFB_IP_PROTO
          11            : OFPXMT_OFB_IPV4_SRC
          12            : OFPXMT_OFB_IPV4_DST
          13, 15, 17    : OFPXMT_OFB_TCP/UDP/SCTP_SRC
          14, 16, 18    : OFPXMT_OFB_TCP/UDP/SCTP_DST
        Name: novi_table_23
        Metadata_match: 0x00000000ffffffff
        Metadata_write: 0x00000000ffffffff
        Max_entries: 4095

--------Table id: 24
        Match Fields (11):
          2             : OFPXMT_OFB_METADATA
          0             : OFPXMT_OFB_IN_PORT
          3             : OFPXMT_OFB_ETH_DST
          4             : OFPXMT_OFB_ETH_SRC
          5             : OFPXMT_OFB_ETH_TYPE
          6             : OFPXMT_OFB_VLAN_VID
          10            : OFPXMT_OFB_IP_PROTO
          11            : OFPXMT_OFB_IPV4_SRC
          12            : OFPXMT_OFB_IPV4_DST
          13, 15, 17    : OFPXMT_OFB_TCP/UDP/SCTP_SRC
          14, 16, 18    : OFPXMT_OFB_TCP/UDP/SCTP_DST
        Name: novi_table_24
        Metadata_match: 0x00000000ffffffff
        Metadata_write: 0x00000000ffffffff
        Max_entries: 1023

--------Table id: 25
        Match Fields (11):
          2             : OFPXMT_OFB_METADATA
          0             : OFPXMT_OFB_IN_PORT
          3             : OFPXMT_OFB_ETH_DST
          4             : OFPXMT_OFB_ETH_SRC
          5             : OFPXMT_OFB_ETH_TYPE
          6             : OFPXMT_OFB_VLAN_VID
          10            : OFPXMT_OFB_IP_PROTO
          11            : OFPXMT_OFB_IPV4_SRC
          12            : OFPXMT_OFB_IPV4_DST
          13, 15, 17    : OFPXMT_OFB_TCP/UDP/SCTP_SRC
          14, 16, 18    : OFPXMT_OFB_TCP/UDP/SCTP_DST
        Name: novi_table_25
        Metadata_match: 0x00000000ffffffff
        Metadata_write: 0x00000000ffffffff
        Max_entries: 1023

--------Table id: 26
        Match Fields (11):
          2             : OFPXMT_OFB_METADATA
          0             : OFPXMT_OFB_IN_PORT
          3             : OFPXMT_OFB_ETH_DST
          4             : OFPXMT_OFB_ETH_SRC
          5             : OFPXMT_OFB_ETH_TYPE
          6             : OFPXMT_OFB_VLAN_VID
          10            : OFPXMT_OFB_IP_PROTO
          11            : OFPXMT_OFB_IPV4_SRC
          12            : OFPXMT_OFB_IPV4_DST
          13, 15, 17    : OFPXMT_OFB_TCP/UDP/SCTP_SRC
          14, 16, 18    : OFPXMT_OFB_TCP/UDP/SCTP_DST
        Name: novi_table_26
        Metadata_match: 0x00000000ffffffff
        Metadata_write: 0x00000000ffffffff
        Max_entries: 1023

--------Table id: 27
        Match Fields (11):
          2             : OFPXMT_OFB_METADATA
          0             : OFPXMT_OFB_IN_PORT
          3             : OFPXMT_OFB_ETH_DST
          4             : OFPXMT_OFB_ETH_SRC
          5             : OFPXMT_OFB_ETH_TYPE
          6             : OFPXMT_OFB_VLAN_VID
          10            : OFPXMT_OFB_IP_PROTO
          11            : OFPXMT_OFB_IPV4_SRC
          12            : OFPXMT_OFB_IPV4_DST
          13, 15, 17    : OFPXMT_OFB_TCP/UDP/SCTP_SRC
          14, 16, 18    : OFPXMT_OFB_TCP/UDP/SCTP_DST
        Name: novi_table_27
        Metadata_match: 0x00000000ffffffff
        Metadata_write: 0x00000000ffffffff
        Max_entries: 1023
prompt&gt;
</pre>

# Version information
<pre>
prompt&gt; show status switch
        -- latest -- (current)
        NoviWare-OPE version: 250.0.6   bfc9aea9d9a9ce7ce0f40874b3ae7a39300f34a8
        NoviWare-PPE version: 250.0.6   34b144dcba0561748b1e5ab60e2ad7da951adc2a
        EZDriver version: 8.46a
        -- previous --
        NoviWare-OPE version: 250.0.5   9b44f913ed738cc5a2605e133e2b408057a92881
        NoviWare-PPE version: 250.0.5   34b144dcba0561748b1e5ab60e2ad7da951adc2a
        EZDriver version: 8.46a
        -- default --
        NoviWare-OPE version: 250.0.5   4f492a897bdd714add9b2c7aa95832034b875d05
        NoviWare-PPE version: 250.0.5   9801e19958c3028c7b1e28bd2d5dec7a7c9721f5
        EZDriver version: 8.46a
prompt&gt;
</pre>

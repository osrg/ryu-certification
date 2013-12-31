---
layout: default
title: NoviFlow_NoviKit200.md - config
---

# OpenFlow related configuration
<pre>
[root@EZsysNP4 ~]# cat noviware_build/novi_hw_conf.xml
&lt;?xml version="1.0" encoding="UTF-8"?&gt;

&lt;novi_hw_conf xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="hw_conf.xsd" &gt;
        &lt;hw_tables&gt;
                &lt;hw_table size="4096" &gt;&lt;/hw_table&gt;
                &lt;hw_table size="4096" &gt;&lt;/hw_table&gt;
                &lt;hw_table size="4096" &gt;&lt;/hw_table&gt;
        &lt;/hw_tables&gt;

        &lt;hw_group_table size="4096" /&gt;
&lt;/novi_hw_conf&gt;

[root@EZsysNP4 ~]# cat noviware_build/noviswitch.xml
&lt;?xml version="1.0" encoding="UTF-8"?&gt;



&lt;noviswitch xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="noviswitch.xsd"
switch_id="1"  miss_send_len ="128"  &gt;
        &lt;ports&gt;
                &lt;port port_id="1" name="novi_port_1" hw_port_no="0" &gt;&lt;/port&gt;
                &lt;port port_id="2" name="novi_port_2" hw_port_no="1" &gt;&lt;/port&gt;
                &lt;port port_id="3" name="novi_port_3" hw_port_no="2" &gt;&lt;/port&gt;
                &lt;port port_id="4" name="novi_port_4" hw_port_no="3" &gt;&lt;/port&gt;
                &lt;port port_id="5" name="novi_port_5" hw_port_no="4" &gt;&lt;/port&gt;
                &lt;port port_id="6" name="novi_port_6" hw_port_no="5" &gt;&lt;/port&gt;
                &lt;port port_id="7" name="novi_port_7" hw_port_no="6" &gt;&lt;/port&gt;
                &lt;port port_id="8" name="novi_port_8" hw_port_no="7" &gt;&lt;/port&gt;
                &lt;port port_id="9" name="novi_port_9" hw_port_no="8" &gt;&lt;/port&gt;
                &lt;port port_id="10" name="novi_port_10" hw_port_no="9" &gt;&lt;/port&gt;
                &lt;port port_id="11" name="novi_port_11" hw_port_no="10" &gt;&lt;/port&gt;
                &lt;port port_id="12" name="novi_port_12" hw_port_no="11" &gt;&lt;/port&gt;
                &lt;port port_id="13" name="novi_port_13" hw_port_no="12" &gt;&lt;/port&gt;
                &lt;port port_id="14" name="novi_port_14" hw_port_no="13" &gt;&lt;/port&gt;
                &lt;port port_id="15" name="novi_port_15" hw_port_no="14" &gt;&lt;/port&gt;
                &lt;port port_id="16" name="novi_port_16" hw_port_no="15" &gt;&lt;/port&gt;
                &lt;port port_id="17" name="novi_port_17" hw_port_no="16" &gt;&lt;/port&gt;
                &lt;port port_id="18" name="novi_port_18" hw_port_no="17" &gt;&lt;/port&gt;
                &lt;port port_id="19" name="novi_port_19" hw_port_no="18" &gt;&lt;/port&gt;
                &lt;port port_id="20" name="novi_port_20" hw_port_no="19" &gt;&lt;/port&gt;
                &lt;port port_id="21" name="novi_port_21" hw_port_no="20" &gt;&lt;/port&gt;
                &lt;port port_id="22" name="novi_port_22" hw_port_no="21" &gt;&lt;/port&gt;
                &lt;port port_id="23" name="novi_port_23" hw_port_no="22" &gt;&lt;/port&gt;
                &lt;port port_id="24" name="novi_port_24" hw_port_no="23" &gt;&lt;/port&gt;
                &lt;port port_id="25" name="novi_port_25" hw_port_no="24" &gt;&lt;/port&gt;
                &lt;port port_id="26" name="novi_port_26" hw_port_no="25" &gt;&lt;/port&gt;
                &lt;port port_id="27" name="novi_port_27" hw_port_no="26" &gt;&lt;/port&gt;
                &lt;port port_id="28" name="novi_port_28" hw_port_no="27" &gt;&lt;/port&gt;

        &lt;/ports&gt;

        &lt;group_table max_group_buckets="15" /&gt;
&lt;/noviswitch&gt;
</pre>

# Version information
<pre>
[root@EZsysNP4 ~]# cat noviware_build/VERSION
NOVISWITCH: NW200
NOVIENGINE:1.1.0
NOVICORE:1.1.0
DRIVER:8.46a
PPE:1.0.1
</pre>

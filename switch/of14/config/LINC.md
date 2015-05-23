---
layout: default
title: Ryu Certification - LINC - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* LINC

# OpenFlow related configuration
<pre>
$ cat rel/linc/releases/1.0/sys.config | grep -v '%%'
[{linc,
     [{of_config,enabled},
      {sync_routing,true},
      {capable_switch_ports,
          [{port,1,[{interface,"eth21"}]},
           {port,2,[{interface,"eth22"}]},
           {port,3,[{interface,"eth23"}]}]},
      {capable_switch_queues,[]},
      {logical_switches,
          [{switch,0,
               [{backend,linc_us5},
                {controllers,[{"Switch0-Controller","10.24.150.30",6633,tcp}]},
                {controllers_listener,disabled},
                {queues_status,disabled},
                {ports,
                    [{port,1,[{queues,[]}]},
                     {port,2,[{queues,[]}]},
                     {port,3,[{queues,[]}]}]}]}]}]},
 {enetconf,
     [{capabilities,
          [{base,{1,0}},
           {base,{1,1}},
           {startup,{1,0}},
           {'writable-running',{1,0}}]},
      {callback_module,linc_ofconfig},
      {sshd_ip,any},
      {sshd_port,1830},
      {sshd_user_passwords,[{"linc","linc"}]}]},
 {lager,
     [{handlers,
          [{lager_console_backend,debug},
           {lager_file_backend,
               [{"log/error.log",error,10485760,"$D0",5},
                {"log/console.log",info,10485760,"$D0",5}]}]}]},
 {sasl,
     [{sasl_error_logger,{file,"log/sasl-error.log"}},
      {errlog_type,error},
      {error_logger_mf_dir,"log/sasl"},
      {error_logger_mf_maxbytes,10485760},
      {error_logger_mf_maxfiles,5}]},
 {sync,[{excluded_modules,[procket]}]}].
</pre>

# Version information
<pre>
$ erl -version
Erlang (SMP,ASYNC_THREADS) (BEAM) emulator version 6.1

$ git log -1 --pretty=fuller
commit 78b590b353b353d985c0c839ffcaa26669255a76
Merge: c65c167 a862e0c
Author:     Marc Sugiyama &lt;sugiyama@acm.org&gt;
AuthorDate: Fri May 22 13:59:19 2015 -0700
Commit:     Marc Sugiyama &lt;sugiyama@acm.org&gt;
CommitDate: Fri May 22 13:59:19 2015 -0700

    Merge pull request #359 from FlowForwarding/appfest_bugs
    
    Appfest bugs

$ git --git-dir=deps/of_protocol/.git/ log -1 --pretty=fuller
commit cfe639c92749fcd633801b34149ac15ca908338b
Author:     Szymon Mentel &lt;szymon.mentel@erlang-solutions.com&gt;
AuthorDate: Tue May 19 18:19:33 2015 +0200
Commit:     Szymon Mentel &lt;szymon.mentel@erlang-solutions.com&gt;
CommitDate: Thu May 21 17:21:05 2015 +0200

    Fix interpretation of total_len field in packet_in message
    
    The 'total_len' field indicates total length of the frame captured
    on the switch. Thus it cannot be computed from the ofp_packet_in.data field
    value as it can contain only a packet portion.
    
    The fix is applied to OpenFlow v1.3 and 1.4.

$ git --git-dir=deps/pkt/.git/ log -1 --pretty=fuller
commit 5b96ba0f3ba573f69ffc3bc6b3adae1ebcb58509
Merge: c4b46da 6f0c45f
Author:     Szymon Mentel &lt;szymon.mentel@erlang-solutions.com&gt;
AuthorDate: Thu May 15 10:30:07 2014 +0200
Commit:     Szymon Mentel &lt;szymon.mentel@erlang-solutions.com&gt;
CommitDate: Thu May 15 10:30:07 2014 +0200

    Merge pull request #13 from esl/checksum_optimizations_tcp
    
    Checksum optimizations for TCP
</pre>

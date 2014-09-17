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
          [{port,1,[{interface,eth21}]},
           {port,2,[{interface,eth22}]},
           {port,3,[{interface,eth23}]}]},
      {capable_switch_queues,[]},
      {logical_switches,
          [{switch,0,
               [{backend,linc_us5},
                {controllers,[{Switch0-Controller,10.24.150.30,6633,tcp}]},
                {controllers_listener,disabled},
                {queues_status,disabled},
                {ports,
                    [{port,1,{queues,[]}},
                     {port,2,{queues,[]}},
                     {port,3,{queues,[]}}]}]}]}]},
 {enetconf,
     [{capabilities,
          [{base,{1,0}},
           {base,{1,1}},
           {startup,{1,0}},
           {'writable-running',{1,0}}]},
      {callback_module,linc_ofconfig},
      {sshd_ip,any},
      {sshd_port,1830},
      {sshd_user_passwords,[{linc,linc}]}]},
 {lager,
     [{handlers,
          [{lager_console_backend,debug},
           {lager_file_backend,
               [{log/error.log,error,10485760,,5},
                {log/console.log,info,10485760,,5}]}]}]},
 {sasl,
     [{sasl_error_logger,{file,log/sasl-error.log}},
      {errlog_type,error},
      {error_logger_mf_dir,log/sasl},
      {error_logger_mf_maxbytes,10485760},
      {error_logger_mf_maxfiles,5}]},
 {sync,[{excluded_modules,[procket]}]}].
</pre>

# Version information
<pre>
$ erl -version
Erlang (SMP,ASYNC_THREADS) (BEAM) emulator version 6.1

$ git log -1 --pretty=fuller
commit 25e5e34d45cba7c211192baacf2fb36f4549f0a4
Merge: 9f1ee10 e8743a7
Author:     Szymon Mentel &lt;szymon.mentel@erlang-solutions.com&gt;
AuthorDate: Wed Sep 17 08:31:57 2014 +0200
Commit:     Szymon Mentel &lt;szymon.mentel@erlang-solutions.com&gt;
CommitDate: Wed Sep 17 08:31:57 2014 +0200

    Merge pull request #342 from subh007/patch-1
    
    Update config_gen

$ git --git-dir=deps/of_protocol/.git/ log -1 --pretty=fuller
commit d09dcab6515a299cf6423d8ad5f8282b09168935
Merge: 2da25f4 590d7d1
Author:     Szymon Mentel &lt;szymon.mentel@erlang-solutions.com&gt;
AuthorDate: Tue Aug 19 13:18:56 2014 +0200
Commit:     Szymon Mentel &lt;szymon.mentel@erlang-solutions.com&gt;
CommitDate: Tue Aug 19 13:18:56 2014 +0200

    Merge pull request #76 from FlowForwarding/ofp_match_for_vlan
    
    Add macros for OFPVID_PRESENT and OFPVID_NONE values

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

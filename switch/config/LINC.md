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
               [{backend,linc_us4},
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
Erlang (SMP,ASYNC_THREADS,HIPE) (BEAM) emulator version 5.10.4

$ git log -1 --pretty=fuller
commit 94cd1b174734127a08852ae710e5595930bc32cb
Merge: 6ed40cb 53b421b
Author:     Szymon Mentel &lt;szymon.mentel@erlang-solutions.com&gt;
AuthorDate: Fri Jun 6 13:45:07 2014 +0200
Commit:     Szymon Mentel &lt;szymon.mentel@erlang-solutions.com&gt;
CommitDate: Fri Jun 6 13:45:07 2014 +0200

    Merge pull request #330 from FlowForwarding/of-config-setup-controller
    
    Use new ofp_client API for updating connection config via OF-Config

$ git --git-dir=deps/of_protocol/.git/ log -1 --pretty=fuller
commit 79254d0856ba87ac6f7b656fcd9404f7092905c4
Merge: 1125617 44dc72c
Author:     Szymon Mentel &lt;szymon.mentel@erlang-solutions.com&gt;
AuthorDate: Fri Jun 6 13:47:48 2014 +0200
Commit:     Szymon Mentel &lt;szymon.mentel@erlang-solutions.com&gt;
CommitDate: Fri Jun 6 13:47:48 2014 +0200

    Merge pull request #74 from FlowForwarding/of-config-setup-controller
    
    Implement API for externally configuring connection to a contoller

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

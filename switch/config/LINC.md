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
commit 70ffc9b1ea6bb43e23d5e4154a611ce797d7f251
Merge: 3d01882 6009b25
Author:     Szymon Mentel &lt;szymon.mentel@erlang-solutions.com&gt;
AuthorDate: Tue Apr 7 18:00:49 2015 +0200
Commit:     Szymon Mentel &lt;szymon.mentel@erlang-solutions.com&gt;
CommitDate: Tue Apr 7 18:00:49 2015 +0200

    Merge pull request #357 from FlowForwarding/doc
    
    Add technical LINC-Switch documentation

$ git --git-dir=deps/of_protocol/.git/ log -1 --pretty=fuller
commit a52f54a9fb02633e4cb5cb74290caf0f308ea2e1
Merge: 48b734b 8f557cd
Author:     Szymon Mentel &lt;szymon.mentel@erlang-solutions.com&gt;
AuthorDate: Wed Jan 7 18:08:32 2015 +0100
Commit:     Szymon Mentel &lt;szymon.mentel@erlang-solutions.com&gt;
CommitDate: Wed Jan 7 18:08:32 2015 +0100

    Merge pull request #82 from FlowForwarding/oe_refactorings
    
    OE refactorings

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

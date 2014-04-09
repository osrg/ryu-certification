---
layout: default
title: Ryu Certification - LINC - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* LINC

# OpenFlow related configuration
<pre>
$ cat rel/linc/releases/1.0/sys.config | grep -v '%%'
[
 {linc,
  [
   {of_config, enabled},

   {capable_switch_ports,
    [
     {port, 1, [{interface, eth1}]},
     {port, 2, [{interface, eth2}]}
    ]},

   {capable_switch_queues,
    [
    ]},

   {logical_switches,
    [
     {switch, 0,
      [
       {backend, linc_us4},

       {controllers,
        [
         {Switch0-DefaultController, 10.24.100.30, 6633, tcp}

        ]},

       {controllers_listener, disabled},

       {queues_status, disabled},

       {ports, [
                {port, 1, {queues, []}},
                {port, 2, {queues, []}}
               ]}
      ]}

    ]}

  ]},

 {enetconf,
  [
   {capabilities, [{base, {1, 0}},
                   {base, {1, 1}},
                   {startup, {1, 0}},
                   {'writable-running', {1, 0}}]},
   {callback_module, linc_ofconfig},
   {sshd_ip, any},
   {sshd_port, 1830},
   {sshd_user_passwords,
    [
     {linc, linc}
    ]}
  ]},

 {lager,
  [
   {handlers,
    [
     {lager_console_backend, info},
     {lager_file_backend,
      [
       {log/error.log, error, 10485760, , 5},
       {log/console.log, info, 10485760, , 5}
      ]}
    ]}
  ]},

 {sasl,
  [
   {sasl_error_logger, {file, log/sasl-error.log}},
   {errlog_type, error},
   {error_logger_mf_dir, log/sasl},      % Log directory
   {error_logger_mf_maxbytes, 10485760},   % 10 MB max file size
   {error_logger_mf_maxfiles, 5}           % 5 files max
  ]},

 {sync,
  [
   {excluded_modules, [procket]}
  ]}
 
].
</pre>

# Version information
<pre>
$ erl -version
Erlang (SMP,ASYNC_THREADS) (BEAM) emulator version 5.10.4

$ git log -1 --pretty=fuller
commit 06dee9746919c104c188dad2bdb6f7a780c022dd
Merge: fa44391 0d06004
Author:     Magnus Henoch &lt;magnus.henoch@gmail.com&gt;
AuthorDate: Wed Apr 9 14:08:05 2014 +0100
Commit:     Magnus Henoch &lt;magnus.henoch@gmail.com&gt;
CommitDate: Wed Apr 9 14:08:05 2014 +0100

    Merge pull request #315 from FlowForwarding/v5
    
    OpenFlow 1.4

$ git --git-dir=deps/of_protocol/.git/ log -1 --pretty=fuller
commit 50169652f324bce7a145a67103f3b68d81ff180e
Merge: 61e4c2f 6658826
Author:     Magnus Henoch &lt;magnus.henoch@gmail.com&gt;
AuthorDate: Wed Apr 9 14:07:39 2014 +0100
Commit:     Magnus Henoch &lt;magnus.henoch@gmail.com&gt;
CommitDate: Wed Apr 9 14:07:39 2014 +0100

    Merge pull request #72 from FlowForwarding/v5
    
    Openflow 1.4

$ git --git-dir=deps/pkt/.git/ log -1 --pretty=fuller
commit c4b46da3655cf4c47bb411e371da7d313dc37c1e
Merge: 68f5b05 85fd13b
Author:     Szymon Mentel &lt;szymon.mentel@erlang-solutions.com&gt;
AuthorDate: Wed Feb 19 16:44:31 2014 +0100
Commit:     Szymon Mentel &lt;szymon.mentel@erlang-solutions.com&gt;
CommitDate: Wed Feb 19 16:44:31 2014 +0100

    Merge pull request #12 from esl/checksum_optimizations
    
    Checksum optimization in UDP
</pre>

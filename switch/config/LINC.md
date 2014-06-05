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
Erlang (SMP,ASYNC_THREADS,HIPE) (BEAM) emulator version 5.10.4

$ git log -1 --pretty=fuller
commit 6ed40cb649ab2288163c4a86c281d0990f9b7ac8
Author:     Szymon Mentel &lt;szymon.mentel@erlang-solutions.com&gt;
AuthorDate: Wed May 21 17:53:59 2014 +0200
Commit:     Szymon Mentel &lt;szymon.mentel@erlang-solutions.com&gt;
CommitDate: Wed May 21 17:53:59 2014 +0200

    Add script testing if a queue {min,max}-rate properties are set correctly
    
    (Motivated by #310).

$ git --git-dir=deps/of_protocol/.git/ log -1 --pretty=fuller
commit 11256179e1e97022e1cfc24645e346a23a49daf8
Author:     ruanpienaar &lt;ruan800@gmail.com&gt;
AuthorDate: Fri May 30 14:02:15 2014 +0100
Commit:     ruanpienaar &lt;ruan800@gmail.com&gt;
CommitDate: Fri May 30 14:02:15 2014 +0100

    added Erlang 17

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

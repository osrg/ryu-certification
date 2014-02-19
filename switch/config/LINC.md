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
commit 763d5504ce24e5fc50f5cefd29fc9cad1259a65d
Merge: 11cc088 a2a297c
Author:     Szymon Mentel &lt;szymon.mentel@erlang-solutions.com&gt;
AuthorDate: Thu Feb 13 17:52:43 2014 +0100
Commit:     Szymon Mentel &lt;szymon.mentel@erlang-solutions.com&gt;
CommitDate: Thu Feb 13 17:52:43 2014 +0100

    Merge pull request #288 from FlowForwarding/controlling_libpcap
    
    Controlling libpcap

$ git --git-dir=deps/of_protocol/.git/ log -1 --pretty=fuller
commit 61e4c2f6c09fc2783fe8a494b84cd5d794f6bf02
Merge: 3bc8b2f 202a5af
Author:     Szymon Mentel &lt;szymon.mentel@erlang-solutions.com&gt;
AuthorDate: Tue Dec 31 05:16:34 2013 -0800
Commit:     Szymon Mentel &lt;szymon.mentel@erlang-solutions.com&gt;
CommitDate: Tue Dec 31 05:16:34 2013 -0800

    Merge pull request #57 from yamt/oxm-4bytes
    
    make oxm on-wire length for ipv6_flabel and mpls_label 32-bit

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

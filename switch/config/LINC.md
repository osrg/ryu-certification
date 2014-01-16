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
commit a03ccaee10f006443c8f713768aac6484371ad67
Merge: e382830 cdbb889
Author:     Szymon Mentel &lt;szymon.mentel@erlang-solutions.com&gt;
AuthorDate: Thu Jan 16 01:50:16 2014 -0800
Commit:     Szymon Mentel &lt;szymon.mentel@erlang-solutions.com&gt;
CommitDate: Thu Jan 16 01:50:16 2014 -0800

    Merge pull request #280 from FlowForwarding/mininet_cleanup
    
    Add deleting all copied releases to rel_copy script

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
commit 68f5b053e05e52055295cb317f9b64ffa5bc5d76
Merge: 38e92c5 363333f
Author:     Szymon Mentel &lt;szymon.mentel@erlang-solutions.com&gt;
AuthorDate: Fri Nov 1 12:07:10 2013 -0700
Commit:     Szymon Mentel &lt;szymon.mentel@erlang-solutions.com&gt;
CommitDate: Fri Nov 1 12:07:10 2013 -0700

    Merge pull request #10 from esl/issue111
    
    Fix handling SCTP packets
</pre>

---
layout: default
title: LINC - config
---

# OpenFlow related configuration
<pre>
$ cat rel/linc/releases/1.0/sys.config
[
 {linc,
  [
   {of_config, enabled},

   {capable_switch_ports,
    [
     {port, 1, [{interface, "eth1"}]},
     {port, 2, [{interface, "eth2"}]}
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
         {"Switch0-DefaultController", "10.24.100.30", 6633, tcp}

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
                   {writable-running, {1, 0}}]},
   {callback_module, linc_ofconfig},
   {sshd_ip, any},
   {sshd_port, 1830},
   {sshd_user_passwords,
    [
     {"linc", "linc"}
    ]}
  ]},

 {lager,
  [
   {handlers,
    [
     {lager_console_backend, info},
     {lager_file_backend,
      [
       {"log/error.log", error, 10485760, "$D0", 5},
       {"log/console.log", info, 10485760, "$D0", 5}
      ]}
    ]}
  ]},

 {sasl,
  [
   {sasl_error_logger, {file, "log/sasl-error.log"}},
   {errlog_type, error},
   {error_logger_mf_dir, "log/sasl"},      % Log directory
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
commit 7eca7324fe6baf4e0474f6c9008741e1adc6c019
Author:     Akos korosmezey &lt;akos.korosmezey@erlang-solutions.com&gt;
AuthorDate: Wed Dec 18 19:41:01 2013 +0100
Commit:     Akos korosmezey &lt;akos.korosmezey@erlang-solutions.com&gt;
CommitDate: Wed Dec 18 19:41:01 2013 +0100

    Fix incorrect github urls. Closes #271
</pre>

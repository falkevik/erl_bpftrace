<pre>
$ ./run_bpftrace
    usage: ./run_bpftrace <path to beam> <filter size> [summerize]



Erlang/OTP 23 [RELEASE CANDIDATE 1] [erts-10.7] [source-ad99dde400] [64-bit] [smp:8:8] [ds:8:8:10] [async-threads:1] [hipe]

Eshell V10.7  (abort with ^G)
1> size(element(2,file:read_file("/home/jonas/Downloads/bigfile"))).
302233568
2> size(element(2,file:read_file("/home/jonas/Downloads/bigfile"))).
302233568
3> size(element(2,file:read_file("/home/jonas/Downloads/bigfile"))).
302233568
4> i(0,10,0).
[{registered_name,erl_prim_loader},
 {current_function,{erl_prim_loader,loop,3}},
 {initial_call,{erlang,apply,2}},
 {status,waiting},
 {message_queue_len,0},
 {links,[<0.0.0>]},
 {dictionary,[]},
 {trap_exit,true},
 {error_handler,error_handler},
 {priority,normal},
 {group_leader,<0.0.0>},
 {total_heap_size,13544},
 {heap_size,2586},
 {stack_size,7},
 {reductions,37073},
 {garbage_collection,[{max_heap_size,#{error_logger => true,kill => true,size => 0}},
                      {min_bin_vheap_size,46422},
                      {min_heap_size,233},
                      {fullsweep_after,65535},
                      {minor_gcs,26}]},
 {suspending,[]}]

5> i(0,60,0).
[{registered_name,file_server_2},
 {current_function,{gen_server,loop,7}},
 {initial_call,{proc_lib,init_p,5}},
 {status,waiting},
 {message_queue_len,0},
 {links,[<0.49.0>]},
 {dictionary,[{'$initial_call',{file_server,init,1}},
              {'$ancestors',[kernel_sup,<0.47.0>]}]},
 {trap_exit,true},
 {error_handler,error_handler},
 {priority,normal},
 {group_leader,<0.46.0>},
 {total_heap_size,466},
 {heap_size,233},
 {stack_size,12},
 {reductions,184},
 {garbage_collection,[{max_heap_size,#{error_logger => true,kill => true,size => 0}},
                      {min_bin_vheap_size,46422},
                      {min_heap_size,233},
                      {fullsweep_after,65535},
                      {minor_gcs,3}]},
 {suspending,[]}]

$ ./run_bpftrace /home/jonas/src/otp/bin/x86_64-unknown-linux-gnu/beam.smp 200000
Attaching 10 probes...
erts_alcu_alloc_thr_pref pid <0.19.0> size 347899
erts_alcu_alloc_thr_pref pid <0.51.0> size 347899
erts_alcu_alloc_thr_pref pid <0.75.0> size 262175
erts_alcu_alloc_thr_pref pid <0.75.0> size 262175
erts_alcu_alloc_thr_pref pid <0.10.0> size 565523
erts_alcu_alloc_thr_pref pid <0.10.0> size 314640
erts_alcu_alloc_thr_spec pid <0.10.0> size 210672
erts_alcu_alloc_thr_spec pid <0.10.0> size 210672
erts_alcu_alloc_thr_spec pid <0.10.0> size 210672
erts_alcu_alloc_thr_pref pid <0.10.0> size 302233599
erts_alcu_alloc_thr_pref pid <0.10.0> size 302233599
erts_alcu_alloc_thr_pref pid <0.60.0> size 302233599


$ ls -l /home/jonas/Downloads/bigfile 
-rw-rw-r--. 1 jonas jonas 302233568 Feb 18 22:17 /home/jonas/Downloads/bigfile

</pre>


```
$ ./run_bpftrace
    usage: ./run_bpftrace <path to beam> <filter size> [summerize]
```
<pre>
file:read_file/1 is handle via file_server process.
while prim_file:read_file/1 are calling the dirty nif directly.

Erlang/OTP 23 [RELEASE CANDIDATE 1] [erts-10.7] [source-ad99dde400] [64-bit] [smp:8:8] [ds:8:8:10] [async-threads:1] [hipe]

Eshell V10.7  (abort with ^G)
1> spawn(fun() -> size(element(2,file:read_file("/home/jonas/Downloads/bigfile"))) end).
<0.83.0>
2> spawn(fun() -> size(element(2,prim_file:read_file("/home/jonas/Downloads/bigfile"))) end).
<0.85.0>
3> spawn(fun() -> size(element(2,prim_file:read_file("/home/jonas/Downloads/bigfile"))) end).
<0.87.0>
4> spawn(fun() -> size(element(2,prim_file:read_file("/home/jonas/Downloads/bigfile"))) end).
<0.89.0>
5> spawn(fun() -> size(element(2,prim_file:read_file("/home/jonas/Downloads/bigfile"))) end).
<0.91.0>


$ ./run_bpftrace /home/jonas/src/otp/bin/x86_64-unknown-linux-gnu/beam.smp 20000
[sudo] password for jonas:
Attaching 10 probes...
...
erts_alcu_alloc_thr_pref pid <0.60.0> size 302233599
erts_alcu_alloc_thr_pref pid <0.10.0> size 50459
erts_alcu_alloc_thr_pref pid <0.85.0> size 302233599
erts_alcu_alloc_thr_pref pid <0.87.0> size 302233599
erts_alcu_alloc_thr_pref pid <0.89.0> size 302233599
erts_alcu_alloc_thr_pref pid <0.91.0> size 302233599


$ ls -l /home/jonas/Downloads/bigfile 
-rw-rw-r--. 1 jonas jonas 302233568 Feb 18 22:17 /home/jonas/Downloads/bigfile

</pre>

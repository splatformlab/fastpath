### Fast Path Condition Bug Patches ###
<table>
 <thead>
    <tr>
     <td>Title</td>
     <td>Category</td>
     <td>Why is this a Fast Path Bug?</td>
     <td>Which lines cause the bug?</td>
    </tr>
    </thead>
   <tbody>
<tr><td><font size=+1><b>4:</b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm?id=49255c619fbd482d704289b5eb2795f8e3b7ff2e">move check for disabled anti-fragmentation out of fastpath</a></td><td>CON</td><td> This damages performance in the fast path with a condition that is unlikely to occur there.</td><td>  L168</td></tr>
<tr><td><font size=+1><b>19:</b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/drivers?id=8f140b407f3be04e7202be9aa0cfef3006d14c9f">Shadow the gpio_mask register</a></td><td>CON</td><td> Out of date code creates unecessary fast path call</td><td> Optimization</td></tr>
<tr><td><font size=+1><b>22:</b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/net?id=d64d80a2cde94f3e89caebd27240be419fec5b81">don't extract flow keys on early demuxed sks in socket match</a></td><td>CON</td><td>  Unnecessary values being accessed in fast path</td><td> Multiple</td></tr>
<tr><td><font size=+1><b>30:</b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/net?id=bb9fc37358ffa9de1cc2b2b6f1a559b926ef50d9">wrong multiplication of TCPOLEN_TSTAMP_ALIGNED in tcp_sack skips fastpath</a></td><td>CON</td><td>  Incorrect multiplication skips fast path</td><td>  L447</td></tr>
<tr><td><font size=+1><b>32:</b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/net?id=8587523640441a9ff2564ebc6efeb39497ad6709">Check rps_flow_table when RPS map length is 1</a></td><td>CON</td><td>  Missing check for fast path</td><td>  L2563</td></tr>
<tr><td><font size=+1><b>33:</b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/net?id=767dd03369ac18af58efdef0383d6eb986eab426">speedup sock_recv_ts_and_drops()</a></td><td>CON</td><td>  Slow function in fast path</td><td></td></tr>
<tr><td><font size=+1><b>35:</b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/net?id=6f74651ae626ec672028587bc700538076dfbefb">Seperate DSACK from SACK fast path</a></td><td>CON</td><td> Unnecessary check in fast path</td><td></td></tr>
   </tbody>
 </table>

### Patches Related to Fast Path Conditions ###

<table>
 <thead>
     <tr>
     <td>Title</td>
     <td>Category</td>
    </tr>
    </thead>
   <tbody>
   <tr><td><font size=+1><b>2: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/slub.c?id=70d71228af9360cc4a0198ecd6351a1b34fa6d01">slub: remove object activities out of checking functions</a></td><td>CON / Path State</td></tr>
<tr><td><font size=+1><b>10: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/slub.c?id=89124d706db0aa95daacfa4c0df45a43a44d44f4">slub: Add might_sleep_if() to slab_alloc()</a></td><td>Path State / CON</td></tr>
<tr><td><font size=+1><b>13: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/memcontrol.c?id=81d39c20f5ee2437d71709beb82597e2a38efbbc">fix shrinking memory to return -EBUSY by fixing retry algorithm</a></td><td>RET / CON</td></tr>
<tr><td><font size=+1><b>20: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/slub.c?id=74e2134ff892ee4ea4fbd52637060b71e540faf1">SLUB: Fix __GFP_ZERO unlikely() annotation</a></td><td>CON</td></tr>
<tr><td><font size=+1><b>21: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/slub.c?id=0f24f1287a86b198c1e4bd4ce45e8565e40ff804">tracing, slab: Define kmem_cache_alloc_notrace ifdef CONFIG_TRACING</a></td><td>RET / CON</td></tr>
<tr><td><font size=+1><b>22: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/page_alloc.c?id=4365a5676fa3aa1d5ae6c90c22a0044f09ba584e">fix NUMA constraint check with nodemask</a></td><td>CON</td></tr>
<tr><td><font size=+1><b>26: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/memcontrol.c?id=747388d78a0ae768fd82b55c4ed38aa646a72364">fix css_is_ancestor() RCU locking</a></td><td>Path State/ CON</td></tr>
<tr><td><font size=+1><b>29: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/?id=ebb76ce16daf6908dc030dec1c00827d37129fe5&context=40&ignorews=0&dt=0">fix wrong VM_BUG_ON() in try_charge()'s mm->owner check</a></td><td>RET / CON</td></tr>
<tr><td><font size=+1><b>31: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/page_alloc.c?id=f33261d75b88f55a08e6a9648cef73509979bfba">fix deferred congestion timeout if preferred zone is not allowed</a></td><td>CON</td></tr>
<tr><td><font size=+1><b>39: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/slub.c?id=73736e0387ba0e6d2b703407b4d26168d31516a7">slub: fix a possible memleak in __slab_alloc()</a></td><td>"Path State
/ CON / FAU"</td></tr>
<tr><td><font size=+1><b>43: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/slub.c?id=4d7868e6475d478172581828021bd8a356726679">slub: Do not dereference NULL pointer in node_match</a></td><td>RET / CON</td></tr>
<tr><td><font size=+1><b>44: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/memcontrol.c?id=a0d8b00a3381f9d75764b3377590451cb0b4fe41">do not declare OOM from __GFP_NOFAIL allocations</a></td><td>CON /  Path State/ FAU</td></tr>
<tr><td><font size=+1><b>58: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs/btrfs/file.c?id=8b050d350c7846462a21e9e054c9154ede9b43cf">fix skipped error handle when log sync failed</a></td><td>FAU / ADS / CON</td></tr>
<tr><td><font size=+1><b>59: </b></font><a href="https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?h=v4.12-rc7&id=b05fd8742f6291b67571ad0fdad4da6b6eb98025">fix transaction leak during fsync call</a></td><td>FAU / CON</td></tr>
<tr><td><font size=+1><b>62: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs/btrfs/file.c?id=9dcbeed4d7e11e1dcf5e55475de3754f0855d1c2">fix signed overflows in btrfs_sync_file</a></td><td>FAU / CON</td></tr>
<tr><td><font size=+1><b>73: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/net/ipv4/tcp_input.c?id=15986e1aadbbf40a331cddd0470bb434d156431d">[TCP]: tcp_rcv_rtt_measure_ts() call in pure-ACK path is superfluous</a></td><td>CON</td></tr>
<tr><td><font size=+1><b>74: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/net/ipv4/tcp_input.c?id=9ae27e0adbf471c7a6b80102e38e1d5a346b3b38">tcp: Fix slab corruption with ipv6 and tcp6fuzz</a></td><td>CON / RET</td></tr>
<tr><td><font size=+1><b>75: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/net/ipv4/tcp_input.c?id=53240c208776d557dba9d7afedbcdbf512774c16">tcp: Fix possible double-ack w/ user dma</a></td><td>CON / RET / RACE</td></tr>
<tr><td><font size=+1><b>76: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/net/ipv4/tcp_input.c?id=59ea33a68a9083ac98515e4861c00e71efdc49a1">tcp: perform DMA to userspace only if there is a task waiting for it</a></td><td>CON /  Path State</td></tr>
<tr><td><font size=+1><b>78: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/net/ipv4/tcp_input.c?id=aab2b4bf224ef8358d262f95b568b8ad0cecf0a0">tcp: fix double-counted receiver RTT when leaving receiver fast path</a></td><td>CON / RET</td></tr>
<tr><td><font size=+1><b>80: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/net/ipv4/tcp_input.c?id=c10d9310edf5aa4a676991139d1a43ec7d87e56b">tcp: do not assume TCP code is non preemptible</a></td><td>CON / Path State</td></tr>
   </tbody>
 </table>

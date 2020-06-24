### Fast Path Output Patches ###
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
<tr><td><font size=+1><b>1:</b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=cbef8478bee55775ac312a574aad48af7bb9cf9f">pmd_huge() returns true for non-present hugepage</a></td><td>RET</td><td> This bug occurs in both fast path and slow path, and stems from an incorrect return value on some conditional branches</td><td> Multiple (both fast and slow path functions)</td></tr>
<tr><td><font size=+1><b>12:</b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs?id=ce170828e24959c69e7a40364731edc0535c550f">fix disk file size and memory file size mismatch</a></td><td>RET</td><td> File size is unchanged in fast path, need to skip fast path in order to ensure correct file size is returned</td><td>  L2167</td></tr>
<tr><td><font size=+1><b>17:</b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs?id=b09e593d799560f1a0782c20ac5900058390a26f">Fix a ref count bug and other clean ups</a></td><td>RET</td><td>"  Incorrect ref count in fast path
"</td><td> Multiple</td></tr>
<tr><td><font size=+1><b>38:</b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/drivers?id=51d2bfbddb33dc59786a3a41f7eeb59e30fa561c">Move ehca2ib_return_code() out of line</a></td><td>RET</td><td> Inlined slowpath code</td><td> Optimization</td></tr>
<tr><td><font size=+1><b>45:</b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/net?id=76fecd8275be6de76513430e7526825944ab932f">In mpls_egress verify the packet length.</a></td><td>FAU/RET</td><td>  Failing to confirm byte presence in fast path</td><td> L92</td></tr>
   </tbody>
 </table>

### Patches Related to Fast Path Output ###
<table>
 <thead>
     <tr>
     <td>Title</td>
     <td>Category</td>
    </tr>
    </thead>
   <tbody>
 <tr><td><font size=+1><b>3: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/slub.c?id=272c1d21d6fe42979068e14c04fb60fb6045ad74">SLUB: return ZERO_SIZE_PTR for kmalloc(0)</a></td><td> Path State/ RET</td></tr>
<tr><td><font size=+1><b>7: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/slub.c?id=00e962c5408b9f2d0bebd2308673fe982cb9a5fe">Revert "SLUB: Alternate fast paths using cmpxchg_local"</a></td><td>RET / FAU</td></tr>
<tr><td><font size=+1><b>13: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/memcontrol.c?id=81d39c20f5ee2437d71709beb82597e2a38efbbc">fix shrinking memory to return -EBUSY by fixing retry algorithm</a></td><td>RET / CON</td></tr>
<tr><td><font size=+1><b>18: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/page_alloc.c?id=945a11136ebdfa7fcce319ee6215958e84cb85f6">add gfp mask checking for __get_free_pages()</a></td><td>RET</td></tr>
<tr><td><font size=+1><b>19: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/memcontrol.c?id=4e649152cbaa1aedd01821d200ab9d597fe469e4">some modification to softlimit under hierarchical memory reclaim.</a></td><td>RET / ADS</td></tr>
<tr><td><font size=+1><b>21: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/slub.c?id=0f24f1287a86b198c1e4bd4ce45e8565e40ff804">tracing, slab: Define kmem_cache_alloc_notrace ifdef CONFIG_TRACING</a></td><td>RET / CON</td></tr>
<tr><td><font size=+1><b>25: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/memcontrol.c?id=93d5c9be1ddd57d4063ce463c9ac2be1e5ee14f1">fix prepare migration</a></td><td>RET / ADS</td></tr>
<tr><td><font size=+1><b>29: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/?id=ebb76ce16daf6908dc030dec1c00827d37129fe5&context=40&ignorews=0&dt=0">fix wrong VM_BUG_ON() in try_charge()'s mm->owner check</a></td><td>RET / CON</td></tr>
<tr><td><font size=+1><b>33: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/slub.c?id=b3d41885d9cd0d9db31c8f49e362bae02c96fa3f">slub: fix kmemcheck calls to match ksize() hints</a></td><td>RET</td></tr>
<tr><td><font size=+1><b>34: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/memcontrol.c?id=7ec99d6213b579a84c85ad37f2aa8ded4857c53c">unify charge/uncharge quantities to units of pages</a></td><td>RET / Path State</td></tr>
<tr><td><font size=+1><b>41: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/slub.c?id=8ba00bb68a067c221cc3ea3a0293e8fcbdcb7ba1">slub: consider pfmemalloc_match() in get_partial_node()</a></td><td>ADS / RET</td></tr>
<tr><td><font size=+1><b>43: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/slub.c?id=4d7868e6475d478172581828021bd8a356726679">slub: Do not dereference NULL pointer in node_match</a></td><td>RET / CON</td></tr>
<tr><td><font size=+1><b>47: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs/inode.c?id=261bca86ed4f7f391d1938167624e78da61dcc6b">nfsd/create race fixes, infrastructure</a></td><td>ADS / RET</td></tr>
<tr><td><font size=+1><b>49: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs/btrfs/file.c?id=580afd76e451deb6772d0507de580fb1df14da6c">Fix compressed checksum fsync log copies</a></td><td>ADS / RET</td></tr>
<tr><td><font size=+1><b>50: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs/btrfs/file.c?id=d397712bcc6a759a560fd247e6053ecae091f958">Fix checkpatch.pl warnings</a></td><td>RET</td></tr>
<tr><td><font size=+1><b>51: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs/btrfs/file.c?id=7237f1833601dcc435a64176c2c347ec4bd959f9">fix tree logs parallel sync</a></td><td>ADS / RET</td></tr>
<tr><td><font size=+1><b>52: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs/btrfs/file.c?id=2cfbd50b536c878e58ab3681c4e944fa3d99b415">check file pointer in btrfs_sync_file</a></td><td>ADS / RET</td></tr>
<tr><td><font size=+1><b>53: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs/btrfs/file.c?id=12fcfd22fe5bf4fe74710232098bc101af497995">tree logging unlink/rename fixes</a></td><td>FAU / RET</td></tr>
<tr><td><font size=+1><b>54: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs/btrfs/file.c?id=2ecb79239bcd04c9d410f4cdce16adb6840b19da">fix unprotected ->log_batch</a></td><td>ADS / RET / RACE</td></tr>
<tr><td><font size=+1><b>56: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs/btrfs/file.c?id=a0634be562c27ddee7c94bce4f765f8071244e07">don't leak transaction in btrfs_sync_file()</a></td><td>FAU / RET</td></tr>
<tr><td><font size=+1><b>57: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs/btrfs/file.c?id=0ef8b726075aa6931ddf1c16f5bae043eef184f9">return an error from btrfs_wait_ordered_range</a></td><td>RET</td></tr>
<tr><td><font size=+1><b>60: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs/btrfs/file.c?id=49dae1bc1c665817e434d01eefaa11967f618243">fix fsync data loss after a ranged fsync</a></td><td>ADS / RET</td></tr>
<tr><td><font size=+1><b>61: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs/btrfs/file.c?id=669249eea365dd32b793b58891c74281c0aac47e">fix fsync race leading to invalid data after log replay</a></td><td>RET / RACE</td></tr>
<tr><td><font size=+1><b>63: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs/btrfs/file.c?id=affc0ff902d539ebe9bba405d330410314f46e9f">fix race when checking if we can skip fsync'ing an inode</a></td><td>RET / RACE</td></tr>
<tr><td><font size=+1><b>67: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs/ubifs/file.c?id=f55aa59106b66cd547c8f296e0b3430ad76554c5">fix bug where page is marked uptodate when out of space</a></td><td>FAU / RET</td></tr>
<tr><td><font size=+1><b>69: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs/ubifs/file.c?id=6ed09c34b7984a978a73a855f4c2e6662acc8bdb">fix assertion warning and refine comments</a></td><td>FAU / RET</td></tr>
<tr><td><font size=+1><b>74: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/net/ipv4/tcp_input.c?id=9ae27e0adbf471c7a6b80102e38e1d5a346b3b38">tcp: Fix slab corruption with ipv6 and tcp6fuzz</a></td><td>CON / RET</td></tr>
<tr><td><font size=+1><b>75: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/net/ipv4/tcp_input.c?id=53240c208776d557dba9d7afedbcdbf512774c16">tcp: Fix possible double-ack w/ user dma</a></td><td>CON / RET / RACE</td></tr>
<tr><td><font size=+1><b>78: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/net/ipv4/tcp_input.c?id=aab2b4bf224ef8358d262f95b568b8ad0cecf0a0">tcp: fix double-counted receiver RTT when leaving receiver fast path</a></td><td>CON / RET</td></tr>
<tr><td><font size=+1><b>79: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/net/ipv4/tcp_input.c?id=c995ae2259ee36caf48bbfacf40111998dacd4af">tcp: Change return value of tcp_rcv_established()</a></td><td>RET</td></tr>
<tr><td><font size=+1><b>83: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/drivers/staging/rdma/hfi1?id=711e104ddca7b609889e1edf0a8482673ea4a7cc">staging/rdma/hfi1: fix panic in send engine</a></td><td>ADS / RET</td></tr>
<tr><td><font size=+1><b>84: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/drivers/infiniband/hw/hfi1?id=2aee309d3e01447c55fdf89cef05a0e2be372655">IB/hfi1: Fix deadlock with txreq allocation slow path</a></td><td>RET / RACE</td></tr>
<tr><td><font size=+1><b>88: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/drivers/scsi/scsi_debug.c?id=44d9269481bb43df445adf464b06ff031e67d7ea">[SCSI] scsi_debug: Thin provisioning support</a></td><td>RET</td></tr>
   </tbody>
 </table>

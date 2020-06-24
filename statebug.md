### Fast Path State Patches ###
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
<tr><td><font size=+1><b>2:</b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=d7365e783edb858279be1d03f61bc8d5d3383d90">fix missed end-writeback page accounting</a></td><td>Path State</td><td> The file unmap fast path is missing the function call to check if the page is still charged.</td><td> The bug is triggered at L2353 in page-writeback.c (test_clear_page_writeback), but the cause of the bug is extensive (throughout the uncharge and writeback functions)</td></tr>
<tr><td><font size=+1><b>3:</b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=eadb41ae82f802105c0601aa8a0a0e7595826497">prevent walking off the end of a pagetable in no-pmd configuration</a></td><td>Path State</td><td>  The fast path returns an incorrect range for configurations with folded pmd</td><td> L379 (__munlock_pagevec_fill)</td></tr>
<tr><td><font size=+1><b>6:</b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs?id=260a459d2e39761fbd39803497205ce1690bc7b1">Is mounted should be testing mnt_ns for NULL or error.</a></td><td>Path State</td><td>  Incorrect value is being checked in fast path</td><td> L74</td></tr>
<tr><td><font size=+1><b>14:</b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/drivers?id=bab6a9eac05360db25c81b0090f6b1195dd986cc">Fix setting initial MAC address</a></td><td>Path State</td><td> Incorrect fast path implementation created regression</td><td> L411</td></tr>
<tr><td><font size=+1><b>16:</b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/drivers?id=dc187cb381f1bceb30498861ece510245c43ed9f">Update firmware and version</a></td><td>Path State</td><td> Outdated context in fast path</td><td>  L56</td></tr>
<tr><td><font size=+1><b>20:</b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/net?id=dc327f8931cb9d66191f489eb9a852fc04530546">close another race condition in tcf_mirred_release()</a></td><td>Path State</td><td> Lock reduction creating race condition in fast path</td><td> Multiple</td></tr>
<tr><td><font size=+1><b>28:</b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/net?id=2519a602c273c5254781bc55b6e678a17e469a12">optimize tcf_match_indev()</a></td><td>Path State</td><td> Incorrect search method and potential inconsistency in fast path function call</td><td>  Multiple</td></tr>
<tr><td><font size=+1><b>29:</b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/net?id=ef209f15980360f6945873df3cd710c5f62f2a3e">fix access the unallocated memory in netprio cgroup</a></td><td>Path State</td><td>  Fixing out of bound accesses in fast path</td><td>  Multiple</td></tr>
<tr><td><font size=+1><b>36:</b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/net?id=2ad41065d9fe518759b695fc2640cf9c07261dd2">Clear stale pred_flags when snd_wnd changes</a></td><td>Path State</td><td>  Stale values in fast path</td><td> L2239 </td></tr>
   </tbody>
 </table>

### Patches Related to Fast Path State ###
<table>
 <thead>
     <tr>
     <td>Title</td>
     <td>Category</td>
    </tr>
    </thead>
   <tbody>
   <tr><td><font size=+1><b>2: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/slub.c?id=70d71228af9360cc4a0198ecd6351a1b34fa6d01">slub: remove object activities out of checking functions</a></td><td>CON / Path State</td></tr>
<tr><td><font size=+1><b>3: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/slub.c?id=272c1d21d6fe42979068e14c04fb60fb6045ad74">SLUB: return ZERO_SIZE_PTR for kmalloc(0)</a></td><td> Path State/ RET</td></tr>
<tr><td><font size=+1><b>4: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/slub.c?id=d07dbea46405b37d59495eb4de9d1056dcfb7c6d">Slab allocators: support __GFP_ZERO in all allocators</a></td><td>Path State</td></tr>
<tr><td><font size=+1><b>6: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/slub.c?id=7fd272550bd43cc1d7289ef0ab2fa50de137e767">Avoid double memclear() in SLOB/SLUB</a></td><td>Path State</td></tr>
<tr><td><font size=+1><b>8: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/slub.c?id=e72e9c23ee025a4c063ca112ba0a6059f9ecc9b7">Revert "SLUB: remove useless masking of GFP_ZERO"</a></td><td>Path State</td></tr>
<tr><td><font size=+1><b>10: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/slub.c?id=89124d706db0aa95daacfa4c0df45a43a44d44f4">slub: Add might_sleep_if() to slab_alloc()</a></td><td>Path State / CON</td></tr>
<tr><td><font size=+1><b>15: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/memcontrol.c?id=a8031cb00e286600ea08bd00a6812dbfec412376">remove warning when CONFIG_DEBUG_VM=n</a></td><td>Path State</td></tr>
<tr><td><font size=+1><b>16: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/memcontrol.c?id=46f7e602fb32e02145ef14f8c0ca6d399f0a96b9">fix build warning and avoid checking for mem != null again and again</a></td><td>Path State</td></tr>
<tr><td><font size=+1><b>17: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/slub.c?id=7e85ee0c1d15ca5f8bff0f514f158eba1742dd87">slab,slub: don't enable interrupts during early boot</a></td><td>Path State</td></tr>
<tr><td><font size=+1><b>26: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/memcontrol.c?id=747388d78a0ae768fd82b55c4ed38aa646a72364">fix css_is_ancestor() RCU locking</a></td><td>Path State/ CON</td></tr>
<tr><td><font size=+1><b>32: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/memcontrol.c?id=8dba474f034c322d96ada39cb20cac711d80dcb2">fix uninitialized variable use in mem_cgroup_move_parent()</a></td><td>Path State/ ADS</td></tr>
<tr><td><font size=+1><b>34: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/memcontrol.c?id=7ec99d6213b579a84c85ad37f2aa8ded4857c53c">unify charge/uncharge quantities to units of pages</a></td><td>RET / Path State</td></tr>
<tr><td><font size=+1><b>35: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/page_alloc.c?id=a197b59ae6e8bee56fcef37ea2482dc08414e2ac">fail GFP_DMA allocations when ZONE_DMA is not configured</a></td><td>Path State</td></tr>
<tr><td><font size=+1><b>36: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/slub.c?id=49a78d085fa6b44d6ed791923c7172a6433589c2">slub: remove no-longer used 'unlock_out' label</a></td><td>Path State</td></tr>
<tr><td><font size=+1><b>37: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/page_alloc.c?id=1fa7b6a29c61358cc2ca6f64cef4aa0e1a7ca74c">Revert "mm: fail GFP_DMA allocations when ZONE_DMA is not configured"</a></td><td>Path State</td></tr>
<tr><td><font size=+1><b>39: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/slub.c?id=73736e0387ba0e6d2b703407b4d26168d31516a7">slub: fix a possible memleak in __slab_alloc()</a></td><td>"Path State
/ CON / FAU"</td></tr>
<tr><td><font size=+1><b>40: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/?id=b121186ab1b12e2a96a945d88eae0735b4542158&context=40&ignorews=0&dt=0">correct page->pfmemalloc to fix deactivate_slab regression</a></td><td> Path State</td></tr>
<tr><td><font size=+1><b>42: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/page_alloc.c?id=d95ea5d18e699515468368415c93ed49b1a3221b">fix watermark checking</a></td><td> Path State</td></tr>
<tr><td><font size=+1><b>44: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/memcontrol.c?id=a0d8b00a3381f9d75764b3377590451cb0b4fe41">do not declare OOM from __GFP_NOFAIL allocations</a></td><td>CON /  Path State/ FAU</td></tr>
<tr><td><font size=+1><b>46: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/page_alloc.c?id=91fbdc0f89807bb97792ea6893717a8d3154b871">__alloc_pages_nodemask(): don't alter arg gfp_mask</a></td><td>ADS/ Path State</td></tr>
<tr><td><font size=+1><b>48: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs/inode.c?id=72a43d63cb51057393edfbcfc4596066205ad15d">ext3/4 with synchronous writes gets wedged by Postfix</a></td><td>ADS / Path State</td></tr>
<tr><td><font size=+1><b>65: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs/ubifs/file.c?id=7bbe5b5aa6d1e38af6f1fc866efc0aa461d73f19">use PAGE_CACHE_MASK correctly</a></td><td> Path State</td></tr>
<tr><td><font size=+1><b>66: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs/ubifs/file.c?id=54566b2c1594c2326a645a3551f9d989f7ba3c5e">symlink write_begin allocation context fix</a></td><td>ADS / Path State</td></tr>
<tr><td><font size=+1><b>70: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs/ubifs/file.c?id=09cbfeaf1a5a67bfb3201e0c83c810cecb2efa5a">get rid of PAGE_CACHE_* and page_cache_{get,release} macros</a></td><td>ADS / Path State</td></tr>
<tr><td><font size=+1><b>72: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/net/ipv4/tcp_input.c?id=55c97f3e990c1ff63957c64f6cb10711a09fd70e">[TCP]: Fix __tcp_push_pending_frames() 'nonagle' handling.</a></td><td> Path State</td></tr>
<tr><td><font size=+1><b>76: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/net/ipv4/tcp_input.c?id=59ea33a68a9083ac98515e4861c00e71efdc49a1">tcp: perform DMA to userspace only if there is a task waiting for it</a></td><td>CON /  Path State</td></tr>
<tr><td><font size=+1><b>80: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/net/ipv4/tcp_input.c?id=c10d9310edf5aa4a676991139d1a43ec7d87e56b">tcp: do not assume TCP code is non preemptible</a></td><td>CON / Path State</td></tr>
<tr><td><font size=+1><b>81: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/drivers?id=bab6a9eac05360db25c81b0090f6b1195dd986cc">Fix setting initial MAC address</a></td><td> Path State</td></tr>
<tr><td><font size=+1><b>85: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/drivers/net/ethernet/broadcom/bnx2x/bnx2x_cmn.c?id=e695a2dda1775dafc88174d2c0d71fab18db105a">bnx2x: dcb bit indices flags used as bits</a></td><td> Path State</td></tr>
<tr><td><font size=+1><b>86: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/drivers/net/ethernet/broadcom/bnx2x/bnx2x_cmn.c?id=a8f47eb701a562f6b5c81e2e0c143148915d7913">bnx2x: namespace and dead code cleanups</a></td><td> Path State / ADS</td></tr>
<tr><td><font size=+1><b>90: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/drivers/scsi/scsi_debug.c?id=c2248fc974df7be55a5f6db6b6f99a90b749581b">scsi_debug: change SCSI command parser to table driven</a></td><td> Path State</td></tr>
   </tbody>
 </table>

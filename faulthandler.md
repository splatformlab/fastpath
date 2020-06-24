### Fast Path Fault Handling Patches ###
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
<tr><td><font size=+1><b>7:</b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs?id=f55aa59106b66cd547c8f296e0b3430ad76554c5">fix bug where page is marked uptodate when out of space</a></td><td>FAU</td><td>  A page can be marked up to date in FP and then fail when there's not enough space, with no handler in slowpath.</td><td> Multiple</td></tr>
<tr><td><font size=+1><b>9:</b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/drivers?id=b0b477c7e0dd93f8916d106018ded1331b81bf61">use percpu 'repeat_count' and 'current_path'</a></td><td>FAU</td><td>  If this fast path fails while it is 'current_path', there is no fault handler.</td><td> Multiple</td></tr>
<tr><td><font size=+1><b>11:</b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/drivers?id=bc602280871cdedc906f622b036f5799f16c13c2">Move TxFIFO underrun handling to reset path</a></td><td>FAU</td><td>  Allow fault handling outside of the fast path</td><td> Optimization</td></tr>
<tr><td><font size=+1><b>12:</b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/drivers?id=2f6ae5cd24491647a011aead90d47523d875e443">only allow REQ_TYPE_FS to use fast path</a></td><td>FAU</td><td>  Missing fault handler for fast path failure</td><td>  L2330</td></tr>
<tr><td><font size=+1><b>13:</b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/drivers?id=c130480b129fbfd7932ad7af3f4ffcea630b027f">Fix se_cmd->state_list leak regression during WRITE failure</a></td><td>FAU</td><td> Failure during WRITE can spill over into fast path</td><td>  L2134</td></tr>
<tr><td><font size=+1><b>15:</b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/drivers?id=d4aeee776017b6da6dcd12f453cd82a3c951a0dc">Disable pagefaults along execbuffer relocation fast path</a></td><td>FAU</td><td>  A potential circular lock dependancy bug that is unhandled in fast path</td><td> L444</td></tr>
<tr><td><font size=+1><b>21:</b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/net?id=c2f34a65a61cd1ace3b53c93e8b38d2f79f4ff0d">fix potential NULL deref in __inet_inherit_port()</a></td><td>FAU</td><td>  Unhandled Race condition in fast path</td><td>  Multiple</td></tr>
<tr><td><font size=+1><b>23:</b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/net?id=76fecd8275be6de76513430e7526825944ab932f">In mpls_egress verify the packet length.</a></td><td>FAU/RET</td><td>  Failing to confirm byte presence in fast path</td><td> L92</td></tr>
<tr><td><font size=+1><b>34:</b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/net?id=5007392d8512e666107dc356d4c2e05627b9029b">FIX ipv6_forward sysctl restart</a></td><td>FAU</td><td>  Fault in fast path leaks to userspace</td><td> L503 addrconf.c</td></tr>
   </tbody>
 </table>

### Patches Related to Fast Path Fault Handling ###
<table>
 <thead>
     <tr>
     <td>Title</td>
     <td>Category</td>
    </tr>
    </thead>
   <tbody>
<tr><td><font size=+1><b>7: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/slub.c?id=00e962c5408b9f2d0bebd2308673fe982cb9a5fe">Revert "SLUB: Alternate fast paths using cmpxchg_local"</a></td><td>RET / FAU</td></tr>
<tr><td><font size=+1><b>9: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/slub.c?id=bdb21928512a860a60e6a24a849dc5b63cbaf96a">slub: Fix use-after-preempt of per-CPU data structure</a></td><td>ADS / FAU</td></tr>
<tr><td><font size=+1><b>11: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/memcontrol.c?id=7f4d454dee2e0bdd21bafd413d1c53e443a26540">avoid deadlock caused by race between oom and cpuset_attach</a></td><td>FAU</td></tr>
<tr><td><font size=+1><b>14: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/memcontrol.c?id=0b7f569e45bb6be142d87017030669a6a7d327a1">fix OOM killer under memcg</a></td><td>ADS / FAU</td></tr>
<tr><td><font size=+1><b>24: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/memcontrol.c?id=867578cbccb0893cc14fc29c670f7185809c90d6">fix oom kill behavior</a></td><td>FAU</td></tr>
<tr><td><font size=+1><b>38: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/slub.c?id=d6543e3935cec9f66b9647c24c2e44c68f8a91fd">slub: Enable backtrace for create/delete points</a></td><td>ADS / FAU</td></tr>
<tr><td><font size=+1><b>39: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/slub.c?id=73736e0387ba0e6d2b703407b4d26168d31516a7">slub: fix a possible memleak in __slab_alloc()</a></td><td>"Path State
/ CON / FAU"</td></tr>
<tr><td><font size=+1><b>44: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/memcontrol.c?id=a0d8b00a3381f9d75764b3377590451cb0b4fe41">do not declare OOM from __GFP_NOFAIL allocations</a></td><td>CON /  Path State/ FAU</td></tr>
<tr><td><font size=+1><b>45: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/mm/memcontrol.c?id=1f14c1ac19aa45118054b6d5425873c5c7fc23a1">do not allow task about to OOM kill to bypass the limit</a></td><td>FAU</td></tr>
<tr><td><font size=+1><b>53: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs/btrfs/file.c?id=12fcfd22fe5bf4fe74710232098bc101af497995">tree logging unlink/rename fixes</a></td><td>FAU / RET</td></tr>
<tr><td><font size=+1><b>56: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs/btrfs/file.c?id=a0634be562c27ddee7c94bce4f765f8071244e07">don't leak transaction in btrfs_sync_file()</a></td><td>FAU / RET</td></tr>
<tr><td><font size=+1><b>58: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs/btrfs/file.c?id=8b050d350c7846462a21e9e054c9154ede9b43cf">fix skipped error handle when log sync failed</a></td><td>FAU / ADS / CON</td></tr>
<tr><td><font size=+1><b>59: </b></font><a href="https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?h=v4.12-rc7&id=b05fd8742f6291b67571ad0fdad4da6b6eb98025">fix transaction leak during fsync call</a></td><td>FAU / CON</td></tr>
<tr><td><font size=+1><b>62: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs/btrfs/file.c?id=9dcbeed4d7e11e1dcf5e55475de3754f0855d1c2">fix signed overflows in btrfs_sync_file</a></td><td>FAU / CON</td></tr>
<tr><td><font size=+1><b>67: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs/ubifs/file.c?id=f55aa59106b66cd547c8f296e0b3430ad76554c5">fix bug where page is marked uptodate when out of space</a></td><td>FAU / RET</td></tr>
<tr><td><font size=+1><b>68: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs/ubifs/file.c?id=2680d722bf2c5f75225dd9acb3ec9e5a9e2652f4">introduce new flag for RO due to errors</a></td><td>ADS / FAU</td></tr>
<tr><td><font size=+1><b>69: </b></font><a href="https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/fs/ubifs/file.c?id=6ed09c34b7984a978a73a855f4c2e6662acc8bdb">fix assertion warning and refine comments</a></td><td>FAU / RET</td></tr>
<tr><td><font size=+1><b>71: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/net/ipv4/tcp_input.c?id=314324121f9b94b2ca657a494cf2b9cb0e4a28cc">[TCP]: Fix stretch ACK performance killer when doing ucopy.</a></td><td>ADS / FAU</td></tr>
<tr><td><font size=+1><b>82: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/drivers/staging/rdma/hfi1?id=50b19729ced72cfa8bb1c44fed9203f395f13991">IB/hfi1: checking for NULL instead of IS_ERR</a></td><td>FAU</td></tr>
<tr><td><font size=+1><b>87: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/drivers/scsi/scsi_debug.c?id=6f3cbf552e0557a463ad421f07b2e873a608406f">[SCSI] scsi_debug: error processing</a></td><td>FAU</td></tr>
<tr><td><font size=+1><b>89: </b></font><a href="http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/drivers/scsi/scsi_debug.c?id=18a4d0a22ed6c54b67af7718c305cd010f09ddf8">[SCSI] Handle disk devices which can not process medium access commands</a></td><td>FAU</td></tr>
   </tbody>
 </table>

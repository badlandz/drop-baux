# drop-baux — the lattice filesystem that pretends to be local

drop-baux is not NFS.  
drop-baux is not Ceph.  
drop-baux is not "yet another distributed filesystem that dies when one Pi loses Wi-Fi".

drop-baux is **SeaweedFS in disguise** — a global object store that mounts as a normal directory and survives anything.

When you `cd ~/drop-baux/project`:
- Your laptop sees the files
- The Pi Zero in the garage sees the same files
- The Arduino on the roof sees the same files
- If the garage Pi explodes, nothing happens — the data lives on the other nodes
- When it comes back, it just works again

No quorum. No locks. No tears.

### How it works (3 commands total)

On every node (Pi, laptop, server):
```bash
weed volume -dir=/drop-baux/vol -mserver=master.local:9333
weed filer -dir=/drop-baux/filer

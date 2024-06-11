# Tor relay tips

_This repository will try to help everyone running a Linux to start up and monitor your Tor relay._

## Let's prepare for running a Tor relay on Linux!

1. Prerequisite: Make sure you did not forcibly disable IPv6 by GRUB entry `ipv6.disable=1`, in which case Tor wouldn't start at all. I ran into this issue myself several times! 😀

2. **GRUB2** I suggest you change the following line if running a very fast SSD type like NVMe, but even SATA should do: `GRUB_CMDLINE_LINUX_DEFAULT="fsck.mode=force fsck.repair=yes rootflags=data=journal"` ie. that will ensure your file system integrity is checked upon every boot and the second part (`rootflags=`) is optional and would slow down disk writes, which is no problem running Tor in a virtual machine, it makes sure data is intact in case of a power outage for instance, sort to speak, tested only on `ext4`. If using good old HDD, I suggest the same if not on bare metal where you normally work on.

3. 

# Tor relay tips

_This repository will try to help everyone running a Linux to start up and monitor your Tor relay._

## Let's prepare for running a Tor relay on Linux!

1. **IPv6**: Make sure you did not forcibly disable IPv6 by GRUB entry `ipv6.disable=1`, in which case Tor wouldn't start at all. I ran into this issue myself several times! 😀

2. **GRUB2**: I suggest you change the following line if running a very fast SSD type like NVMe, but even SATA should do: `GRUB_CMDLINE_LINUX_DEFAULT="fsck.mode=force fsck.repair=yes rootflags=data=journal"` ie. that will ensure your file system integrity is checked upon every boot and the second part (`rootflags=`) is optional and would slow down disk writes, which is no problem running Tor in a virtual machine, it makes sure data is intact in case of a power outage for instance, sort to speak, tested only on `ext4`. If using good old HDD, I suggest the same if not on bare metal where you normally work on.

3. **Debian/Ubuntu** experience: I always ran Tor relays on the latest stable Debian GNU/Linux, but lately I decided to go into an Ubuntu-based OS like my always-running Linux Mint desktop, running multiple services. That does not mean this page is only related to such systems. On the contrary, I will try to post as much possible non-OS-related stuff.

4. **UPS**: An uninterruptible power supply is always preferable to just running on a laptop with a semi-dead battery. If running it on a non-battery computer like a regular server, ordinary PC, Raspberry Pi, or some routers even capable of it, choosing a sufficient _time to empty the UPS battery_ is of the essence.

# Tor relay tips (will sort them later)

_This repository will try to help everyone running a Linux to start up and monitor your Tor relay._

## Let's prepare for running a Tor relay on Linux!

- **IPv6**: Make sure you did not forcibly disable IPv6 by GRUB entry `ipv6.disable=1`, in which case Tor wouldn't start at all. I ran into this issue myself several times! 😀

- **GRUB2**: I suggest you change the following line if running a very fast SSD type like NVMe, but even SATA should do: `GRUB_CMDLINE_LINUX_DEFAULT="fsck.mode=force fsck.repair=yes rootflags=data=journal"` ie. that will ensure your file system integrity is checked upon every boot and the second part (`rootflags=`) is optional and would slow down disk writes, which is no problem running Tor in a virtual machine, it makes sure data is intact in case of a power outage for instance, sort to speak, tested only on `ext4`. If using a good old HDD, I suggest the same if not on bare metal where you normally work on.

- **Debian/Ubuntu** experience: I always ran Tor relays on the latest stable Debian GNU/Linux, but lately I decided to go into an Ubuntu-based OS like my always-running Linux Mint desktop, running multiple services. That does not mean this page is only related to such systems. On the contrary, I will try to post as much possible non-OS-related stuff.

- **UPS**: An uninterruptible power supply is always preferable to just running on a laptop with a semi-dead battery. If running it on a non-battery computer like a regular server, ordinary PC, Raspberry Pi, or some routers even capable of it, choosing a sufficient _time to empty the UPS battery_ is of the essence.

- **Unmetered Traffic**: A virtual private server may seem to be a logical choice for Tor relays. However, it is not easy to find one that is **cheap** and has a 100% unmetered network. Just do the math, if you did set say 3 MiB/s, then yearly traffic would make 3 (down) + 3 (up) simultaneously = 6 * day (24h * 3600s) = 518400 MiB per 1 day. You can go on like this, and multiply by a year => 518400 * 365 = 189216000 MiB which equals 180.45 TiB per year. Now, that is a traffic, which could make a regular ISP / VPS limit your relay. Make sure you do your research well and balance money vs. network properties. Not one time I ended up breaking with the VPS written / unwritten terms of service (unconsciously of course). In the end, it's almost all about traffic, therefore prioritize it over CPU, RAM, and other VPS properties.

- **Bridges, Non-Exit relays vs. Exit relays**: The list and details of bridges are not published almost anywhere; they help where _ordinary_ relays could not. Such places are all over the world where network censorship is strong. Also, your details are not published, and traffic can be limited. Exit relays are the complete opposite, your details are publicly visible and you may receive some letters for your relay which has for example played some role in say _prohibited doing_. I never ran an exit relay, be it on VPS or university or what is the worst idea... at my home, therefore please don't ask me on this topic. However, you may open an issue ticket, and we may chat about what it's like, and in the end, I might decide to publish your findings or some parts of it, anyway. The _Middle_ or Non-Exit relays are my main thing of interest. I ran some bridges too, but deleted them for low traffic, and supposedly low impact. I may be mistaken here, don't take me word by word.

- (More content coming in the following days, let me just quickly attach `nyx` monitoring tool snippet for you _to see_ something useful too.)

  ![nyx](https://github.com/burianvlastimil/tor-relay-tips/assets/14146682/2bca12ec-dcdb-4087-9b79-33087b4e8999)

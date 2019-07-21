# General Network Configuration

This section only applies if a network card is to be configured.

# Network Interface Configuration Files

Starting with version 209, systemd ships a network configuration daemon called **systemd-networkd** which can be used for basic network configuration. Additionally, since version 213, DNS name resolution can be handled by **systemd-resolved** in place of a static `/etc/resolv.conf` file. Both services are enabled by default.

Configuration files for **systemd-networkd** (and **systemd-resolved**) can be placed in `/usr/lib/systemd/network` or `/etc/systemd/network`. Files in `/etc/systemd/network` have a higher priority than the ones in `/usr/lib/systemd/network`. There are three types of configuration files: .link, .netdev and .network files. For detailed descriptions and example contents of these configuration files, consult the `systemd-link(5)`, `systemd-netdev(5)` and `systemd-network(5)` manual pages.

# Network Device Naming

Udev normally assigns network card interface names based on system physical characteristics such as enp2s1. If you are not sure what your interface name is, you can always run **ip link** after you have booted your system.

For most systems, there is only one network interface for each type of connection. For example, the classic interface name for a wired connection is eth0. A wireless connection will usually have the name wifi0 or wlan0.

If you prefer to use the classic or customized network interface names, there are three alternative ways to do that:

- Mask udev's .link file for the default policy:

  ```sh
  ln -s /dev/null /etc/systemd/network/99-default.link
  ```

- Create a manual naming scheme, for example by naming the interfaces something like "internet0", "dmz0", or "lan0". For that, create .link files in /etc/systemd/network/, that choose an explicit name or a better naming scheme for one, some, or all of your interfaces. For example:

  ```sh
  cat > /etc/systemd/network/10-ether0.link << "EOF"
  [Match]

  # Change the MAC address as appropriate for your network device

  MACAddress=12:34:45:78:90:AB

  [Link]
  Name=ether0
  EOF
  ```

    <p>

  See the man page systemd.link(5) for more information. <p>

- In `/boot/grub/grub.cfg`, pass the option net.ifnames=0 on the kernel command line.

# Static IP Configuration

The command below creates a basic configuration file for a Static IP setup (using both systemd-networkd and systemd-resolved):

```sh
cat > /etc/systemd/network/10-eth-static.network << "EOF"
[Match]
Name=<network-device-name>

[Network]
Address=192.168.0.2/24
Gateway=192.168.0.1
DNS=192.168.0.1
Domains=<Your Domain Name>
EOF
```

Multiple DNS entries can be added if you have more than one DNS server. Do not include DNS or Domains entries if you intend to use a static `/etc/resolv.conf` file.

# DHCP Configuration

The command below creates a basic configuration file for an IPv4 DHCP setup:

```sh
cat > /etc/systemd/network/10-eth-dhcp.network << "EOF"
[Match]
Name=<network-device-name>

[Network]
DHCP=ipv4

[DHCP]
UseDomains=true
EOF
```

# Creating the /etc/resolv.conf File

If the system is going to be connected to the Internet, it will need some means of Domain Name Service (DNS) name resolution to resolve Internet domain names to IP addresses, and vice versa. This is best achieved by placing the IP address of the DNS server, available from the ISP or network administrator, into `/etc/resolv.conf`.

# systemd-resolved Configuration

> **Note**
>
> > If using another means to configure your network interfaces (ex: ppp, network-manager, etc.), or if using any type of local resolver (ex: bind, dnsmasq, etc.), or any other software that generates an /etc/resolv.conf (ex: resolvconf), the systemd-resolved service should not be used.

When using **systemd-resolved** for DNS configuration, it creates the file `/run/systemd/resolve/resolv.conf`. Create a symlink in `/etc` to use the generated file:

# Static resolv.conf Configuration

If a static `/etc/resolv.conf` is desired, create it by running the following command:

```sh
cat > /etc/resolv.conf << "EOF"
# Begin /etc/resolv.conf

domain <Your Domain Name>
nameserver _<IP address of your primary nameserver>_
nameserver _<IP address of your secondary nameserver>_

# End /etc/resolv.conf
EOF
```

The domain statement can be omitted or replaced with a `search` statement. See the man page for resolv.conf for more details.

Replace `<IP address of the nameserver>` with the IP address of the DNS most appropriate for the setup. There will often be more than one entry (requirements demand secondary servers for fallback capability). If you only need or want one DNS server, remove the second _nameserver_ line from the file. The IP address may also be a router on the local network.

> **Note**
>
> > The Google Public IPv4 DNS addresses are _8.8.8.8_ and _8.8.4.4_ for IPv4, and _2001:4860:4860::8888_ and _2001:4860:4860::8844_ for IPv6.

# Configuring the system hostname

During the boot process, the file `/etc/hostname` is used for establishing the system's hostname.

Create the `/etc/hostname` file and enter a hostname by running:

```sh
echo "<lfs>" > /etc/hostname
```

_\<lfs>_ needs to be replaced with the name given to the computer. Do not enter the Fully Qualified Domain Name (FQDN) here. That information is put in the `/etc/hosts` file.

# Customizing the /etc/hosts File

Decide on a fully-qualified domain name (FQDN), and possible aliases for use in the `/etc/hosts` file. If using static addresses, you'll also need to decide on an IP address. The syntax for a hosts file entry is:

```sh
IP_address myhost.example.org aliases
```

Unless the computer is to be visible to the Internet (i.e., there is a registered domain and a valid block of assigned IP addresses—most users do not have this), make sure that the IP address is in the private network IP address range. Valid ranges are:

```sh
Private Network Address Range      Normal Prefix
10.0.0.1 - 10.255.255.254           8
172.x.0.1 - 172.x.255.254           16
192.168.y.1 - 192.168.y.254         24
```

x can be any number in the range 16-31. y can be any number in the range 0-255.

A valid private IP address could be 192.168.1.1. A valid FQDN for this IP could be lfs.example.org.

Even if not using a network card, a valid FQDN is still required. This is necessary for certain programs to operate correctly.

If using DHCP, DHCPv6, IPv6 Autoconfiguration, or if a network card is not going to be configured, create the `/etc/hosts`file by running the following command:

```sh
cat > /etc/hosts << "EOF"
# Begin /etc/hosts

127.0.0.1 localhost
127.0.1.1 _<FQDN>_ _<HOSTNAME>_
::1       localhost ip6-localhost ip6-loopback
ff02::1   ip6-allnodes
ff02::2   ip6-allrouters

# End /etc/hosts
EOF
```

The ::1 entry is the IPv6 counterpart of 127.0.0.1 and represents the IPv6 loopback interface. 127.0.1.1 is a loopback entry reserved specifically for the FQDN.

If using a static address, create the `/etc/hosts` file by running this command instead:

```sh
cat > /etc/hosts << "EOF"
# Begin /etc/hosts

127.0.0.1 localhost
127.0.1.1 _<FQDN>_ _<HOSTNAME>_
_<192.168.0.2>_ _<FQDN>_ _<HOSTNAME>_ [alias1] [alias2] ...
::1       localhost ip6-localhost ip6-loopback
ff02::1   ip6-allnodes
ff02::2   ip6-allrouters

# End /etc/hosts
EOF
```

The _\<192.168.0.2>_, _\<FQDN>_, and _\<HOSTNAME>_ values need to be changed for specific uses or requirements (if assigned an IP address by a network/system administrator and the machine will be connected to an existing network). The optional alias name(s) can be omitted.

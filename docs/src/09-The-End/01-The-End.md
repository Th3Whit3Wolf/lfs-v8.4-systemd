# The End

Well done! The new LFS system is installed! We wish you much success with your shiny new custom-built Linux system.

Create an `/etc/os-release` file required by systemd:

```sh
cat > /etc/os-release << "EOF"
NAME="Linux From Scratch"
VERSION="8.4-systemd"
ID=lfs
PRETTY_NAME="Linux From Scratch 8.4-systemd"
VERSION_CODENAME="<your name here>"
EOF
```

Creating the file `/etc/lfs-release` is recommended for compatibility with the non-systemd branch. By having this file, it is very easy for you (and for us if you need to ask for help at some point) to find out which LFS version is installed on the system. Create this file by running:

```sh
echo 8.4-systemd > /etc/lfs-release
```

It is also a good idea to create a file to show the status of your new system with respect to the Linux Standards Base (LSB). To create this file, run:

```sh
cat > /etc/lsb-release << "EOF"
DISTRIB_ID="Linux From Scratch"
DISTRIB_RELEASE="8.4-systemd"
DISTRIB_CODENAME="<your name here>"
DISTRIB_DESCRIPTION="Linux From Scratch"
EOF
```

Be sure to put some sort of customization for the field 'DISTRIB_CODENAME' to make the system uniquely yours.

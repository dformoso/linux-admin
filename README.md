# Linux Administration - Resource List
A summary of the architecture, setup, commands, and administration of a Linux system.

## Download
Download the mindmap PDF here:
- https://github.com/dformoso/linux-admin/blob/master/mindmap.pdf

## Linux Components
Get an idea of how a Linux system comes together. Here's a screenshot to show what the PDF looks like.

![alt text](https://github.com/dformoso/linux-admin/blob/master/images/linux.png)

## Linux Directories
A list of the base directories in Linux and their purpose, also in the mindmap.

![alt text](https://github.com/dformoso/linux-admin/blob/master/images/directories.png)

## vi Commands
Visually Represented.

![alt text](https://github.com/dformoso/linux-admin/blob/master/images/vi.png)

## Install Basic Packages

```shell
## BASE LIBRARIES ##
apt-get -y update
apt-get -y install openssh-server net-tools inetutils-traceroute wireless-tools htop lsof
apt-get -y install yum rpm quota xorg openbox ntpdate ntp postfix mutt cups xinetd cups-bsd rng-tools
```

## Important System Directories

```shell
## DIRECTORIES ##
cat      /etc/hostname                       # Instance's hostname
cat      /etc/nsswitch.conf                  # List of Databases: 'passwd', 'hosts', and sources for those DBs
cat      /etc/hosts                          # Mapping of hostnames to IP addresses
cat      /etc/hosts.allow                    # Allowed hostnames, processed first
cat      /etc/hosts.deny                     # Denied hostnames, processed second
cat      /etc/nologin                        # If exists, only root can login. Contents of file displayed
cat      /etc/passwd                         # DB of info on users, can include hashed passwords, or x
cat      /etc/shadow                         # DB of users and hashed passwords + password config
cat      /etc/group                          # DB of groups + users in groups, can include group passwords
cat      /etc/gshadow                        # DB of groups and hashed passwords + password config
ls       /etc/skel                           # Its contents will be copied to each new user's /home/ directory
cat      /etc/profile                        # Set system wide environmental variables on users shells
file     /bin/bash                           # Unix shell and command language
cat      /etc/bash.bashrc                    # System wide bash initialization file
cat      /etc/aliases                        # Aliases for sendmail. Not bash aliases
cat      ~/.profile                          # User specific shell initialization script/file.
cat      ~/.bashrc                           # Personal bash initialization file for interactive, non-login shells
cat      ~/.bash_profile                     # Personal bash initialization file login shells (console or ssh)
cat      ~/.bash_aliases                     # Personal bash aliases config, can also go bash_profile, or bashrc
cat      ~/.bash_login                       # Additional config executed right after login
cat      ~/.bash_logout                      # Additional config executed right after logout
cat      ~/.bash_history                     # Bash command history
cat      /etc/issue                          # Message or system identification to be printed before the login prompt
cat      /etc/os-release                     # Contains OS info
cat      /etc/crontab                        # Contains the crontab file jobs and scheduling
ls       /etc/cron.daily                     # Contains the crontab scripts to be run daily
cat      /etc/anacrontab                     # Contains the anacrontab file jobs and scheduling
cat      /etc/at.allow                       # Determines which user can submit commands for later execution via at or batch
cat      /etc/at.deny                        # Determines which user can submit commands for later execution via at or batch
cat      /etc/protocols                      # DB of TCP/IP protocols + protocol number + description
cat      /etc/services                       # DB of services and TCP/UDP ports used + description
cat      /etc/timezone                       # Stores configured timezone
cat      /etc/localtime                      # Stores configured localtime
cat      /etc/sudoers                        # Determines the groups and users sudo priviledges. Edit with visudo
ls       /etc/sudoers.d/                     # Ideal place to add sudoers
cat      /etc/ntp.conf                       # Configuration file for for ntpd
cat      /etc/inetd.conf                     # Configuration file for inetd. Edit requires service restart
cat      /etc/xinetd.conf                    # Configuration file for xinetd. Edit requires service restart
ls       /etc/xinetd.d/                      # Configuration files for each service managed by xinetd . Edit requires service restart
cat      /etc/initramfs-tools/initramfs.conf # Configuration file for initramfs
ls       /etc/udev                           # Device Manager - udev (systemd). Execute changes from kernel in /sys and /dev
cat      /etc/udev/udev.conf                 # udev configuration file.
file     /usr/sbin/logrotate                 # Log rotation utility
cat      /etc/logrotate.conf                 # Configuration file for logrotate
ls       /etc/logrotate.d                    # Configuration files for logrotate - system packages
cat      /etc/logrotate.d/rsyslog            # Configuration files for logrotate - system rsyslog
cat      /etc/rsyslog.conf                   # Configuration file for syslog
ls       /etc/rsyslog.d                      # Configuration files for services
cat      /etc/rsyslog.d/50-default.conf      # Default logging rules
cat      /etc/updatedb.conf                  # Config file read by updatedb before updating the locate database
cat      /etc/environment                    # Stores the PATH env variable
cat      /etc/fstab                          # Where should partitions should be mounted and how
ls       /etc/rc0.d                          # System-v runlevel initiation - halt
ls       /etc/rc6.d                          # System-v runlevel initiation - reboot
cat      /etc/init/dbus.conf                 # dbus config file
file     /sbin/upstart                       # Upstart initialization script
ls       /etc/init                           # Contains configuration files used by Upstart
file     /sbin/init                          # System-V initialization script
ls       /etc/init.d                         # Contains scripts used by the System V init tools
cat      /etc/init.d/networking              # System-v script for service
cat      /etc/init.d/cron                    # System-v script for service
cat      /etc/init.d/halt                    # System-v script for service
cat      /etc/init.d/dbus                    # System-v script for service
cat      /etc/init.d/functions               # Contains functions to be used by most or all shell scripts stored in the /etc/init.d directory
cat      /etc/inittab                        # describes how the INIT process should set up the system in a certain run-level (RedHat - Sys-V)
ls -lrt  /bin/systemd                        # Systemd initialization script symlink
file     /lib/systemd/systemd                # Systemd initialization script
ls -lrt  /etc/systemd/system/                # Contains symlinks to files in lib/systemd/system/
ls       /lib/systemd/system/*.target        # Contains init scripts
cat      /etc/systemd/journald.conf          # Configuration for the systemd journal logging service
cat      /etc/default/grub                   # GRUB config. Run 'update-grub' to update grub.cfg
ls       /etc/grub.d/                        # Additional files to configure the GRUB menu
cat      /boot/grub/menu.lst                 # GRUB menu list config file
cat      /boot/grub/grub.cfg                 # GRUB 2 menu list config file
cat      /etc/dhcp/dhclient.conf             # Configuration file for /sbin/dhclient - DHCP
cat      /etc/network/interfaces             # Network interface configuration information (Debian)
cat      /etc/sysconfig/network              # Network interface configuration information (RedHat)
cat      /etc/sysconfig/network-scripts      # Network interface configuration information (RedHat)
cat      /etc/ssh/sshd_config                # OpenSSH service configuration file
cat      /etc/cups/cupsd.conf                # Configuration file for the CUPS scheduler
ls       /usr/share/X11/xorg.conf.d/         # Xorg configuration file directory
cat      /etc/apt/sources.list               # Lists the 'sources' from which packages can be obtained
cat      /etc/yum.conf                       # Yum configuration file
ls       /etc/yum.repos.d                    # A list of directories where to look for .repo files
cat      /etc/ld.so.conf                     # Contains a list of directories in which to search for libraries for ldconfig
ls       /etc/ld.so.conf.d/                  # Directories in which to search for libraries for ldconfig, add new libs here, run ldconfig
ls       /lib                                # Library directory, also searched by ldconfig
ls       /usr/lib                            # Library directory, also searched by ldconfig
ls       /dev/sd*                            # SCSI drives
cat      /proc/1/status                      # Pseudo filesystem with info on running process
cat      /proc/1/io                          # Pseudo filesystem with info on running process
cat      /proc/1/syscall                     # Pseudo filesystem with info on running process
ls       /var/log                            # Main directory for log files
cat      /var/log/syslog                     # Syslog log files
cat      /var/log/mail.log                   # Mail log files - MTA
cat      ~/.forward                          # Email forwarding configuration
ls       ~/.ssh/                             # Root dir of ssh keys and config
cat      ~/.ssh/id_rsa                       # Example of ssh private key
cat      ~/.ssh/id_rsa.pub                   # Example of ssh public key
cp       ~/.ssh/authorized_keys              # Configures permanent access using SSH keys - copy .pub keys here
cat      /etc/ssh/ssh_known_hosts            # Systemwide list of known host keys.
cat      ~/.ssh/known_hosts                  # list of host keys for user not already in the systemwide list
```

## System Administration Commands

```shell
## COMMANDS ##
which ls                                     # Locate a command directory
whereis ls                                   # Locate the binary, source, and manual page files for a command
file /etc/passwd                             # Determine file type
type ls                                      # Display information about command type
who                                          # Show who is logged on
who -r                                       # Print current runlevel
w                                            # Show who is logged on and what they are doing
whoami                                       # Print effective userid
id                                           # Print real and effective user and group IDs
man                                          # An interface to the on-line reference manuals
info                                         # Read Info docum
shutdown                                     # Halt, power-off or reboot the machine
shutdown -c
shutdown -r now
uptime                                       # Tell how long the system has been running.
tzselect                                     # View and adjust timezones
timedatectl                                  # Control the system time and date
timedatectl set-time "2015-11-08 08:00:00"
timedatectl set-timezone "Asia/Kathmandu"
timedatectl set-ntp false
locale                                       # Get locale-specific information - LC_ALL
date                                         # Print or set the system date and time
date +%s                                     # Print or set the system date and time in UNIX epoch time
ntpd                                         # Network Time Protocol (NTP) daemon - auto update
ntpdate                                      # Set the date and time via NTP - manual update
ntpdate pool.ntp.org
hwclock                                      # Read or set the hardware clock (RTC)
hwclock --systohc --localtime
hwclock --systohc --utc
vmstat                                       # Reports information about processes, memory, paging, block IO, traps, disks and cpu activity
lscpu                                        # Display information about the CPU architecture
lspci                                        # List all PCI devices
lsusb                                        # List USB devices
free                                         # Display amount of free and used memory in the system
uname -r                                     # Print system information --kernel-release
uname -p                                     # Print system information --processor
uname -o                                     # Print system information --operating-system
dmesg                                        # Print or control the kernel ring buffer
lsmod                                        # Show the status of modules in the Linux Kernel
modprobe                                     # Add and remove modules from the Linux Kernel
rmmod                                        # Remove a module from the Linux Kernel
env                                          # Display all environment variables
export                                       # Display all environment variables
export ENV=/home/user                        # Create new environment variable
declare -r ENV=/home/user                    # Declare variables and give them attributes
crontab -e                                   # Edit crontab for current user
crontab -l                                   # List crontab for current user
export VISUAL=nano; crontab -e               # Set nano as default editor
at                                           # Queue jobs for later execution
atq                                          # Examine jobs for later execution
atrm                                         # Delete jobs
batch                                        # Executes commands when system load levels permit
ping                                         # Send ICMP ECHO_REQUEST to network hosts
ping6                                        # Send ICMP ECHO_REQUEST to network hosts IPv6
dig                                          # DNS lookup utility
nslookup                                     # Query Internet name servers interactively
traceroute                                   # Trace the route to a host
traceroute6                                  # Trace the route to a host IPv6
tracepath                                    # Traces path to a network host discovering MTU along this path
tracepath6                                   # Traces path to a network host discovering MTU along this path IPv6
service                                      # Run a System V init script
service --status-all                         # Display status of all System V managed services
service ssh start                            # Start System V service
service ssh stop                             # Stop System V service
service ssh status                           # Display status of System V service
service ssh restart                          # Restart System V service
systemctl                                    # Control the systemd system and service manager
systemctl list-units                         # List known units
systemctl status sound.target                # Show terse runtime status information about one or more units
systemctl stop   sound.target                # Stop (deactivate) one or more units
systemctl start  sound.target                # Start (activate) one or more units
systemctl enable multi-user.target           # Enable one or more unit files or unit file instances
systemctl set-default multi-user.target      # Set the default target to boot into.
systemctl set-default graphical.target       # Set the default target to boot into.
systemctl isolate multi-user.target          # Start the unit specified and stop all others
ifconfig -a                                  # Display all network interfaces, even if down
ifconfig eth0 up                             # Bring a network interface up
ifconfig eth0 down                           # Bring a network interface down
ifup                                         # Bring a network interface up
ifdown                                       # Take a network interface down
route                                        # Show / manipulate the IP routing table
route -n                                     # Show numerical addresses instead of trying to determine symbolic host names
route add <> netmask <> gw <>                # Add a new route with a netmask and a gateway
route del                                    # Delete a route
ip a, ip addr, ip address                    # Display network interface info
ip link                                      # Display link info
ip route show                                # Show Routing Table entries
ip route add <>/<> broadcast <> via <> eth0  # Add Routing Table entry
netstat -r                                   # Display the kernel routing tables
netstat -at                                  # Display listening and non-listening sockets
lsof                                         # List open files
lsof /tmp                                    # List open files
iptables -L                                  # List all NAT rules
iwlist ens33 auth                            # Get wireless information from a wireless interface
netcat -l 12345                              # Opens arbitrary TCP and UDP connections and listens
netcat 192.168.0.12 12345                    # Sends input to netcat location
nc -l 12345                                  # Same as netcat
nc 192.168.0.12 12345                        # Same as netcat
nmap localhost                               # Network exploration tool and security / port scanner
dpkg -l                                      # Package manager for Debian - list packages
dpkg -i                                      # Package manager for Debian - install package
dpkg --purge                                 # Purge an installed or removed package, removes everything including conffiles
dpkg-reconfigure                             # Reconfigure an already installed package
apt-get update                               # APT package handling utility - update packages from sources in /etc/apt/sources.list
apt-get dist-upgrade                         # upgrade + attempt to upgrade the most important packages at the expense of less important ones
apt-get install                              # Install package and dependencies from sources in /etc/apt/sources.list
apt-get remove                               # Remove package. Leave config files
apt-get purge                                # Remove package. Delete config files
apt-get autoremove                           # Remove packages that are no longer needed
apt-cache pkgnames                           # Prints the name of each package APT knows
apt-cache search                             # Text search on all available package lists
apt-cache depends                            # Shows a listing of each dependency a package has
aptitude                                     # Interface to the Debian GNU/Linux package system - APT
rpm -i                                       # RPM Package Manager - install package
rpm2cpio                                     # Extract cpio archive from RPM Package Manager (RPM) package
cpio -idmv                                   # Tool for creating and extracting archives
yum update                                   # Interactive, rpm based, package manager
yum install                                  # Install package and dependencies
yum install --downloadonly --downloaddir=/tmp # Download the package to directory but do not install
yum update                                   # Update packages from sources
yum remove                                   # Remove package
yumdownloader                                # Download RPM packages from Yum repositories
wget                                         # Utility for non-interactive download of files from the Web
ldconfig                                     # Creates links and cache to shared libraries found in /etc/ld.so.conf, /lib, and /usr/lib
ldconfig -p                                  # Lists of directories and candidate libraries stored in the current cache
ldd /bin/ls                                  # Prints the shared libraries required by the program
ps                                           # Snapshot of the current processes
ps -A                                        # Select all processes
ps -e                                        # Identical to -A
ps aux                                       # See every process on the system using standard syntax
top                                          # Dynamic real-time view of processes running on the system.
kill                                         # Send a signal to a process. Default  signal for kill is TERM
kill -SIGINT 78929
kill -SIGKILL 78929
pkill ping                                   # Send a signal to list of process matching a pattern
killall ping                                 # Kill processes by name
nice -12 large-job                           # Run a program with modified scheduling priority
renice -5 -p 1575                            # Alter priority of running processes
nohup <> &                                   # Run a command immune to hangups, with output to a non-tty. & runs in background
bg                                           # Make suspended command to execute in background
jobs                                         # List background jobs
fg                                           # Bring most recent job to the foreground
fg %1                                        # Bring a certain job to the foreground
kill %2                                      # Kill background job
tail -n 5 /var/log/syslog                    # Output the last 5 lines of file
tail -f /var/log/syslog                      # Output the last 10 lines of file and continue to display new events
grep                                         # Print lines matching a pattern
grep -E                                      # grep with --extended-regexp
egrep                                        # Same as grep -E
grep -F                                      # grep with --fixed-strings
fgrep                                        # Same as grep -F
rsync                                        # Remote (and local) file-copying tool
echo                                         # Display a line of text
echo -e                                      # echo + enable interpretation of backslash escapes
./                                           # Execute the content of the file passed as argument, in the current shell
source                                       # Execute the content of the file passed as argument, in the current shell
.                                            # Execute the content of the file passed as argument, in the current shell
chmod                                        # Change permissions for file or folder
chmod +x script.sh                           # Everyone gets execute permissions
chmod -R 754 myfiledir                       # Change permissions of folders and files recursively
chown -R daniel:group myfiledir              # Change user ownership of folders and files recursively
chgrp -R group myfiledir                     # Change group ownership of folders and files recursively
useradd                                      # Create a locked new user
useradd -u 1000 -g 500 daniel -G group dans  # Create a locked new user in a group
userdel --force --remove daniel              # Delete a user
usermod                                      # Modify a user account
usermod -L david                             # Lock a user's password
passwd                                       # Change a user's password
pwconv                                       # Convert and update user's passwords from passwd to shadow
grpconv                                      # Convert and update groups' passwords from passwd to shadow
groupadd                                     # Create a new group
groupdel                                     # Delete a group
groupmod                                     # Modify a group
gpasswd                                      # Modify a group's password
chage --list daniel                          # Show account aging information
chage -d 0 daniel                            # Force immediate password expiration
chage -E "2009-05-31" daniel                 # Set user password expiry information
umask                                        # Display umask - file permission mask for newly created files
umask -S                                     # Display umask in text
getent hosts                                 # Get entries from Name Service Switch libraries Databases
su = su root                                 # Change user ID or become superuser - overtake session
su daniel                                    # Change user ID or become superuser - overtake session
su - = su - root                             # Change user ID or become superuser - new session
su - daniel                                  # Change user ID or become superuser - new session
sudo su                                      # Using sudo to invoke su, so to use the sudo password
last                                         # Show a listing of last logged in users
wall                                         # Write a message to all users
visudo                                       # Edit the sudoers file
ulimit -a                                    # Show and change all system limits
ulimit -u                                    # Show and change system limits for max user processes
set                                          # Set or unset values of shell options and positional parameters
set -o noclobber                             # Prevent > from overwrite file
set -x                                       # Print commands and their arguments as they are executed
set +x                                       # Disable printing commands and their arguments as they are executed
cat                                          # Concatenate files and print on the standard output
cat -vet                                     # Convert tabs to spaces
expand                                       # Convert tabs to spaces
unexpand                                     # Convert spaces to tabs
wc                                           # Print newline, word, and byte counts for each file
fmt                                          # Reformat each paragraph in the file writing to standard output
pr                                           # Convert text files for printing
join                                         # Join lines of two files on a common field
paste                                        # Write lines from each file side by side, separated by TABs, to standard output
nl                                           # Number lines of files
>                                            # Redirects output to a file, overwriting the file
>>                                           # Redirects output to a file appending the redirected output at the end
<                                            # Feeds file (right) to command (left). sort < /etc/passwd
<<                                           # Feeds file from input until stop character (right) to command (left). sort << END
2>                                           # Redirects standard error to file
&>                                           # Redirects standard output and standard error to file
ls /tmp/hello > error.log 2>&1               # Redirects the standard error to the standard output, and both to file
2>&1                                         # Redirects the standard error to the standard output
logger                                       # Enter messages into the system log
tee                                          # Read from standard input and write to standard output and files
sort                                         # Sort lines of text files
sort -k 3                                    # Sort lines of text files by field
sort << END                                  # Sort lines of input string until keyword appears
tr -s ' ' < file.txt                         # Translate or delete characters. Squeeze repeats
tr -d 'to_remove' < file.txt                 # Delete character in set wherever found
sed -e s/Nick/John file.txt                  # Edit -replace as script input
sed 's/Nick/John/g' file.txt
cut -c3 names                                # Cut character vertically
cut -c3-10 names                             # Cut range of characters vertically
cut -d: -f1-2 names                          # Use delimited to separate into fields, and select specified fields
cut -f 1 -d " " names
cut -f 2 -d " " names
cut -f 2 -d " " names | paste names -
cut -f 2 -d " " names | paste names - | sort -k 3 | cut -f 1
uniq                                         # Report or omit repeated lines
split file.txt header_text_for_files         # Split a file into pieces
iconv -f utf-8 -t ISO_8895-15 < file1.txt > file2.txt # Convert text from one character encoding to another
xargs                                        # Build and execute command lines from standard input
ls name* | xargs paste
pwd                                          # Print name of current/working directory
ls                                           # List directory contents
ls -i                                        # + include inodes
ls -lrt                                      # + include reverse, long format, time ordering (modification)
la                                           # + include hidden . files
alias ls="ls -al"                            # Create an alias for a compound command
cd                                           # Change directory
mv                                           # Move (rename) files
cp                                           # Copy files and directories
rm                                           # Remove files or directories
scp                                          # Secure copy (remote file copy program)
scp -i                                       # + include private key
tar -zcvf to.tar.gz files_to_compress        # Archiving utility.  -z : Compress.   -c : Create.  -v : Verbose. -f : File to Save.
tar -zxvf to.tar.gz files_to_compress        # Archiving utility.  -z : Decompress. -x : Extract. -v : Verbose. -f : File to Save.
tar -cvf to.tar files_to_compress            #
gzip to.tar >> to.tar.gz                     # Compress files
gzip -d to.tar.gz >> to.tar                  # Expand files. -d: decompress
find . -name "protocols"                     # Search for files in current directory by name
find ./ -name "protocols"                    # Search for files in current directory by name
find / -name "protocols"                     # Search for files in / directory by name
find / -inum 129698                          # Search for files in / directory by inode number
find /etc -type f -mtime +30                 # Search for files by type and mod time by day-hour
find /etc -type f -size +1M                  # + add greater than for size
find /usr -type f -size -1M                  # + add less than for size
find /usr -maxdepth 2 -type f -size +1M      # + look up to two directies deep
find /var/log -mmin -60                      # + last modified n minutes ago
locate                                       # Find files/databases by name. Built by updatedb
updatedb                                     # Update a database for mlocate, locate command
ln file1 file2                               # Make hard link between files
ln -s                                        # Make soft link between files
df                                           # Report file system disk space usage
df -h                                        # + human readable sizes
df -T                                        # + partition type
du                                           # Estimate file space usage
du -h                                        # + human readable sizes
lsblk                                        # Info on block devices. Reads the sysfs filesystem and udev db
lsblk -f                                     # + filesystems
fdisk /dev/sda                               # Create disk partition table - MBR
fdisk -l /dev/sda                            # List disk partition table - MBR
gdisk /dev/sda                               # Create GUID partition table (GPT)
gdisk -l /dev/sda                            # List GUID partition table (GPT)
parted                                       # Create GUID partition table (GPT)
mkfs /dev/sdb1                               # Build a Linux filesystem on a hard disk partition
mkfs -t ext3 /dev/sdb1                       # + filesystem type
mkfs.ext3 /dev/sdb1                          # + dot notation. Recommended way to call mkfs
mkfs.xfs -f /dev/sdb1                        # + force overwrite
mount /dev/sdb1 /mnt/Photos                  # Mount a filesystem to the file tree
umount /mnt/Photos                           # Unmount a filesystem
mkswap /dev/sdb2                             # Sets up a Linux swap area on a device or in a file
swapon /dev/sdb2                             # Enable/disable devices and files for paging and swapping
swapoff /dev/sdb2                            # Enable/disable devices and files for paging and swapping
fsck /dev/sda1                               # Check and repair a Linux filesystem
e2fsck /dev/sda1                             # Check and repair a Linux ext2/ext3/ext4 file system
dumpe2fs -h /dev/sda1                        # Dump ext2/ext3/ext4 filesystem information + only display the superblock info
tune2fs -l /dev/sda1                         # List the contents of the filesystem superblock
tune2fs -L Photos /dev/sda1                  # Set the volume label of the filesystem
tune2fs -c 10 /dev/sda1                      # Adjust the number of mounts after which the filesystem will be checked by e2fsck
fuser /tmp                                   # Identify processes using files or sockets
/etc/fstab                                   # To configure quotas, edit and add usrquota and grpquota to filesystem, reboot
quotacheck -avug                             # Initial quota check on filesystem. Create a aquota file for user and group
quota -u daniel testuser                     # Display disk usage and limits for user
quota -g group testuser                      # Display disk usage and limits for group
edquota -u daniel                            # Edit user quotas
edquota -g group                             # Edit group quotas
repquota /mnt/Photos                         # Display disc usage and quotas for a filesystem
quotaon /mnt/Photos                          # Enable filesystem quotas
quotaoff /mnt/Photos                         # Disable filesystem quotas
dd if=/dev/sda of=bootloader.bak bs=446 count=1 # Copy and convert file. if - input file, of = output file, bs - bytes
xxd bootloader.bak                           # Make a hexdump or do the reverse
od                                           # Dump files in octal and other formats
grub-probe --version                         # Probe device information for GRUB
grub-probe --target=fs /boot/grub            #
grub-probe --target=drive --device /dev/sda  #
grub-install /dev/sda                        # Install GRUB to a device
grub-mkconfig -o /boot/grub/grub.cfg         # Generate a GRUB configuration file
update-grub                                  # Same as: grub-mkconfig -o /boot/grub/grub.cfg
init 3                                       # Change systemd runlevel to 3
telinit 3                                    # Change SysV runlevel to 3
screen -ls                                   # List available screens
screen -r 1499.screen_name                   # Reattach to a particular screen id
screen                                       # Create a new screen session with a default id
screen -S screen_name                        # Create a new screen session - Press CTRL-A + d to detach
apt-get -y install xorg                      # Install X11 - X Server Window system
startx                                       # Initialize an X session
apt-get -y install openbox                   # Install Extensible Window Manager
startx                                       # Initialize an X session with a Window Manager
apt-get -y install lightdm gnome             # Install Display Managers
export DISPLAY=:1                            # Export displays for us to connect to
xterm                                        # Open another terminal
xwininfo                                     # Get info about my screen
xdpyinfo                                     # Get technical info about x server
xhost +                                      # Allow anyone to connect to server
xhost -                                      # Allow only authorised clients to connect to server
journalctl -b -1                             # Query the systemd journal - Show messages from a specific boot
journalctl --since "2 days ago"              # Show messages from 2 days ago
mutt                                         # Text based program for reading and sending email
mail -s "Hello World" someone@example.com
mail -s "This is the subject" somebody@example.com <<< 'This is the message'
mailq                                        # List the mail queue
newaliases                                   # Initialize the alias database
lpq                                          # Show printer queue status
lpc                                          # Cancel Printer Job
lpr                                          # Print file
cupsenable printer_name                      # Stop/start printers and classes
cupsdisable printer_name                     # Stop/start printers and classes
ssh-keygen                                   # Generates, manages and converts authentication keys for ssh
chmod 700 ~/.ssh/                            # Permissions best practices for ssh keys
chmod 644 ~/.ssh/id_rsa.pub                  # Permissions best practices for ssh keys
chmod 600 ~/.ssh/id_rsa                      # Permissions best practices for ssh keys
eval `ssh-agent`                             # ssh-agent is a background program that handles passwords for SSH private keys
ssh-add                                      # Prompts the user for a private key password and adds it to the list maintained by ssh-agent
touch file1.txt                              # Creates file
rngd -r /dev/urandom                         # Creates some entropy to be able to use gpg
gpg --gen-key                                # Generate a new key pair using the current default parameters
gpg --gen-revoke your_email@address.com      # Generate a revocation certificate for the complete key
gpg --keyserver pgp.mit.edu --search-keys params # Set a preferred keyserver for the specified user ID, search for key
gpg --list-keys                              # List all keys from the public keyrings
gpg --encrypt --recipient user file1.txt     # Encrypt data
la -la text1.txt.gpg
gpg --decrypt file1.txt.gpg > file1.txt      # Decrypt data
```

## Important Environment Variables

```shell
## ENV VARIABLES ##
LD_LIBRARY_PATH      # LD_LIBRARY_PATH is an environment variable you set to give the run-time shared library loader (ld.so)
                     # an extra set of directories to look for when searching for shared libraries.
                     # This list is prepended to the existing list of compiled-in loader paths for a given executable, and any system default loader paths.
                     # For security reasons, LD_LIBRARY_PATH is ignored at runtime for executables that have their setuid or setgid bit set.
                     # This severely limits the usefulness of LD_LIBRARY_PATH.
HOME                 # Contains the path to the home directory of the current user
PATH                 # Contains a colon-separated list of directories in which your system looks for executable files
```

## Scripting Basics

```shell
## SCRIPTING ##
#!/bin/bash
if [ -f "$1" ]
then
    echo "$1 is a file"
else
    echo "$1 is not a file"
fi

if [ "$1" = "cool" ]
then
    echo "Cool Beans"
elif [ "$1" = "neat" ]
fi

if [ "$#" -gt 0 ]
then
    echo "There's Beans"
fi

for index in 1 2 3 4 5
do
    echo $index
done

for i in $(seq 1 100)
do
    echo $i
done

echo "Please enter your name"
read name
echo "Hello, $name. How are you?"

i = 0
while i != 10
do
    i = `expr i + 1`
done

echoFunction() {
  echo "echo is Called"
}
echoFunction;

echo $?
```



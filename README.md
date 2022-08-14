<div align="center">
  <img height="60" src="assets/img/linux.png">
  <h1>Linux Commands You Must</h1>
  
---

<span>
 </br>
I'll try to update these if needed, and if you'd like to contribute, you are free to do so.    
You can use this to learn commands, practice for interviews, or whatever you want to do. 
</span>
<br>
Feel free to contact me! <br />
<a href="https://www.twitter.com/DonUbwise"><img height="30" src="assets/img/twitter.png"></a> 
<a href="https://www.linkedin.com/in/ubongndoh"><img height="30" src="assets/img/linkedin.png"></a>

---

</div>

## Table of Contents

### 1. [Linux Network Commands](#network)

### 2. [Linux File Commands](#file)

### 3. [Linux Date Commands](#date)

### 4. [Linux Search Commands](#search)

### 5. [Linux Package Manager Commands](#pm)

### 6. [Linux User Commands](#user)

### 7. [Linux Process Management Commands](#ps)

### 8. [Linux Hardware Commands](#hardware)

### 9. [Linux Remote Commands](#remote)

### 10. [Linux File Permission Commands](#fp)

<hr/>

## Linux Network Commands <a id="network"></a>

<hr/>
### SSH
login into a remote Linux machine using SSH

```bash
### SSH
SSH username@ip-address or hostname
```

<hr/>
### dir

Display files in the current directory of a remote computer

### whois

Shows whois information about the given domain such as registrar info, registrant info, admin info if available.

```bash
## Displays available information of apple.com
whois apple.com
```

<hr/>

### ping

Sends ICMP packets to given address to check connectivity.

```bash
## Sends ICMP packets to google.com to check connectivity
ping google.com
```

<hr/>

### ifconfig

Shows IP addresses of all interfaces

```bash
ifconfig
```

<hr/>

### iwconfig

Shows wireless properties of the interfaces such as ESSID, Encryption keys.

```bash
iwconifg
```

<hr/>

### host

Performs IP lookup for the domain name or vice-versa.

```bash
## Displays IP address of apple.com
host apple.com

## Displays domain name of 17.253.144.10
host 17.253.144.10
```

<hr/>

### ss

Displays the information on all connections (TCP, UDP, unix Sockets). Previously accomplished by `netstat` command.

```bash
## Displays information on all connections
ss

## Only currently listening sockets
ss -l

## Displays UDP sockets
ss -u

## Displays TCP sockets
ss -t

## Displays Unix sockets
ss -x

## Displays TCP sockets that are listening. Works with -u and -x as well
ss -t -a
```

<hr/>

### wget

Download the file from a given source.

```bash
## Saves the index.html file of the google homepage
wget google.com

##Downloads the D5100 manual pdf at the given location
wget https://cdn-10.nikon-cdn.com/pdf/manuals/dslr/D5100_EN.pdf
```

<hr/>

### curl

Transfer data to or from a server using supported protocols like HTTP, FTP, SMTP, IMAP.

```bash
## displays content of the URL on the terminal
curl https://www.google.com

## download and saves the pdf in your local machine
curl -O https://cdn-10.nikon-cdn.com/pdf/manuals/dslr/D5100_EN.pdf

## download files from FTP servers. You don't need -u parameter if it's not authenticated.
curl -u <username>:<password> ftp://oshan.net/index.js

## display the definition of the word using DICT protocol. The following line displays the dictionary definition of 'aversion'
curl dict://dict.org/d:aversion
```

**EXTRA TIP**: You can view manual for `curl` using your terminal with `man curl` command.

<hr/>

## Linux File Commands <a id="file"></a>

<hr/>

### pwd

Displays the path of the current directory.

```bash
## Outputs the path of the directory you are in
pwd
```

<hr/>

### ls

Shows the content of your directory.

```bash
## Shows the content of current directory
ls

## Shows the content including . files or hidden files of current directory
ls -a

## Shows the content with permission and other details
ls -l

ls -al
```

<hr/>

### cd

Change your current directory to given path.

```bash
## Takes you to the downloads folder if there is one
cd Downloads

## Toggle between your last two working directories
cd -

## Takes you to the parent directory
cd ..

## Takes you to the HOME directory
cd
```

<hr/>

### mkdir

Create a new directory in a given filepath.

```bash
## Creates a directory named Projects in current directory
mkdir Projects
```

<hr/>

### rm

Delete a file or directory.

```bash
## Deletes the file.txt in working directory or specified path
rm file.txt

## Deletes the directory dir1 iff it's empty
rmdir dir1

## Deletes the directory dir1 along with its contents
rm -r dir1
```

<hr/>

### mv

Move file/directory from one place to other. You can also use this to rename files.

```bash
## Move file.txt to directory dir1
mv file.txt dir1

## Rename file.txt to index.txt
mv file.txt index.txt

## Move directory dir1 to directory dir2
mv dir1 dir2

## To avoid overwriting index.txt if it already exists
mv -n file.txt index.txt
```

You can also move multiple files such as `mv file1 file2 file3 dir`.

<hr/>

### cp

Copy file/directory from one place to another.  
Basic format:

```bash
cp [Options] sourceFile/Dir destinationFile/Dir
```

```bash
## Copies file.txt to dir1
cp file.txt dir1

## Copies directory dir1 to dir2 along with the contents
cp -R dir1 dir2

## Copies content of file.txt to file2.txt. You can use -i or -b or -f options according to your requirement. -i asks for confirmation if the file needs to be overwritten. -b creates a backup before overwriting file. -f forces the overwriting without any warning/backup.
cp file.txt file2.txt
```

You can also move multiple files such as `cp file1 file2 file3 dir`.

<hr/>

### touch

Create or update a file on a specified path.

```bash
## Creates file file1.txt in the current director
touch file1.txt

## Creates multiple files file1.txt and index.js in the current working directory
touch file1.txt index.js
```

<hr/>

### cat

1. Displays the content of the file
2. Create a new file
3. Copy the content of one file to other
4. Merge files

```bash
## Display the content of file.txt
cat file.txt

## Create a file with the text "This is the first line"
cat > file2.txt
This is the first line.

## Copy the content of file2.txt to file.txt
cat file2.txt > file.txt

## Append "This is the second line" in the existing file file2.txt
cat >> file2.txt
This is the second line.

## Merge contents of file1 and file2 as merged_file
cat file1.txt file2.txt > merged_file.txt
```

<hr/>

### head/tail

Displays the first 10 lines of file or last 10 lines of file. Helps when you are viewing a large file.

```bash
## Displays the first 10 lines of file.txt
head file.txt

## Displays the last 10 lines of file.txt
tail file.txt
```

<hr/>

## Linux Date Commands <a id="date"></a>

<hr/>

### date

Displays date and time of the system.

```bash
## Displays date and time of the system
date

## Displays date and time of 5 days ago
date --date="5 days ago"

## Similarly, displays date and time of 10 seconds ago
date --date="10 seconds ago"
```

<hr/>

### cal

Displays calendar.

```bash
## Displays the current month with day highlighted
cal

## Displays the third month of 1997
cal 03 1997
```

<hr/>

## Linux Search Commands <a id="search"></a>

<hr/>

### grep

Search for pattern in given file.

```bash
## Searches and displays lines containing string "linux" in file.txt
grep "linux" file.txt

## Searches and displays lines containing string "linux" in files in directory dir
grep -r "linux" dir

## Searches for the exact word "linux" in file.txt
grep -w "linux" file.txt

## Ignores the case while searching
grep -i "linux" file.txt
```

<hr/>

### find

Searches for files in given directory with given criteria.  
Generally the pattern is:

```bash
find [starting_directory] [criteria]
```

```bash
## displays the path of all files in the current directory
find .

## displays the path of files with name "index.js" in current directory
find . -name index.js

## displays the path of files greater than 500kb in size
find . -size +500k
```

You can use +/- with `-atime` or `-mtime` to get the files with last accessed time or modified time.  
You can also execute commands on the result with `-exec` command or with prompt using `-ok` command.

```bash
## finds the file named index.js and delete it after displaying prompt
find . -name index.js -ok rm {} \;
```

<hr/>

## Package Manager Commands <a id="pm"></a>

<hr/>

### rpm

Manages rpm packages.

```bash
## Install package named "oshan.rpm"
rpm -ivh oshan.rpm

## Update if the package is already installed "oshan.rpm"
rpm -Uvh oshan.rpm

## Remove package named "oshan.rpm"
rpm -e oshan.rpm

## Verify package named "oshan.rpm"
rpm -V oshan.rpm

## List all the RPM packages
rpm -qa
```

Generally, most of the distros use their own package manager, and it's prefereable to use package manager like `yum` or `dnf` instead of rpm because it handles all the dependencies.  
I use OpenSUSE, and I have `zypper` as my package manager.

`apt` is used commonly for Debian family systems to handle dpkg.

<hr/>

## User Commands <a id="user"></a>

<hr/>

### useradd

Add new users. (needs superuser privileges)

```bash
## Add new user named friends
sudo useradd friends

## Set password for friends
sudo passwd friends

## Specify userid 3001, group as users while adding user
sudo useradd -u 3001 -g users oshan

## Create user with expiry date as 2021-02-30
sudo useradd -e 2021-02-30 oshan

## Check Account/Password expiry dates for oshan
sudo chage -l oshan
```

<hr/>

### userdel

Delete users. (need superuser privileges)

```bash
## Delete user named friends
sudo userdel friends

## Delete user friends and it's home directory
sudo userdel -r friends
```

### last

Displays the last logins on the system.  
**Tips:**
If you want to check if anyone is using your computer when you are not home this is the command you need.

```bash
#Outputs the info on last logins
last
```

**Similar commands:**

```bash
## Shows the active user id and group id
id

## Shows the username and login time of active user
who
```

<hr/>

## Process Management Commands <a id="ps"></a>

<hr/>

### ps

Displays process status.

```bash
## returns all the process running under the current user
ps ux

## returns the status of process with process ID 5266
ps 5266
```

<hr/>

### top

Displays in real time all the running process along with CPU usage, Memory usage, Priority, CPU time.

```bash
## You can press q to exit from the display
top
```

<hr/>

### kill

kills the process with given process ID

```bash
## Terminates the process with PID 5766
kill 5766

## Kills all process named code
killall code
```

<hr/>

### pidof

returns the Process ID of given process name

```bash
## returns the process ID of process name code
pidof code

## returns the process ID of process name containing code. Here code is the pattern instead of process name.
pgrep code
```

<hr/>

### pkill

kills the process with the process name of the given pattern

```bash
## kills all the processes whose names has pattern code
pkill code
```

<hr/>

### jobs

returns the list of background jobs

```bash
## returns the background jobs with status
jobs

## send stopped processes to background jobs
bg

## bring the background job code to foreground
fg code
```

<hr/>

### free

returns the memory status (RAM)

```bash
## Outputs the memory status in kilobytes
free

## Outputs the memory status in gigabytes or you can use -m for megabyte, -b for byte
free -g
```

<hr/>

## Hardware Commands <a id="hardware"></a>

<hr/>

### lsusb

Lists USB buses and the devices connected to them.

```bash
## Displays USB buses and the devices connected
lsusb

## Displays detailed information about USB buses and connected devices
lsusb -v
```

<hr/>

### lspci

Lists PCI buses and the devices connected ot them. You might need root privileges to run this command.

```bash
## Displays PCI buses and the devices connected
lspci

## Displays detailed information of PCI buses. The amount of details increase with the number of v in the options
lspci -v
lspci -vv
lspci -vvv
```

<hr/>

### lshw

Lists the hardware configuration of the machine. Device information, Motherboarad configuration, CPU version, Memory configuration, etc. You might need root privileges to run this command.

```bash
## Displays the hardware configuration of the machine
lshw

## Displays the information in html format with tree structure
lshw -html
```

**EXTRA TIPS**: `lshw -html > index.html` to save the output as index.html and view it in your browser.

<hr/>

### lsblk

Lists the information about block devices.

```bash
## Lists the block devices
lsblk
```

Using different options you can modify your result. Some of the useful ones are:  
`lsblk -all` list all devices including empty ones  
`lsblk -O` list all devices with all the availables columns  
`lsblk -o ColumnName` list devices with given column information

<hr/>

### fdisk

List out partition information and lets you modify it as well. You might need root privileges to run this command.

```bash
## List the partition and their sizes, number of sectors
fdisk -l

## lets you create/delete partition or other commands in given disk
fdisk /dev/sdb1
```

<hr/>

### dmidecode

List hardware information from the BIOS. You might need root privileges to run this command.

```bash
## List the hardware information from the BIOS
dmidecode

## List the hardware information with little detail only. It's more readable.
dmidecode -q
```

<hr/>

### dmesg

List detected hardware and boot messages.

```bash
## List the boot messages with detected hardware
dmesg

## List the messages in human readable format
dmesg -H

## Read the information and clear it
dmesg -c
```

**EXTRA TIP**: `dmesg -H > file.txt` saves the output in file.txt.

<hr/>

### badblocks

Used to check for badblocks in disk partition. You might need root privileges to run this command.

```bash
## Check for bad blocks in partition /dev/sda with progress of the scan. -s parameter is optional.
badblocks -s /dev/sda
```

**EXTRA TIP**: `badblocks -s /dev/sda -o file.txt` saves the list of badblocks found in file.txt.

<hr/>

### hdparms

Get/Set hard disk parameters.

```bash
## Check hard disk drive speed. I got 999.36 MB/sec
hdparm -t /dev/sda1

## Check hard disk cache read speed. I got 6458.49 MB/sec
hdparm -T /dev/sda1

## you can see all other things you can do with this command
hdparm -h
```

<hr/>

## Linux Remote Commands <a id="remote"></a>

<hr/>

### ssh (Secure Shell)

SSH lets you connect remote systems and enables secured transfer of files over insecure networks. It is used widely over its predecessors `telnet` which isn't as secured as SSH, and there are possible problems like eavesdropping.

```bash
## Install ssh server (On debian systems )
sudo apt-get install openssh-server

## Install ssh server on OpenSUSE or you can use your Package Manager
sudo zypper install openssh-server

## Start ssh server
sudo service ssh start

## Check ssh server status
sudo service ssh status

## Connect to remote server
ssh <username>@<host_ip_address>

## Connect to host using specific port
ssh -p <port> <username>@<host_ip_address>
```

<hr/>

### telnet

Telnet is a client-server protocol based on TCP connections. It dates back to almost 50 years ago. SSH is preferred over, but still it doesn't hurt to learn about this as it is still in use.

```bash
## Install ssh server (On debian systems )
sudo apt-get install openssh-server

## Install ssh server on OpenSUSE or you can use your Package Manager
sudo zypper install openssh-server

## start the connection setup
telnet <hostname>

## start using IP address and port number
telnet <IP_ADDRESS> <PORT>
```

<hr/>

## Linux File Permission Commands <a id="fp"></a>

<hr/>

### chmod

Change the file access rights. The permission is expressed in **three sets** of **three characters** to denote permission for file owner, group owner, and all other users.

For files:
| rwx | rwx | rwx |  
| --- | --- | --- |
|Read, write, and execute permission for file owner | Read, write and execute permission for group owner | Read, write, and execute permission for all other users

Here, we will use _octal notation_ to make changes to file permissions.

```
rwx rwx rwx 111 111 111
--- --- --- 000 000 000
rw- rw- rw- 110 110 110

111 => 7
110 => 6
101 => 5
100 => 4
011 => 3
010 => 2
001 => 1
000 => 0
```

So, it's easy to give permission using octal notation to files.

```bash
## Give read, write, and execution permission to everybody
chmod 777 index.js

## Give read, write, and execution permission to nobody
chmod 000 index.js

## Give all permission to directory owner and no permission to anybody else
chmod 700 dir
```

<hr/>

### sudo

Get superuser (root) privileges temporarily. You need to enter root password for that. There are some commands that need superuser privileges because the file containing them don't have permission for other users.

```bash
sudo fdisk -l
```

<hr/>

### chown

Change ownership of files. You need sudo privileges for executing this command.

```bash
## Change ownership of index.js from user to root
sudo chown root index.js
```

<hr/>

### chgrp

Change group owner of file. You need sudo privileges for executing this command.

```bash
## Change group ownership of index.js from user to root
sudo chgrp root index.js
```

<hr/>

# Linux Q & A

## Linux 101

**_1.What is Linux?_**
  
- Wikipedia: "Linux is a family of open-source Unix-like operating systems based on the Linux kernel, an operating system kernel first released on September 17, 1991, by Linus Torvalds. Linux is typically packaged in a Linux distribution."

- Red Hat: "Linux® is an open source operating system (OS). An operating system is the software that directly manages a system’s hardware and resources, like CPU, memory, and storage. The OS sits between applications and hardware and makes the connections between all of your software and the physical resources that do the work."

**_2.Explain what each of the following commands does and give an example on how to use it:_**

- touch - update file's timestamp. More commonly used for creating files
- ls - listing files and directories
- rm - remove files and directories
- cat - create, view and concatenate files
- cp - copy files and directories
- mkdir - create directories
- pwd - print current working directory (= at what path the user currently located)
- cd - change directory

**_3.What each of the following commands does?_**

- cd /  --> change to the root directory
- cd ~  --> change to your home directory
- cd    --> change to your home directory
- cd .. --> change to the directory above your current i.e parent directory
- cd .  --> change to the directory you currently in
- cd -  --> change to the last visited path

**_4.Some of the commands in the previous question can be run with the -r/-R flag. What does it do? Give an example to when you would use it_**

- The -r (or -R in some commands) flag allows the user to run a certain command recursively. For example, listing all the files under the following tree is possible when done recursively (`ls -R`):

- /dir1/ dir2/ file1 file2 dir3/ file3

-  To list all the files, one can run `ls -R /dir1`

**_5.Explain each field in the output of `ls -l` command_**

- It shows a detailed list of files in a long format. From the left:
  - file permissions, number of links, owner name, owner group, file size, timestamp of last modification and directory/file name
 
**_6.What are hidden files/directories? How to list them?_**

- These are files directly not displayed after performing a standard ls direct listing. An example of these files are .bashrc which are used to execute some scripts. Some also store configuration about services on your host like .KUBECONFIG. The command used to list them is, `ls -a`

**_7.What do > and < do in terms of input and output for programs?_**

- They take in input (<) and output for a given file (>) using stdin and stdout.
  - `myProgram < input.txt > executionOutput.txt`
 
**_8.Explain what each of the following commands does and give an example on how to use it:_**

- sed: a stream editor. Can be used for various purposes like replacing a word in a file:
  - `sed -i s/salad/burger/g`

- grep: a search tool. Used to search, count or match a text in a file:
  - searching for any line that contains a word in a file: `grep 'word' file.md`
  - or displaying the total number of times a string appears in a file: `grep -c 'This is a string' file.md`
 
- cut: a tool for cutting out selected portions of each line of a file:
  - syntax: `cut OPTION [FILE]`
    -  cutting first two bytes from a word in a file: `cut -b 1-2 file.md`, output: `wo`
   
- awk: a programming language that is mainly used for text processing and data extraction. It can be used to manipulate and modify text in a file:
  - syntax: `awk [OPTIONS] [FILTER] [FILE]` extracting a specific field from a CSV file: `awk -F ',' '{print $1}' file.csv`, output: `first field of each line in the file`
 
**_9.How to rename the name of a file or a directory?_**

- Using the `mv` command.

**_10.Specify which command would you use (and how) for each of the following scenarios_**

- `rm -rf dir` --> Remove a directory with files
- `cat or less` --> Display the content of a file
- `chmod 777 /tmp/x` --> Provides access to the file /tmp/x for everyone
- `cd ~` --> Change working directory to user home directory
- `sed -i s/good/great/g /tmp/y` --> Replace every occurrence of the word "good" with "great" in the file /tmp/y

**_11.How can you check what is the path of a certain command?_**

- `whereis`
- `which`

**_12. What is the difference between these two commands? Will it result in the same output?_**
- `echo hello world`
- `echo "hello world"`

- The echo command receives two separate arguments in the first execution and in the second execution it gets one argument which is the string "hello world". The output will be the same.

**_13.Explain piping. How do you perform piping?_**

- Using a pipe in Linux, allows you to send the output of one command to the input of another command. For example: `cat /etc/services | wc -l`

**_14.Fix the following commands:_**
- sed "s/1/2/g' /tmp/myFile --> `sed 's/1/2/g' /tmp/myFile  # sed "s/1/2/g" is also fine`
- find . -iname *.yaml -exec sed -i "s/1/2/g" {} ; --> `find . -iname "*.yaml" -exec sed -i "s/1/2/g" {} \;`

**_15.How to check which commands you executed in the past?_**

- history command or .bash_history file
  - also can use up arrow key to access or to show the recent commands you type
 
**_16.Running the command `df` you get "command not found". What could be wrong and how to fix it?_**

- Most likely the default/generated $PATH was somehow modified or overridden thus not containing `/bin/` where df would normally go. This issue could also happen if bash_profile or any configuration file of your interpreter was wrongly modified, causing erratics behaviours. You would solve this by fixing your $PATH variable:

- As to fix it there are several options:
  1. Manually adding what you need to your $PATH PATH="$PATH":/user/bin:/..etc
  2. You have your weird env variables backed up.
  3. You would look for your distro default $PATH variable, copy paste using method #1

- Note: There are many ways of getting errors like this: if bash_profile or any configuration file of your interpreter was wrongly modified; causing erratics behaviours, permissions issues, bad compiled software (if you compiled it by yourself)... there is no answer that will be true 100% of the time.

**_17.How do you schedule tasks periodically?_**

- You can use the commands `cron` and `at`. With cron, tasks are scheduled using the following format:

- `*/30 * * * * bash myscript.sh` Executes the script every 30 minutes.

- The tasks are stored in a cron file, you can write in it using `crontab -e`

- Alternatively if you are using a distro with systemd it's recommended to use systemd timers.

## I/O Redirection

**_18.Explain Linux I/O redirection_**

- In Linux, IO redirection is a way of changing the default input/output behavior of a command or program. It allows you to redirect input and output from/to different sources/destinations, such as files, devices, and other commands.

- Here are some common examples of IO redirection:
  - Redirecting Standard Output (stdout): `ls > filelist.txt`
  - Redirection Standard Error (stderr): `ls /some/nonexistent/directory 2> error.txt`
  - Appending to a file: `echo "hello" >> myfile.txt`
  - Redirecting Input (stdin): `sort < unsorted.txt`
  - Using Pipes: Pipes ("|"): `ls | grep ".txt$"`

**_19.Demonstrate Linux output redirection_**

- `ls > ls_output.txt`
 
**_20.Demonstrate Linux stderr output redirection_**

- `yippiekaiyay 2> ls_output.txt`
 
**_21.Demonstrate Linux stderr to stdout redirection_**

- `yippiekaiyay &> file`
 
**_22.What is the result of running the following command? `yippiekaiyay 1>&2 die_hard`_**

- An output similar to: `yippikaiyay: command not found...`
- The file `die_hard` will not be created


## Filesystem Hierarchy Standard

**_23.In Linux FHS (Filesystem Hierarchy Standard) what is the `/`?_**

- The root of the filesystem. The beginning of the tree.

**_24.What is stored in each of the following paths?_**

- `/bin, /sbin, /usr/bin and /usr/sbin` -> binaries
- `/etc` -> configuration files
- `/home` -> home directories of the different users
- `/var` -> files that tend to change and be modified like logs
- `/tmp` -> temporary files

**_25.What is special about the /tmp directory when compared to other directories?_**

- `/tmp` folder is cleaned automatically, usually upon reboot.

**_26.What kind of information one can find in /proc?_**

- It contains useful information about the processes that are currently running, it is regarded as control and information center for kernel.

**_27.What makes /proc different from other filesystems?_**

- `/proc` is a special virtual filesystem in Unix-like operating systems, including Linux, that provides information about processes and system resources.

**_28.True or False? only root can create files in /proc_**

- False. No one can create file in `/proc` directly (certain operations can lead to files being created in /proc by the kernel).

**_29.What can be found in /proc/cmdline?_**

- The command passed to the boot loader to run the kernel

**_30.In which path can you find the system devices (e.g. block storage)?_**

- `/dev`

## Permissions

**_31.How to change the permissions of a file?_**

- Using the `chmod` command.

**_32.What does the following permissions mean?:_**

- `777` -> You give the owner, group and other: Execute (1), Write (2) and Read (4); 4+2+1 = 7.
- `644` -> Owner has Read (4), Write (2), 4+2 = 6; Group and Other have Read (4).
- `750` -> Owner has x+r+w, Group has Read (4) and Execute (1); 4+1 = 5. Other have no permissions.

**_33.What this command does? `chmod +x some_file`_**

- It adds execute permissions to all sets i.e user, group and others.

**_34.Explain what is setgid and setuid_**

- `setuid` is a linux file permission that permits a user to run a file or program with the permissions of the owner of that file. This is possible by elevation of current user privileges.

- `setgid` is a process when executed will run as the group that owns the file.

**_35.What is the purpose of sticky bit?_**

- Its a bit that only allows the owner or the root user to delete or modify the file.

**_36.What the following commands do?_**

- `chmod` - changes access permissions to files system objects
- `chown` - changes the owner of file system files and directories
- `chgrp` - changes the group associated with a file system object

**_37.What is sudo? How do you set it up?_**

- sudo is a command-line utility in Unix-like operating systems that allows users to run programs with the privileges of another user, usually the superuser (root). It stands for "superuser do.

- The sudo program is installed by default in almost all Linux distributions. If you need to install sudo in Debian/Ubuntu, use the command apt-get install sudo

**_38.True or False? In order to install packages on the system one must be the root user or use the sudo command_**

- True

**_39.Explain what are ACLs. For what use cases would you recommend to use them?_**

- An Access Control List (ACL) is a set of rules that determines which users or systems are granted or denied access to a specific resource, such as a file, directory, or network.

- They are used to enforce granular security policies, and recommended use cases include managing file and directory permissions, controlling network traffic, and securing API access. 

**_40.You try to create a file but it fails. Name at least three different reason as to why it could happen_**

- No more disk space
- No more inodes
- No permissions

**_41.A user accidentally executed the following `chmod -x $(which chmod)`. How to fix it?_**

- Using `sudo setfacl -m u::rx /usr/bin/chmod` will set the execute permissions on `chmod` for all the users. Post this, the `chmod` binary can be used as usual.

## Scenarios

**_42.You would like to copy a file to a remote Linux host. How would you do?_**

- There are multiple ways to transfer files between hosts. Personal opinion: use `rsync`

**_43.How to generate a random string?_**

- One way is to run the following: `cat /proc/sys/kernel/random/uuid`

**_44.How to generate a random string of 7 characters?_**

- `mkpasswd -l 7`

## Systemd

**_45.What is systemd?_**

- Systemd is a daemon (System 'd', d stands for daemon).

- A daemon is a program that runs in the background without direct control of the user, although the user can at any time talk to the daemon.

**_46.How to start or stop a service?_**

- To start a service: `systemctl start <service name>`
- To stop a service: `systemctl stop <service name>`

**_47.How to check the status of a service?_**

- `systemctl status <service name>`

**_48.On a system which uses systemd, how would you display the logs?_**

- `journalctl`

**_49.Describe how to make a certain process/app a service_**

- Create a new file with a .service extension in /etc/systemd/system/.
  - For example, my-app.service.
    - `sudo nano /etc/systemd/system/my-app.service`
   
- Populate the .service file with the necessary configurations. A basic unit file includes:
  - [Unit]
  - Description=My Custom Application Service
  - After=network.target

  - [Service]
  - ExecStart=/path/to/your/application/executable
  - WorkingDirectory=/path/to/your/application/directory
  - User=your_username
  - Restart=always
  - RestartSec=5
 
  - [Install]
  - WantedBy=multi-user.target

## Troubleshooting and Debugging

**_50.Where system logs are located?_**

- `/var/log`

**_51.How to follow file's content as it being appended without opening the file every time?_**

- `tail -f <file_name>`

**_52.What are you using for troubleshooting and debugging network issues?_**

- `dstat -t` is great for identifying network and disk issues. 
- `netstat -tnlaup` can be used to see which processes are running on which ports.
- `lsof -i -P` can be used for the same purpose as netstat.
- `ngrep -d any metafilter` for matching regex against payloads of packets.
- `tcpdump` for capturing packets.
- `wireshark` same concept as tcpdump but with GUI (optional).

**_53.What are you using for troubleshooting and debugging disk & file system issues?_**

- `dstat -t` is great for identifying network and disk issues.
- `opensnoop` can be used to see which files are being opened on the system (in real time).

**_54.What are you using for troubleshooting and debugging process issues?_**

- `strace` is great for understanding what your program does. It prints every system call your program executed.

**_55.What are you using for debugging CPU related issues?_**

- `top` will show you how much CPU percentage each process consumes
- `perf` is a great choice for sampling profiler and in general, figuring out what your CPU cycles are "wasted" on `flamegraphs` is great for CPU consumption visualization

**_56.You get a call from someone claiming "my system is SLOW". What do you do?_**

- Check with `top` for anything unusual
- Run `dstat -t` to check if it's related to disk or network.
- Check if it's network related with `sar`
- Check I/O stats with `iostat`

**_57.Explain iostat output_**

- The `iostat` command in Linux provides input/output statistics for devices and CPU utilization.

**_58.How to debug binaries?_**

- 1.Using GDB for Interactive Debugging
  - Start GDB
  - Set Breakpoints
  - Run the program
  - Step through code
  - Inspect variables
  - Examine memory
  - Continue execution
  - Quit GDB
  - Attaching to a Running Process
     
- 2.Utilizing Other Binary Analysis Tools
  - `strace`
  - `ltrace`
  - `readelf`
  - `objdump`
  - `ldd`
  - `strings`

- 3.Handling Missing Debugging Symbols

- 4.Remote Debugging
 
- 5.IDEs  

**_59.What is the difference between CPU load and utilization?_**

- CPU utilization is the percentage of time a CPU is actively busy, while CPU load is the number of processes either actively using the CPU or waiting to use it.

**_60.How you measure time execution of a program?_**

- `time` command

### Scenario

**_61.You have a process writing to a file. You don't know which process exactly, you just know the path of the file. You would like to kill the process as it's no longer needed. How would you achieve it?_**

- Run `lsof <FILE_PATH>`
- Use the pid (process ID) from the lsof command and run `kill <PID>`

## Kernel

**_62.What is a kernelm and what does it do?_**

- The kernel is part of the operating system and is responsible for tasks like:
  - Allocating memory
  - Schedule processes
  - Control CPU
 
**_63.How do you find out which Kernel version your system is using?_**

- `uname -a` command

**_64.What is a Linux kernel module and how do you load a new module?_**

- A Linux kernel module is a piece of code that can be dynamically loaded into the kernel to extend its functionality. These modules are typically used to add support for hardware devices, filesystems, or system calls. The kernel itself is monolithic, but with modules, its capabilities can be extended without having to reboot the system or recompile the entire kernel.

**_65.Explain user space vs. kernel space_**

- The operating system executes the kernel in protected memory to prevent anyone from changing (and risking it crashing). This is what is known as "Kernel space". "User space" is where users executes their commands or applications. It's important to create this separation since we can't rely on user applications to not tamper with the kernel, causing it to crash.

**_66.In what phases of kernel lifecycle, can you change its configuration?_**

- Build time (when it's compiled)
- Boot time (when it starts)
- Runtime (once it's already running)

**_67.Where can you find kernel's configuration?_**

- Usually it will reside in `/boot/config-<kernel version>.<os release>.<arch>`

**_68.Where can you find the file that contains the command passed to the boot loader to run the kernel?_**

- `/proc/cmdline`

**_69.How to list kernel's runtime parameters?_**

- `sysctl -a`

**_70.Will running sysctl -a as a regular user vs. root, produce different result?_**

- Yes, you might notice that in most systems, when running `systctl -a` with root, you'll get more runtime parameters compared to executing the same command with a regular user.

**_71.You would like to enable IPv4 forwarding in the kernel, how would you do it?_**

- `sudo sysctl net.ipv4.ip_forward=1`

- To make it persistent (applied after reboot for example): insert `net.ipv4.ip_forward = 1` into `/etc/sysctl.conf`

- Another way to is to run `echo 1 | sudo tee /proc/sys/net/ipv4/ip_forward`

**_72.How `sysctl` applies the changes to kernel's runtime parameters the moment you run sysctl command?_**

- If you `strace` the sysctl command you can see it does it by changing the file under /proc/sys/...

- In the past it was done with sysctl system call, but it was deprecated at some point.

**_73.How changes to kernel runtime parameters persist? (applied even after reboot to the system for example)_**

- There is a service called `systemd-sysctl` that takes the content of `/etc/sysctl.conf` and applies it. This is how changes persist, even after reboot, when they are written in `/etc/sysctl.conf`

**_74.Are the changes you make to kernel parameters in a container, affects also the kernel parameters of the host on which the container runs?_**

- No. Containers have their own `/proc` filesystem so any change to kernel parameters inside a container, are not affecting the host or other containers running on that host.

## SSH

**_75.What is SSH? How to check if a Linux server is running SSH?_**

- Wikipedia Definition: "SSH or Secure Shell is a cryptographic network protocol for operating network services securely over an unsecured network."

- Hostinger.com Definition: "SSH, or Secure Shell, is a remote administration protocol that allows users to control and modify their remote servers over the Internet."

- An SSH server will have SSH daemon running. Depends on the distribution, you should be able to check whether the service is running (e.g. `systemctl status sshd`).

**_76.Why SSH is considered better than telnet?_**

- Telnet also allows you to connect to a remote host but as opposed to SSH where the communication is encrypted, in telnet, the data is sent in clear text, so it doesn't considered to be secured because anyone on the network can see what exactly is sent, including passwords.

**_77.What is stored in `~/.ssh/known_hosts`?_**

- The file stores the key fingerprints for the clients connecting to the SSH server. This fingerprint creates a trust between the client and the server for future SSH connections.

**_78.You try to ssh to a server and you get "Host key verification failed". What does it mean?_**

- It means that the key of the remote host was changed and doesn't match the one that stored on the machine (in `~/.ssh/known_hosts`).

**_79.What is the difference between SSH and SSL?_**

- SSH (Secure Shell) and SSL (Secure Sockets Layer) are both cryptographic protocols for secure communication, but they serve fundamentally different purposes. SSH is primarily used for secure remote access and command execution, while SSL/TLS is used to secure data in transit between a website and a user's browser

**_80.What `ssh-keygen` is used for?

- ssh-keygen is a tool to generate an authentication key pair for SSH, that consists of a private and a public key. It supports a number of algorithms to generate authentication keys :
  - dsa
  - ecdsa
  - ecdsa-sk
  - ed25519
  - ed25519-sk
  - rsa (default)

- One can also specify number of bits in key. Command below generates an SSH key pair with RSA 4096-bits :
  - `$ ssh-keygen -t rsa -b 4096`

- The output looks like this:
  - Generating public/private rsa key pair.
  - Enter file in which to save the key (/home/user/.ssh/id_rsa):
  - Enter passphrase (empty for no passphrase):
  - Enter same passphrase again:
  - Your identification has been saved in /home/user/.ssh/id_rsa
  - Your public key has been saved in /home/user/.ssh/id_rsa.pub
  - The key fingerprint is:
  - SHA256:f5MOGnhzYfC0ZCHvbSXXiRiNVYETjxpHcXD5xSojx+M user@mac-book-pro
  - The key's randomart image is:
  - `+---[RSA 4096]----+`
  - `|        . ..+***o|`
  - `|         o o++*o+|`
  - `|        . =+.++++|`
  - `|         B.oX+. .|`
  - `|        S *=o+   |`
  - `|       . o oE.   |`
  - `|      . + + +    |`
  - `|       . = + .   |`
  - `|        .   .    |`
  - `+----[SHA256]-----+`

- One can check how many bits an SSH key has with :
  - `$ ssh-keygen -l -f /home/user/.ssh/id_rsa`
 
- Output should look like this :
  - `4096 SHA256:f5MOGnhzYfC0ZCHvbSXXiRiNVYETjxpHcXD5xSojx+M user@mac-book-pro (RSA)`

- It shows the key is RSA 4096-bits.

- `-l` and `-f` parameters usage explanation :
  - `l Show the fingerprint of the key file.`
  - `f filename Filename of the key file.`
 
**_81.What is SSH port forwarding?_**

- SSH port forwarding, also known as SSH tunneling, is a powerful technique that redirects network traffic through an encrypted SSH connection. This creates a secure "tunnel" that allows you to safely transmit data, bypass firewalls, and access services that might otherwise be unavailable. 

## Globbing & Wildcards

**_82.What is Globbing?_**

- Globbing is the mechanism used by the shell (like Bash) to expand wildcard characters in a command line into a list of matching file and directory names. This process happens before the command (such as `ls`, `cp`, or `rm`) actually runs, allowing users to perform operations on multiple files with a single, concise pattern.

**_83.What are wildcards? Can you give an example of how to use them?_**

-  Wildcards are special symbols used during a process called globbing to represent one or more characters when matching file or directory names in the command line. They are essential tools for managing files efficiently, allowing you to perform actions on groups of files without typing each name individually.

**_84.Explain what will `ls [XYZ]` match_**

- The command `ls [XYZ]` uses a wildcard pattern that leverages square brackets ([]) to perform filename matching (globbing).
- The pattern `[XYZ]` specifically matches any single character that is either an X, a Y, or a Z exactly where the bracket pattern appears in the filename.

**_85.Explain what will `ls [^XYZ]` match_**

- The command `ls [^XYZ]` utilizes a globbing pattern in Linux that uses the caret (`^`) character inside square brackets to perform negation.
- The pattern `[^XYZ]` matches any single character file name in the current directory that is not an `X`, `Y`, or `Z`.

**_86.Explain what will `ls [0-5]` match_**

- The command `ls [0-5]` uses a standard Linux globbing pattern that leverages square brackets (`[]`) with a range definition.
- This pattern matches any single-character filename that is a digit between `0` and `5`, inclusive.

**_87.What each of the following matches_**
- The `?` matches any single character
- The `*` matches zero or more characters

**_88.What do we grep for in each of the following commands?:_**
- `grep '[0-9]{1,3}.[0-9]{1,3}.[0-9]{1,3}.[0-9]{1,3}' some_file` -> An IP address
- `grep -E "error|failure" some_file` -> The word "error" or "failure"
- `grep '[0-9]$' some_file` -> Lines which end with a number

**_89.Which line numbers will be printed when running `grep '\baaa\b'` on the following content:_** 
- **_aaa bbb ccc.aaa aaaaaa_**

- No Output

**_90.What is the difference single and double quotes?_**

- In Linux shells (like Bash), both single quotes (`' '`) and double quotes (`" "`) are used to group strings and escape characters that would otherwise have special meaning (like spaces or wildcards).
- However, they differ fundamentally in one crucial way: single quotes disable all special meanings, while double quotes allow a select few special characters to remain active.
- This difference is often called "strong quoting" versus "weak quoting."

**_91.What is escaping? What escape character is used for escaping?_**

- Escaping is the mechanism used to remove the special meaning from a character that would normally be interpreted by the shell

- The escape character used is the backslash (`\`).

**_92.What is an exit code? What exit codes are you familiar with?_**

- An exit code (or return code) represents the code returned by a child process to its parent process.
- 0 is an exit code which represents success while anything higher than 1 represents error. Each number has different meaning, based on how the application was developed.

## Boot Process

**_93.Tell me everything you know about the Linux boot process._**

- The Linux boot process is a highly choreographed sequence of events that transforms a powered-off computer into a fully operational system, passing control from low-level hardware firmware to the operating system's kernel and finally to user-space applications.

- The process generally involves six major stages: 
  - 1. BIOS/UEFI (Firmware Initialization)
  - 2. Bootloader (GRUB)
  - 3. Kernel Initialization
  - 4. Initial RAM Disk (initramfs/initrd)
  - 5. Init Process (systemd)
    6. User Space and Login Prompt

**_94.What is GRUB2?_**

- GRUB2 (GRand Unified Bootloader version 2) is the standard and default bootloader for nearly all modern Linux distributions. It is the essential software that loads the Linux kernel (and initial RAM disk) into memory and transfers control to it, allowing the operating system to start.

**_95.What is Secure Boot?_**

- Secure Boot is a security standard and feature of the UEFI (Unified Extensible Firmware Interface) firmware designed to protect the computer's boot process from malicious software (like bootkits and rootkits) that tries to load during startup.

**_96.What can you find in /boot?_**

- The `/boot` directory in Linux contains the essential, static files required to start the system. The contents of this directory are read by the bootloader (like GRUB2) before the main operating system's configuration files in `/etc` are accessed.

## Disk and Filesystem

**_97.What's an inode?_**

- For each file (and directory) in Linux there is an inode, a data structure which stores meta data related to the file like its size, owner, permissions, etc.

**_98.Which of the following is not included in inode:_**
- **_Link count_**
- **_File size_**
- **_File name_**
- **_File timestamp_**

- File name (it's part of the directory file)

**_99.How to check which disks are currently mounted?_**

- Run `mount`

**_100.You run the `mount` command but you get no output. How would you check what mounts you have on your system?_**

- `cat /proc/mounts`

**_101.What is the difference between a soft link and hard link?_**

- Hard link is the same file, using the same inode. Soft link is a shortcut to another file, using a different inode.

**_102.True or False? You can create an hard link for a directory_**

- False

**_103.True or False? You can create a soft link between different filesystems_**

- True

**_104.True or False? Directories always have by minimum 2 links_**

- True

**_105.What happens when you delete the original file in case of soft link and hard link?_**

- When the original file is deleted, a soft link breaks because it merely points to the file's path, while a hard link remains fully functional because it acts as an alternative name pointing directly to the data on the disk. The data is only truly deleted when the last hard link referencing it is removed.

**_106.Can you check what type of filesystem is used in /home?_**

- There are many answers for this question. One way is running `df -T`

**_107.What is a swap partition? What is it used for?_**

- A swap partition is a dedicated area on a Linux storage drive that the operating system uses as virtual memory when the physical RAM is full. The kernel moves inactive data from RAM to this slower disk space to free up memory for active applications, or to write the entire system state to disk during hibernation.

**_108.How to create a_**
- **_new empty file_** -> `touch new_file.txt`
- **_a file with text (without using text editor)_** -> `
cat > new_file [enter] submit text; ctrl + d to exit insert mode`
- **_a file with given size_** -> `truncate -s new_file.txt`

**_109.You are trying to create a new file but you get "File system is full". You check with df for free space and you see you used only 20% of the space. What could be the problem?_**

- When you receive a "File system is full" error but df indicates plenty of free disk space, the problem is typically caused by exhausting all available inodes. In Linux filesystems, an inode is a metadata structure assigned to every file, storing information like ownership, permissions, and location on the disk, but not the file's actual data.
- While df reports on the usage of data blocks (the file content space), it doesn't always highlight inode usage. If a system has millions of extremely tiny files (e.g., temporary web cache files or session data), every single one consumes an inode. Once all inodes allocated for that specific partition are used up, the system cannot create any new files, regardless of how much physical storage space remains empty.

**_110.How would you check what is the size of a certain directory?_**

- `du -sh`

**_111.What is LVM?_**

- LVM (Logical Volume Management) is a powerful, flexible storage management system for Linux that provides an abstraction layer between the physical storage devices (hard disks, SSDs) and the filesystem partitions used by the operating system.

**_112.Explain the following in regards to LVM:_**
  - **_PV_** - A Physical Volume (PV) is the foundational layer of LVM. It is an actual, physical storage device or partition that has been initialized for use by LVM.

  - **_VG_** - A Volume Group (VG) is the next layer up. It is a unified pool of storage space created by combining one or more Physical Volumes.

  - **_LV_** - A Logical Volume (LV) is a "virtual partition" carved out from the storage pool provided by a Volume Group. This is the final layer that the operating system interacts with.

**_112.What is NFS? What is it used for?_**

- NFS (Network File System) is a distributed filesystem protocol in Linux that allows a user to access files and directories on a remote computer over a network as if they were stored locally on their own machine. 

**_113.What RAID is used for? Can you explain the differences between RAID 0, 1, 5 and 10?_**

- RAID (Redundant Array of Independent Disks) is a storage technology used in Linux and other operating systems that combines multiple physical disk drives into a single logical unit. Its primary purposes are to improve performance (speed), provide data redundancy (fault tolerance), or both. This allows administrators to optimize storage for specific needs, ranging from high-speed temporary storage to mission-critical, highly reliable data storage.

- The primary differences lie in how data is distributed and protected:
  - RAID 0 (Striping) offers the fastest performance by splitting data across drives, but provides no data protection if a single drive fails.
  - RAID 1 (Mirroring) provides maximum safety by duplicating all data across drives, but halves the usable storage capacity and offers no performance benefit for writing.
  - RAID 5 balances performance and safety by using striping with a parity scheme, allowing for a single drive failure tolerance with minimal capacity overhead (requiring at least three drives).
  - RAID 10 (Striping and Mirroring) provides the best of both worlds—high performance and high fault tolerance—by combining mirrored pairs into a striped array, though at the cost of 50% usable capacity (requiring at least four drives).

**_114.Describe the process of extending a filesystem disk space_**

- Extending a filesystem's disk space in Linux involves several steps that must be performed sequentially, moving from the physical layer up to the logical layer. The exact process depends on whether you are using traditional disk partitions or LVM (Logical Volume Management), with LVM being the more flexible method. 

- The General Process
  - 1. Add/Expand the Physical Disk Space: This is usually done at the hardware level (adding a new drive) or hypervisor level (expanding a virtual disk in VMware, AWS, etc.).
    2. Rescan the Kernel: The Linux kernel needs to recognize the new, unallocated space.
      - For a new disk, you might need to rescan the SCSI host: echo "- - -" > /sys/class/scsi_host/host[X]/scan.
      - For an expanded existing disk, a simple reboot often works, or you can force a rescan: echo 1 > /sys/block/sd[X]/device/rescan.
    3. Expand the Partition/Volume: This is where the process diverges based on your setup

**_115.What is lazy umount?_**

- Lazy unmount in Linux is a mechanism that allows you to immediately detach a filesystem from the system's directory hierarchy, even if it is currently "busy" (has open files or active processes using it). 

**_116.What is tmpfs?_**

- `tmpfs` (Temporary File System) is a type of volatile, in-memory filesystem used in Linux. It is a modern, faster alternative to the older `ramdisk` approach.

**_117.What is stored in each of the following logs?_**
- **_/var/log/messages_** -> Stores general system activity, informational messages, and non-critical errors from the kernel and various daemons on Red Hat-based systems.
- **_/var/log/boot.log_** -> Contains a record of all events, service statuses, and console messages generated specifically during the system's boot process.

**_118.True or False? both /tmp and /var/tmp cleared upon system boot_**

- False. `/tmp` is cleared upon system boot while `/var/tmp` is cleared every a couple of days or not cleared at all (depends on distro).

## Performance Analysis

**_119.How to check what is the current load average?_**

- One can use `uptime` or `top`

**_120.You know how to see the load average, great. but what each part of it means? for example 1.43, 2.34, 2.78_**

- The Linux load average provides a snapshot of system demand and can typically be viewed using commands like `uptime`, `top`, or `htop`. It is represented by three numbers:

- `load average: 1.43, 2.34, 2.78`

- These three numbers represent the average number of processes that are either running or waiting to run (in a runnable state or uninterruptible sleep) over different time periods:

- `Value	Time Period	      Meaning`
- `1.43	  Last 1 minute	    The immediate system load average.`
- `2.34	  Last 5 minutes    The intermediate system load average.`
- `2.78	  Last 15 minutes	  The long-term system load average.`

**_121.How to check process usage?_**

- `pidstat`

**_122.How to check disk I/O?_**

- `iostat -xz 1`

**_123.How to check how much free memory a system has? How to check memory consumption by each process?_**

- You can use the commands `top` and `free`

**_124.How to check TCP stats?_**

- sar -n TCP,ETCP 1

## Processes

**_125.How to list all the processes running in your system?_**

- The "`ps`" command can be used to list all the processes running in a system. The "`ps aux`" command provides a detailed list of all the processes, including the ones running in the background.

**_126.How to run a process in the background and why to do that in the first place?_**

- You can achieve that by specifying & at the end of the command. As to why, since some commands/processes can take a lot of time to finish execution or run forever, you may want to run them in the background instead of waiting for them to finish before gaining control again in current session.

**_127.How can you find how much memory a specific process consumes?_**

- `mem()`
- `{`
- `ps -eo rss,pid,euser,args:100 --sort %mem | grep -v grep | grep -i $@ | awk '{printf $1/1024 "MB"; $1=""; print }'`
- `}`

**_128.What signal is used by default when you run 'kill *process id*'?_**

- The default signal is SIGTERM (15). This signal kills process gracefully which means it allows it to save current state configuration.

**129.What signals are you familiar with?_**

- SIGTERM -> default signal for terminating a process
- SIGHUP -> common usage is for reloading configuration
- SIGKILL -> a signal which cannot caught or ignored
- To view all available signals run `kill -l`

**_130.What kill 0 does?_**

- "`kill 0`" sends a signal to all processes in the current process group. It is used to check if the processes exist or not

**_131.What kill -0  does?_**

- "`kill -0`" checks if a process with a given process ID exists or not. It does not actually send any signal to the process.

**_132.What is a trap?_**

- A trap is a mechanism that allows the shell to intercept signals sent to a process and perform a specific action, such as handling errors or cleaning up resources before terminating the process.

**_133.Every couple of days, a certain process stops running. How can you look into why it's happening?_**

- One way to investigate why a process stops running is to check the system logs, such as the messages in `/var/log/messages` or `journalctl`. Additionally, checking the process's resource usage and system load may provide clues as to what caused the process to stop.

**_134.What happens when you press ctrl + c?_**

- When you press "Ctrl+C," it sends the SIGINT signal to the foreground process, asking it to terminate gracefully.

**_135.What is a Daemon in Linux?_**

- A background process. Most of these processes are waiting for requests or set of conditions to be met before actually running anything. Some examples: sshd, crond, rpcbind.

**_136.What are the possible states of a process in Linux?_**

- `Running (R)`
- `Uninterruptible Sleep (D)` - The process is waiting for I/O
- `Interruptible Sleep (S)`
- `Stopped (T)`
- `Dead (x)`
- `Zombie (z)`

**_137.How do you kill a process in D state?_**

- A process in D state (also known as "uninterruptible sleep") cannot be killed using the "kill" command. The only way to terminate it is to reboot the system.

**_138.What is a zombie process?_**

- A process which has finished to run but has not exited.

- One reason it happens is when a parent process is programmed incorrectly. Every parent process should execute wait() to get the exit code from the child process which finished to run. But when the parent isn't checking for the child exit code, the child process can still exists although it finished to run.

**_139.How to get rid of zombie processes?_**

- You can't kill a zombie process the regular way with kill -9 for example as it's already dead.
- One way to kill zombie process is by sending SIGCHLD to the parent process telling it to terminate its child processes. This might not work if the parent process wasn't programmed properly. The invocation is kill -s SIGCHLD [parent_pid]
- You can also try closing/terminating the parent process. This will make the zombie process a child of init (1) which does periodic cleanups and will at some point clean up the zombie process.

**_140.How to find all the_**
- **_Processes executed/owned by a certain user_** -> `ps -u [username]`
- **_Process which are Java processes_** -> `ps -ef | grep java`
- **_Zombie Processes_** -> `ps -eAo stat,pid,comm | grep -w Z`

**_141.What is the init process?_**

- It is the first process executed by the kernel during the booting of a system. It is a daemon process which runs till the system is shutdown. That is why, it is the parent of all the processes

**_142.Can you describe how processes are being created?_**

- The process creation mechanism is fundamentally based on a two-step procedure involving the fork() and exec() system calls, known as the fork-exec model.

**_143.How to change the priority of a process? Why would you want to do that?_**

- To change the priority of a process, you can use the nice command in Linux. The nice command allows you to specify the priority of a process by assigning a priority value ranging from -20 to 19. A higher value of priority means lower priority for the process, and vice versa.
- You may want to change the priority of a process to adjust the amount of CPU time it is allocated by the system scheduler. For example, if you have a CPU-intensive process running on your system that is slowing down other processes, you can lower its priority to give more CPU time to other processes.

**_144.Can you explain how network process/connection is established and how it's terminated?_**

- When a client process on one system wants to establish a connection with a server process on another system, it first creates a socket using the socket system call. The client then calls the connect system call, passing the address of the server as an argument. This causes a three-way handshake to occur between the client and server, where the two systems exchange information to establish a connection.
Once the connection is established, the client and server can exchange data using the read and write system calls. When the connection is no longer needed, the client or server can terminate the connection by calling the close system call on the socket.

**_145.What `strace` does? What about `ltrace`?_**

- `Strace` is a debugging tool that is used to monitor the system calls made by a process. It allows you to trace the execution of a process and see the system calls it makes, as well as the signals it receives. This can be useful for diagnosing issues with a process, such as identifying why it is hanging or crashing.
- `Ltrace`, on the other hand, is a similar tool that is used to trace the library calls made by a process. It allows you to see the function calls made by a process to shared libraries, as well as the arguments passed to those functions. This can be useful for diagnosing issues with a process that involve library calls, such as identifying why a particular library is causing a problem.

**_146.Find all the files which end with '.yml' and replace the number 1 in 2 in each file_**

- find /some_dir -iname *.yml -print0 | xargs -0 -r sed -i "s/1/2/g"

**_147.You run ls and you get "/lib/ld-linux-armhf.so.3 no such file or directory". What is the problem?_**

- The ls executable is built for an incompatible architecture.

**_148.How would you split a 50 lines file into 2 files of 25 lines each?_**

- You can use the `split` command this way: `split -l 25 some_file`

**_149.What is a kerberos file descriptor? What file descriptors are you familiar with?_**

- Kerberos File descriptor, also known as file handler, is a unique number which identifies an open file in the operating system.
In Linux (and Unix) the first three file descriptors are:
  - 0 - the default data stream for input
  - 1 - the default data stream for output
  - 2 - the default data stream for output related to errors

**_150.What is NTP? What is it used for?_**

- NTP stands for Network Time Protocol. It is a networking protocol used for clock synchronization between computer systems over packet-switched, variable-latency data networks, like the internet. In simpler terms, it's a way for your Linux machine (or any networked device) to get the correct time from a highly accurate source.

**_151.Explain Kernel OOM._**

- The Kernel OOM (Out-of-Memory) Killer is a crucial, last-resort mechanism in the Linux kernel designed to maintain system stability when the available physical RAM and swap space have been exhausted. Due to Linux's default policy of memory overcommit (where the kernel allows processes to request more memory than is physically available), it's possible for the system to run into a critical situation where a legitimate memory request cannot be fulfilled.

## Security

**_152.What is chroot? In what scenarios would you consider using it?_**

- Chroot, short for "change root," is a command and system call in Linux that changes the apparent root directory (/) for the currently running process and all its children. This action creates a restricted environment, often called a chroot jail, where the processes running inside cannot access or name files outside of the newly defined directory structure. Essentially, the processes are isolated and tricked into believing that the new directory is the topmost level of the file system. While this provides a form of basic sandboxing, it does not provide full security isolation on its own, as a process with root privileges can potentially escape the jail.

- The chroot utility is primarily used in scenarios requiring isolation, system recovery, or clean building environments. Common uses include system maintenance and repair, such as when a Linux system fails to boot: an administrator can boot from a live USB, mount the damaged system's partitions, and then use chroot to step into that broken environment to safely reinstall a bootloader or reset a forgotten password. It is also used for security sandboxing by restricting network services (like FTP or DNS daemons) to a limited part of the file system to contain the damage if the service is compromised. Furthermore, developers use it to build software packages in a clean environment that only contains the necessary dependencies, preventing unintended conflicts with the host system.

**_153.What is SELiunx?_**

- SELinux (Security-Enhanced Linux) is a Linux kernel security module that provides a mechanism for supporting Mandatory Access Control (MAC) security policies. It was originally developed by the U.S. National Security Agency (NSA) and integrated into the Linux kernel using the Linux Security Modules (LSM) framework. Its primary purpose is to add a crucial, fine-grained layer of security that operates in addition to the traditional Linux Discretionary Access Control (DAC), which is the standard owner/group/world read/write/execute permissions.

**_154.What is Kerberos?_**

- Kerberos is a network authentication protocol that uses symmetric-key cryptography to provide strong mutual authentication for client-server applications over non-secure networks. It was developed at MIT and is designed to eliminate the transmission of unencrypted passwords across the network. Instead of passwords, Kerberos uses temporary, encrypted credentials called tickets to prove the identity of both the user and the service. This is the foundation for providing a Single Sign-On (SSO) experience in a Linux or Unix network environment, allowing users to log in once and access multiple services without re-entering credentials.

**_155.What is nftables?_**

- nftables is the modern, flexible packet filtering framework that replaced the aging iptables in the Linux kernel. It is integrated with the Netfilter project and provides a more efficient, unified, and scalable approach to managing firewall rules.

**_156.What firewalld daemon is responsible for?_**

- The firewalld daemon is the dynamic firewall management service that acts as the primary network defense mechanism on many modern Linux distributions (like Fedora, CentOS/RHEL, and recent Debian/Ubuntu versions). Its main responsibility is to provide a user-friendly, dynamic, and rule-set-independent interface for configuring the underlying kernel packet filtering facilities (Netfilter, which may use iptables or nftables as the backend).

**_157.Do you have experience with hardening servers? Can you describe the process?_**

- Yes, I have extensive knowledge of server hardening best practices in a Linux environment. Hardening is a systematic process of increasing a server's security posture by reducing its attack surface, eliminating unnecessary functionality, and strengthening configurations.

- The process is generally divided into several key phases
  - 1.`Baseline & Preparation` -> Establish a secure starting point, document the current configuration, and ensure all systems are up-to-date.
  - 2.`Reduce Attack Surface` - > Remove unnecessary software and services to minimize potential entry points for attackers.
  - 3.`Account & Authentication` -> Implement strong controls over user access and authentication mechanisms.
  - 4.`Kernel & System Security` -> Configure kernel parameters and security modules to defend against exploits.
  - 5.`Network & Firewall` -> Implement robust filtering and monitoring of all network traffic.
  - 6.`Logging & Auditing` -> Ensure all significant security events are logged, and implement regular reviews.
    
**_158.How do you create a private key for a CA (certificate authority)?_**

- One way is using openssl this way:
  - `openssl genrsa -aes256 -out ca-private-key.pem 4096`
 
**_159.How do you create a public key for a CA (certificate authority)?_**

- `openssl req -new -x509 -days 730 -key [private key file name] -sha256 -out ca.pem`

- If using the private key from the previous question then the command would be:
  - `openssl req -new -x509 -days 730 -key ca-private-key.pem -sha256 -out ca.pem`
 
**_160.Demonstrate one way to encode and decode data in Linux_**

- Encode: `echo -n "some password" | base64` Decode: `echo -n "allE19remO91" | base64`

## Networking

**_161.How to list all the interfaces?_**

- `ip link show`

**_162.What is the loopback (lo) interface?_**

- The loopback interface is a special, virtual network interface that your computer uses to communicate with itself. It is used mainly for diagnostics and troubleshooting, and to connect to servers running on the local machine.

**_163.What the following commands are used for?_**

  - **_1.ip addr_** -> Used to display and manipulate IP addresses and their associated properties on network interfaces. It shows the current state of all interfaces (e.g., eth0, lo), their assigned IPv4 and IPv6 addresses, network masks, and hardware (MAC) addresses
    
  - **_2.ip route_** -> Used to display and manipulate the IP routing table. It shows how packets are directed out of the system, including the default gateway (default via), destination networks, and which network interface (dev) to use.
  - 
  - **_3.ip link_** -> Used to display and manipulate the state of network interfaces (Layer 2 configuration). It shows interface status (e.g., UP/DOWN), hardware (MAC) addresses, Multi-Transport Unit (MTU), and other physical/link layer properties. It is used to bring interfaces up or down.
    
  - **_4.ping_** -> Used to test basic network connectivity to a target host (IP address or hostname). It sends ICMP Echo Request packets and measures the time it takes to receive the Echo Reply, providing the Round Trip Time (RTT) and reporting packet loss. This confirms if the host is "alive" and reachable.
    
  - **_5.netstat_** -> (Short for Network Statistics) Used to display active network connections, routing tables, interface statistics, and open listening ports. It's useful for security auditing and troubleshooting to see what services are running, on which ports they are listening, and what connections are currently established. Note: On modern Linux systems, netstat is being superseded by the more performant ss command.
    
  - **_6.traceroute_** -> Used to trace the path that network packets take from the source host to a destination host. It works by sending packets with gradually increasing Time To Live (TTL) values and records the IP address and latency of each intermediate router, or hop, on the path. This is vital for identifying network bottlenecks or points of failure.

**_164.What is a network namespace? What is it used for?_**

- A network namespace is a feature of the Linux kernel that provides a virtually isolated copy of the network stack for a set of processes. This isolation includes its own network interfaces, IP address tables, routing tables, socket lists, connection tracking tables, and firewall rules. Every new Linux system starts with at least one default network namespace, known as the initial or root namespace. Any process inside a network namespace sees only the network configuration and interfaces associated with that specific namespace, making it appear as if it is running on an entirely separate host.

- Network namespaces are a foundational technology for containerization (e.g., Docker, Kubernetes) and other virtualization solutions, as they allow multiple containers on a single host to run applications using the same port numbers (like port 80 or 443) without conflict, each binding to the interfaces within its own isolated environment. They are also used for network testing and development, enabling developers and administrators to create complex virtual network topologies, test routing protocols, and simulate different network conditions on a single machine without needing physical hardware or fully virtualized systems.

**_165.How to check if a certain port is being used?_**

- One of the following would work:
  - `netstat -tnlp | grep <port_number>`
  - `lsof -i -n -P | grep <port_number>`

**_166.How can you turn your Linux server into a router?_**

- To turn a Linux server into a router, you must configure the kernel to enable IP forwarding (or IP masquerading) so that the server can route packets between different network interfaces. This is primarily done by setting the kernel parameter `net.ipv4.ip_forward` to `1` in the `/etc/sysctl.conf` file. Additionally, you need to configure Network Address Translation (NAT) rules using the firewall (e.g., `nftables` or `iptables`) to allow devices on the private network to share the server's single external IP address when communicating with the internet.

**_167.What is a virtual IP? In what situation would you use it?_**

- A Virtual IP (VIP) is an IP address that is not permanently assigned to a single physical network interface but is instead shared and managed by a group of hosts. It acts as a logical identifier for a service or a cluster of servers, creating a single point of access for clients. Clients connect to the VIP, and the underlying network infrastructure or cluster software determines which physical server actually receives and handles the traffic destined for that address.

- VIPs are essential in high availability (HA) and load balancing scenarios. In HA, a VIP is used to achieve failover; for instance, a master server holds the VIP, and if it fails, a heartbeat or cluster manager instantly moves (or floats) the VIP to a redundant backup server, ensuring the service remains continuously accessible to users without a change in the connection address. In load balancing, the VIP is assigned to a front-end load balancer, which then distributes incoming client connections across multiple back-end application or web servers to efficiently spread the workload and handle higher traffic volumes.

**_168.True or False? The MAC address of an interface is assigned/set by the OS_**

- False

**_169.Can you have more than one default gateway in a given system?_**

- Technically, yes.

**_170.What is telnet and why is it a bad idea to use it in production? (or at all)_**

- Telnet is a type of client-server protocol that can be used to open a command line on a remote computer, typically a server. By default, all the data sent and received via telnet is transmitted in clear/plain text, therefore it should not be used as it does not encrypt any data between the client and the server.

**_171.What is the routing table? How do you view it?_**

- The routing table is a kernel data structure used by Linux to determine the next hop (destination) for an outgoing packet. It matches a packet's destination IP against its entries to decide which gateway and local network interface to use, including a default route for all unknown destinations.

- You can view the routing table using the command `ip route` (or the more verbose `ip route show`), which displays the destination network, the gateway IP, and the device (interface) associated with each entry.

**_172.How can you send an HTTP request from your shell?_**

- Using nc is one way

**_173.What are packet sniffers? Have you used one in the past? If yes, which packet sniffers have you used and for what purpose?_**

- It is a network utility that analyses and may inject tasks into the data-stream travelling over the targeted network.

**_174.How to list active connections?_**

- `ss -tn`

**_175.How to trigger neighbor discovery in IPv6?_**

- One way would be `ping6 ff02::1`

**_176.What is network interface bonding and do you know how it's performed in Linux?_**

- Network interface bonding (also known as NIC Teaming or link aggregation) is a Linux technique used to combine multiple physical network interfaces (like eth0 and eth1) into a single logical link, called a bond interface (e.g., bond0).

- How it's Performed in Linux
  - Bonding is implemented using the bonding kernel module and is configured via user-space tools. The high-level steps are:
    - 1.Load the Module: Ensure the bonding kernel module is loaded (modprobe bonding).
    - 2.Configuration Files: Create a configuration file for the new bond interface (bond0) that defines the IP address, netmask, and the bonding mode (e.g., Active-Backup, Round Robin).
    - 3.Configure Slaves: Configure the physical interfaces (the "slave" interfaces) to be part of the bond interface and ensure they do not have their own IP addresses.
    - 4.Networking Service Restart: Restart the networking service to bring up the bond0 interface.

**_177.What network bonding modes are there?_**

- There a couple of modes:
  - balance-rr: round robing bonding
  - active-backup: a fault tolerance mode where only one is active
  - balance-tlb: Adaptive transmit load balancing
  - balance-alb: Adaptive load balancing
 
**_178.What is a bridge? How it's added in Linux OS?_**

- A network bridge is a software device that functions like a Layer 2 network switch on a Linux server, forwarding traffic between multiple network segments (physical interfaces, virtual interfaces, or other bridges) based on MAC addresses.

- It is added in Linux by using the brctl utility (from the bridge-utils package, for legacy setups) or the modern ip link command:
  - 1.Create the bridge: `ip link add name br0 type bridge`
  - 2.Add interfaces (ports): `ip link set eth0 master br0`
  - 3.Bring up the bridge: `ip link set br0 up`

## DNS

**_179.How to check what is the hostname of the system?_**

- `cat /etc/hostname`

- You can also run `hostnamectl` or `hostname` but that might print only a temporary hostname. The one in the file is the permanent one.

**_180.What the file /etc/resolv.conf is used for? What does it include?_**

- The file /etc/resolv.conf configures the Linux system's DNS resolver for hostname-to-IP-address translation.
- It primarily includes the nameserver directives, which list the IP addresses of the DNS servers to query, and the search directive, which specifies domain names to append to hostnames for unqualified lookups.

**_181.What commands are you using for performing DNS queries (or troubleshoot DNS related issues)?_**

- You can specify one or more of the following:
  - dig
  - host
  - nslookup
 
**_182.You run dig codingshell.com and get the following result:_**
- **_`ANSWER SECTION:`_**
- **_`codingshell.com.	3515	IN	A	185.199.109.153`_**
- **_`What is the meaning of the number 3515?`_**
- **_What is the meaning of the number 3515?_**

- This is the TTL. When you lookup for an address using a domain/host name, your OS is performing DNS resolution by contacting DNS name servers to get the IP address of the host/domain you are looking for.
- When you get a reply, this reply in cached in your OS for a certain period of time. This is period of time is also known as TTL and this is the meaning of 3515 number, it will be cached for 3515 seconds before removed from the cache and during that period of time, you'll get the value from the cache instead of asking DNS name servers for the address again.

**_183.How can we modify the network connection via `nmcli` command, to use `8.8.8.8` as a DNS server?_**

- 1.Find the connection name:
- `# nmcli con show`
- `NAME         UUID                                  TYPE      DEVICE`
- `System ens5  8126c120-a964-e959-ff98-ac4973344505  ethernet  ens5`
- `System eth0  5fb06bd0-0bb0-7ffb-45f1-d6edd65f3e03  ethernet  --`

Here the connection name is "System ens5". Let's say we want to modify settings for this connection.

- 2.Modify the connection to use 8.8.8.8 as DNS server:

- `# nmcli con mod "System ens5" ipv4.dns "8.8.8.8"`

- 3.We need to reactivate the connection for the change to take effect:

- `nmcli con up "System ens5"`

- 4.Verify our settings once more:

- `cat /etc/resolv.conf`
- `nmcli -f ipv4.dns con show "System ens5"`

## Packaging

**_184.**Do you have experience with packaging? (as in building packages) Can you explain how does it works?_**

- Yes, I have extensive knowledge of the packaging process in Linux. Building packages is the method of compiling an application's source code and bundling the resulting binaries, configuration files, documentation, and dependencies into a single, standardized archive file (like a .deb or .rpm) that can be easily installed, upgraded, and removed across many systems.

**_185.How packages installation/removal is performed on the distribution you are using?_**

- The answer depends on the distribution being used.
- In Fedora/CentOS/RHEL/Rocky it can be done with `rpm` or `dnf` commands. In Ubuntu it can be done with the `apt` command.

**_186.RPM: explain the spec format (what it should and can include)_**

- The RPM Spec File is the blueprint for creating RPM packages, containing metadata (Name, Version, Release, License, Summary, Dependencies), build instructions (%prep, %build, %install), a list of all files to include in the package (%files), and optional scriptlets (%pre, %post, %preun, %postun) that execute during the installation or removal process.

**_187.How do you list the content of a package without actually installing it?_**

- To list the contents (the files and their installation paths) of a Linux package without actually installing it, you use the query capabilities of the package manager specific to your distribution: `rpm` for RPM-based systems or `dpkg` for Debian-based systems.

**_188.How to know to which package a file on the system belongs to? Is it a problem if it doesn't belongs to any package?_**

- To find the owning package for a file, you use the package manager's query function: `rpm -qf /path/to/file` (for RHEL/Fedora) or `dpkg -S /path/to/file` (for Debian/Ubuntu).

- It is NOT necessarily a problem if a file doesn't belong to any package; this is normal for user-created data, logs, or manually compiled third-party software. However, it is a major security concern if critical system files (e.g., in `/usr/bin` or `/etc`) are unowned, as this can indicate a manual installation of malicious code or system tampering.

**_189.Where repositories are stored? (based on the distribution you are using)_**

- Linux distribution repositories are typically configured via files located in the /etc/apt/ or /etc/yum.repos.d/ directories.
  - Debian/Ubuntu (using APT): Repository lists are primarily defined in the `/etc/apt/sources.list` file and often in individual `.list` files within the `/etc/apt/sources.list.d/` directory.
  - RHEL/CentOS/Fedora (using DNF/YUM): Repository configurations are stored in individual `.repo` files within the `/etc/yum.repos.d/` directory (e.g., `epel.repo`).
 
**_190.What is an archive? How do you create one in Linux?_**

- An archive is a single file that bundles multiple other files and directories together, primarily for the purpose of data consolidation and easy portability. Archives are typically created using utilities like `tar` and often use compression algorithms (like gzip or bzip2) to reduce their size, though the archiving and compression steps are technically separate processes.
- The basic command to create a compressed archive is:
  - `tar -czvf archive_name.tar.gz /path/to/files/`

**_191.How to extract the content of an archive?_**

- `tar -xzvf archive_name.tar.gz`

**_192.Why do we need package managers? Why not simply creating archives and publish them?_**

- Package managers allow you to manage packages lifecycle as in installing, removing and updating the packages.
- In addition, you can specify in a spec how a certain package will be installed - where to copy the files, which commands to run prior to the installation, post the installation, etc.

## DNF

**_193.What is DNF?_**

- "Dandified YUM (DNF) is the next upcoming major version of YUM. It does package management using RPM, libsolv and hawkey libraries."

**_194.How to look for a package that provides the command /usr/bin/git? (the package isn't necessarily installed)_**

- dnf provides /usr/bin/git

## Applications & Services

**_195.What can you find in /etc/services?_**

- The file `/etc/services` is a plain text configuration file in Linux that acts as a local database mapping well-known service names to their corresponding port numbers and transport protocols (TCP or UDP).

**_196.How to make sure a Service starts automatically after a reboot or crash?_**

- Depends on the init system.

- Systemd:  `systemctl enable [service_name]`  System V:  `update-rc.d [service_name]`  and add this line  `id:5678:respawn:/bin/sh /path/to/app`  to `/etc/inittab` Upstart: add Upstart init script at /etc/init/service.conf

**_197.You run ssh 127.0.0.1 but it fails with "connection refused". What could be the problem?_**

- 1.SSH server is not installed
- 2.SSH server is not running

**_198.How to print the shared libraries required by a certain program? What is it useful for?_**

- To print the shared libraries required by a certain program in Linux, you use the ldd command (List Dynamic Dependencies).

- The `ldd` command is useful for troubleshooting program startup failures caused by missing dependencies and for verifying that the correct library versions are being linked. It is essential when building minimal container images or creating isolated chroot environments, as it defines the exact set of external files required for the application to run.

**_199.What is CUPS?_**

- CUPS stands for Common Unix Printing System. It is a modular printing system that allows a computer running Linux to act as a print server. It is the standard printing service used by nearly all modern Linux distributions.

**_200.What types of web servers are you familiar with?_**

- Nginx, Apache httpd.

## Users and Group

**_201.What is a "superuser" (or root user)? How is it different from regular users?_**

- A superuser, or root user, is the administrative account in Linux, possessing unrestricted system privileges.

- It is fundamentally different from a regular user in the following ways:
  - Permissions: The superuser (UID 0) can bypass standard file and directory permissions (DAC), allowing it to read, write, or execute any file and perform any system-wide changes (installing software, configuring networks, managing all users).
  - Regular users have restricted permissions, primarily limited to their own home directory and files, and must use tools like sudo to temporarily gain root privileges for administrative tasks.
 
**_202.How do you create users? Where user information is stored?_**

- Command to create users is `useradd`
- Syntax: `useradd [options] Username`
- There are 2 configuration files, which stores users information
- 1.`/etc/passwd` - Users information like, username, shell etc is stored in this file
- 2.`/etc/shadow` - Users password is stored in encrypted format

**_203.Which file stores information about groups?_**

- `/etc/groups` file stores the group name, group ID, usernames which are in secondary group.

**_204.How do you change/set the password of a user?_**

- `passwd <username>` is the command to set/change password of a user.

**_205.Which file stores users passwords? Is it visible for everyone?_**

- `/etc/shadow` file holds the passwords of the users in encrypted format. NO, it is only visible to the root user

**_206.Do you know how to create a new user without using adduser/useradd command?_**

- YES, we can create new user by manually adding an entry in the `/etc/passwd` file.
- For example, if we need to create a user called john.
  - Step 1: Add an entry to `/etc/passwd` file, so user gets created.
    - `echo "john:x:2001:2001::/home/john:/bin/bash" >> /etc/passwd`
  - Step 2: Add an entry to `/etc/group` file, because every user belong to the primary group that has same name as the username.
    - `echo "john:x:2001:" >> /etc/group`
  - Step 3: Verify if the user got created
    - `id john`
   
**_207.What information is stored in /etc/passwd? explain each field_**

- `/etc/passwd` is a configuration file, which contains users information. Each entry in this file has, 7 fields,

- `username:password:UID:GID:Comment:home directory:shell`

- `username` - The name of the user.

- `password` - This field is actually a placeholder of the password field. Due to security concerns, this field does not contain the password, just a placeholder (x) to the encrypted password stored in /etc/shadow file.

- `UID` - User ID of the user.

- `GID` - Group ID

- `Comment` - This field is to provide description about the user.

- `home directory` - Abousulte path of the user's home directory. This directory gets created once the user is added.
  
- `shell` - This field contains the absolute path of the shell that will be used by the respective user.

**_208.How to add a new user to the system without providing him the ability to log-in into the system?_**

- `adduser user_name --shell=/bin/false --no-create-home` You can also add a user and then edit /etc/passwd.

**_208.How to switch to another user? How to switch to the root user?_**

- `su` command. Use `su -` to switch to root

**_209.What is the UID the root user? What about a regular user?_**

- UID of root user is 0
- Default values of UID_MIN and UID_MAX in `/etc/login.defs` `UID_MIN` is `1000` `UID_MAX` is `60000`

- Actually, we can change this value. But UID < 1000 are reserved for system accounts. Therefore, as per the default configuration, for regular user UID starts from `1000`.

**_210.What can you do if you lost/forogt the root password?_**

- Re-install the OS IS NOT the right answer

**_211.What is /etc/skel?_**

- `/etc/skel` is a directory, that contains files or directories, so when a new user is created, these files/directories created under `/etc/skel` will be copied to user's home directory.

**_212.How to see a list of who logged-in to the system?_**

- Using the `last` command.

**_213.Explain what each of the following commands does:_**
- **_1.useradd_** -> Command for creating new users
- **_2.usermod_** -> Modify the users setting
- **_3.whoami_** -> Outputs, the username that we are currently logged in 
- **_4.id_**  Prints the User ID (UID), Group ID (GID)

**_214.You run grep $(whoami) /etc/passwd but the output is empty. What might be a possible reason for that?_**

- The user you are using isn't defined locally but originates from services like LDAP.
- You can verify with: `getent passwd`

## Hardware

**_215.Where can you find information on the processor (like number of CPUs)?_**

- `/proc/cpuinfo`

- You can also use nproc for number of processors

**_216.How can you print information on the BIOS, motherboard, processor and RAM?_**

- `dmidecoode`

**_217.How can you print all the information on connected block devices in your system?_**

- `lsblk`

**_218.True or False? In user space, applications don't have full access to hardware resources_**

- True. Only in kernel space they have full access to hardware resources.

## Namespaces

**_219.What types of namespaces are there in Linux?_**

- Process ID namespaces: these namespaces include independent set of process IDs
- Mount namespaces: Isolation and control of mountpoints
- Network namespaces: Isolates system networking resources such as routing table, interfaces, ARP table, etc.
- UTS namespaces: Isolate host and domains
- IPC namespaces: Isolates interprocess communications
- User namespaces: Isolate user and group IDs
- Time namespaces: Isolates time machine

**_220.True or False? In every PID (Process ID) namespace the first process assigned with the process id number 1_**

- True. Inside the namespace it's PID 1 while to the parent namespace the PID is a different one.

**_221.True or False? In a child PID namespace all processes are aware of parent PID namespace and processes and the parent PID namespace has no visibility of child PID namespace processes_**

- False. The opposite is true. Parent PID namespace is aware and has visibility of processes in child PID namespace and child PID namespace has no visibility as to what is going on in the parent PID namespace.

**_222.rue or False? By default, when creating two separate network namespaces, a ping from one namespace to another will work fine_**

- False. Network namespace has its own interfaces and routing table. There is no way (without creating a bridge for example) for one network namespace to reach another.

**_223.True or False? With UTS namespaces, processes may appear as if they run on different hosts and domains while running on the same host_**

- True

**_224.True or False? It's not possible to have a root user with ID 0 in child user namespaces_**

- False. In every child user namespace, it's possible to have a separate root user with uid of 0.

**_225.What time namespaces are used for?_**

- In time namespaces processes can use different system time.

## Virtualization

**_226.What virtualization solutions are available for Linux?_**

- KVM
- XEN
- VirtualBox
- Linux-VServer
- User-mode Linux

**_227.What is KVM?_**

- Is an open source virtualization technology used to operate on x86 hardware.

**_228.What is Libvirt?_**

- It's an open source collection of software used to manage virtual machines. It can be used with: KVM, Xen, LXC and others. It's also called Libvirt Virtualization API.

## AWK

**_229.What the awk command does? Have you used it? What for?_**

- From Wikipedia: "AWK is domain-specific language designed for text processing and typically used as a data extraction and reporting tool"

**_230.How to print the 4th column in a file?_**

- `awk '{print $4}'` file

**_231.How to print every line that is longer than 79 characters?_**

- `awk 'length($0) > 79'` file

**_232.What the lsof command does? Have you used it? What for?_**

- The lsof command in Unix-like operating systems stands for "LiSt Open Files." Its primary function is to report a comprehensive list of all files that are currently open by active processes on the system.

- I have used `lsof` for powerful troubleshooting and system monitoring

- Used it for:
  - Finding which process is using a file
  - Identifying network connections and ports
  - Listing files opened by a specific user or command
  - Finding deleting files still held open
 
**_233.What is the difference between find and locate?_**

- Use locate when you need a fast, system-wide search for a file by name and you don't need real-time accuracy (e.g., finding a configuration file you know exists).
  - Example: `locate httpd.conf`
- Use find when you need real-time accuracy or when you need to search based on complex criteria other than just the name.
  - Example : `find /var/log -size +10M -mtime -7`
 
**_234.How a user process performs a privileged operation, such as reading from the disk?_**

- Using system calls

## System Call

**_235.What is a system call? What system calls are you familiar with?_**

- A system call is the programmatic way a computer program requests a service from the operating system kernel.

- Some common Linux system calls are:
  - Process Control:
    - `fork()`: Creates a new process (a child process).
    - `execve()`: Replaces the current process image with a new program.
    - `wait()`/`wait4()`: Waits for a child process to terminate or stop.
    - `exit()`: Terminates the calling process.
    - `getpid()`: Gets the process ID of the current process
      
  - File Management (I/O):
    - `open()`/`openat()`: Opens or creates a file, returning a file descriptor.
    - `read()`: Reads data from a file descriptor.
    - `write()`: Writes data to a file descriptor.
    - `close()`: Closes a file descriptor.
    - `lseek()`: Changes the file offset (position) of a file descriptor.

  - Memory Management:
    - `brk()` / `sbrk()`: Changes the program's data segment size (heap allocation).
    - `mmap()`: Maps files or devices into memory.

  - Device Management / Information:
    - `ioctl()`: Performs device-specific I/O operations.
    - `stat()` / `fstat()` / `lstat()`: Gets file or file descriptor metadata (e.g., size, permissions).
    - `time()` / `gettimeofday()`: Gets the system time.
   
**_236.How a program executes a system call?_**

- A program executes a trap instruction. The instruction jump into the kernel while raising the privileged level to kernel space.
- Once in kernel space, it can perform any privileged operation
- Once it's finished, it calls a "return-from-trap" instruction which returns to user space while reducing back the privilege level to user space.

**_237.Explain the fork() system call._**

- `fork()` is used for creating a new process. It does so by cloning the calling process but the child process has its own PID and any memory locks, I/O operations and semaphores are not inherited.

**_238.What is the return value of fork()?_**

- On success, the PID of the child process in parent and 0 in child process
- On error, -1 in the parent

**_239.Name one reason for fork() to fail._**

- Not enough memory to create a new process

**_240.Why do we need the wait() system call?_**

- `wait()` is used by a parent process to wait for the child process to finish execution. If wait is not used by a parent process then a child process might become a zombie process.

**_241.How the kernel notifies the parent process about child process termination?_**

- The kernel notifies the parent by sending the SIGCHLD to the parent.

**_242.How the waitpid() is different from wait()?_**

- The `waitpid()` is a non-blocking version of the wait() function.
- It also supports using library routine (e.g. `system()`) to wait a child process without messing up with other children processes for which the process has not waited.

**_243.True or False? The wait() system call won't return until the child process has run and exited._**

- True in most cases though there are cases where wait() returns before the child exits.

**_244.Explain the exec() system call._**

- It transforms the current running program into another program.
- Given the name of an executable and some arguments, it loads the code and static data from the specified executable and overwrites its current code segment and current static code data. After initializing its memory space (like stack and heap) the OS runs the program passing any arguments as the argv of that process.

**_245.True or False? A successful call to exec() never returns._**

- True
- Since a successful exec replace the current process, it can't return anything to the process that made the call.

**_246.What system call is used for listing files?_**

- There is no single system call that directly returns a list of files.

- Listing files (reading directory contents) is typically accomplished in Linux using a sequence of operations based on these system calls:
  - `open()` or `openat()`: Opens the directory, returning a file descriptor.
  - `getdents()` (Get Directory Entries): This is the primary system call used to read raw directory entries from the file descriptor obtained in step 1.
  - close(): Closes the directory file descriptor.

- In standard C programming, the `readdir()` function (part of the C library) is the wrapper that internally uses the `getdents()` system call to read and format the directory information for the user program.

**_247.What system calls are used for creating a new process?_**

- `fork()`, `exec()` and the `wait()` system call is also included in this workflow.

**_248.What execve() does?_**

- Executes a program. The program is passed as a filename (or path) and must be a binary executable or a script.

**_249.What is the return value of malloc?_**

- The return value of `malloc()` is a pointer of type `void*` (a "pointer to void").
  - This pointer points to the beginning of the block of newly allocated, uninitialized memory on the heap.
  - The `void*` type indicates that it's a generic pointer; it must be cast to the appropriate data type before being used (e.g., to `int*` or `struct Node*`).
- On Failure:
- If the requested memory allocation fails (e.g., due to insufficient memory), `malloc()` returns a null pointer ($\text{NULL}$). Always check for a $\text{NULL}$ return value.

**_250.Explain the pipe() system call. What does it used for?_**

- "Pipes provide a unidirectional interprocess communication channel. A pipe has a read end and a write end. Data written to the write end of a pipe can be read from the read end of the pipe. A pipe is created using pipe(2), which returns two file descriptors, one referring to the read end of the pipe, the other referring to the write end."

**_251.What happens when you execute `ls -l`?_**

- Shell reads the input using getline() which reads the input file stream and stores into a buffer as a string
- The buffer is broken down into tokens and stored in an array this way: {"ls", "-l", "NULL"}
- Shell checks if an expansion is required (in case of ls *.c)
- Once the program in memory, its execution starts. First by calling readdir()

- Notes:
  - `getline()` originates in GNU C library and used to read lines from input stream and stores those lines in the buffer
 
**_252.What happens when you execute ls -l *.log?_**

- When you execute ls -l *.log:
  - Shell Expansion: The shell (e.g., Bash) first replaces `*.log` with the list of all matching filenames (e.g., `a.log`, `b.log`) in the current directory.
  - Command Execution: The shell executes the `ls` command with the `-l` (long listing) option and the expanded file list as arguments.
  - Result: `ls` uses system calls (like `stat()`) to retrieve and print detailed metadata (permissions, size, owner, time) for each file ending in `.log`.
 
**_253.What readdir() system call does?_**

- The function `readdir()` (part of the C standard library, not a direct system call itself) is used to read the contents of a directory.

- It repeatedly calls the underlying  `getdents()` system call to return information about the next file or directory entry (name, inode number, etc.) within a directory stream.

**_254.What exactly the command alias x=y does?_**

- The command `alias x=y` creates a temporary shortcut where the string `x` is replaced with the string `y` by the shell (e.g., Bash) whenever x is executed as the first word of a command.
  - `x` is the alias name (the new command).
  - `y` is the replacement string (the actual command or commands to execute).

- This alias only persists for the current shell session.

**_255.Why running a new program is done using the fork() and exec() system calls? why a different API wasn't developed where there is one call to run a new program?_**

- This way provides a lot of flexibility. It allows the shell for example, to run code after the call to `fork()` but before the call to `exec()`. Such code can be used to alter the environment of the program it about to run.

**_256.Describe shortly what happens when you execute a command in the shell._**

- The shell figures out, using the PATH variable, where the executable of the command resides in the filesystem. It then calls `fork()` to create a new child process for running the command. Once the fork was executed successfully, it calls a variant of `exec()` to execute the command and finally, waits the command to finish using `wait()`. When the child completes, the shell returns from `wait()` and prints out the prompt again.


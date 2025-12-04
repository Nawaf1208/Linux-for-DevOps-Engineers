# Linux-Questions

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

**_77.What is stored in `~/.ssh/known_hosts`?_*

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

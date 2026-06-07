# Linux Q & A

![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)

![](Linux.png)

## Linux 101

<details>
<summary><b><i>1.What is Linux?</i></b></summary>

$\color{green}{\text{Answer}}$
  
- Wikipedia: "Linux is a family of open-source Unix-like operating systems based on the Linux kernel, an operating system kernel first released on September 17, 1991, by Linus Torvalds. Linux is typically packaged in a Linux distribution."

- Red Hat: "Linux® is an open source operating system (OS). An operating system is the software that directly manages a system’s hardware and resources, like CPU, memory, and storage. The OS sits between applications and hardware and makes the connections between all of your software and the physical resources that do the work."

</details>

<details>
<summary><b><i>2.Explain what each of the following commands does and give an example on how to use it:</i></b></summary>

$\color{green}{\text{Answer}}$

- `touch` - update file's timestamp. More commonly used for creating files
- `ls` - listing files and directories
- `rm` - remove files and directories
- `cat` - create, view and concatenate files
- `cp` - copy files and directories
- `mkdir` - create directories
- `pwd` - print current working directory (= at what path the user currently located)
- `cd` - change directory

</details>

<details>
<summary><b><i>3.What each of the following commands does?</i></b></summary>

$\color{green}{\text{Answer}}$

- `cd /`  --> change to the root directory
- `cd ~`  --> change to your home directory
- `cd`    --> change to your home directory
- `cd ..` --> change to the directory above your current i.e parent directory
- `cd .`  --> change to the directory you currently in
- `cd -`  --> change to the last visited path

</details>

<details>
<summary><b><i>4.Some of the commands in the previous question can be run with the -r/-R flag. What does it do? Give an example to when you would use it.</i></b></summary>

$\color{green}{\text{Answer}}$

- The `-r` (or -R in some commands) flag allows the user to run a certain command recursively. For example, listing all the files under the following tree is possible when done recursively (`ls -R`):

- /dir1/ dir2/ file1 file2 dir3/ file3

-  To list all the files, one can run `ls -R /dir1`

</details>

<details>
<summary><b><i>5.Explain each field in the output of `ls -l` command.</i></b></summary>

$\color{green}{\text{Answer}}$

- It shows a detailed list of files in a long format. From the left:
  - file permissions, number of links, owner name, owner group, file size, timestamp of last modification and directory/file name

</details>
 
<details>
<summary><b><i>6.What are hidden files/directories? How to list them?</i></b></summary>

$\color{green}{\text{Answer}}$

- These are files directly not displayed after performing a standard ls direct listing. An example of these files are .bashrc which are used to execute some scripts. Some also store configuration about services on your host like .KUBECONFIG. The command used to list them is, `ls -a`

</details>

<details>
<summary><b><i>7.What do `>` and `<` do in terms of input and output for programs?</i></b></summary>

$\color{green}{\text{Answer}}$

- They take in input (<) and output for a given file (>) using stdin and stdout.
  - `myProgram < input.txt > executionOutput.txt`

</details>
 
<details>
<summary><b><i>8.Explain what each of the following commands does and give an example on how to use it:</i></b></summary>

$\color{green}{\text{Answer}}$

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

</details>

<details>
<summary><b><i>9.How to rename the name of a file or a directory?</i></b></summary>

$\color{green}{\text{Answer}}$

Using the `mv` command.

</details>

<details>
<summary><b><i>10.Specify which command would you use (and how) for each of the following scenarios</i></b></summary>

$\color{green}{\text{Answer}}$

- `rm -rf dir` --> Remove a directory with files
- `cat or less` --> Display the content of a file
- `chmod 777 /tmp/x` --> Provides access to the file /tmp/x for everyone
- `cd ~` --> Change working directory to user home directory
- `sed -i s/good/great/g /tmp/y` --> Replace every occurrence of the word "good" with "great" in the file /tmp/y

</details>

<details>
<summary><b><i>11.How can you check what is the path of a certain command?</i></b></summary>

$\color{green}{\text{Answer}}$

`whereis`
`which`

</details>

<details>
<summary><b><i>12. What is the difference between these two commands? Will it result in the same output?</i></b></summary>

$\color{green}{\text{Answer}}$

`echo hello world`
`echo "hello world"`

- The echo command receives two separate arguments in the first execution and in the second execution it gets one argument which is the string "hello world". The output will be the same.

</details>

<details>
<summary><b><i>13.Explain piping. How do you perform piping?</i></b></summary>

$\color{green}{\text{Answer}}$

Using a pipe in Linux, allows you to send the output of one command to the input of another command. For example: `cat /etc/services | wc -l`

</details>

<details>
<summary><b><i>14.Fix the following commands:</i></b></summary>

$\color{green}{\text{Answer}}$

- sed "s/1/2/g' /tmp/myFile --> `sed 's/1/2/g' /tmp/myFile  # sed "s/1/2/g" is also fine`
- find . -iname *.yaml -exec sed -i "s/1/2/g" {} ; --> `find . -iname "*.yaml" -exec sed -i "s/1/2/g" {} \;`

</details>

<details>
<summary><b><i>15.How to check which commands you executed in the past?</i></b></summary>

$\color{green}{\text{Answer}}$

- history command or .bash_history file
  - also can use up arrow key to access or to show the recent commands you type
 
</details>

<details>
<summary><b><i>16.Running the command `df` you get "command not found". What could be wrong and how to fix it?</i></b></summary>

$\color{green}{\text{Answer}}$

- Most likely the default/generated $PATH was somehow modified or overridden thus not containing `/bin/` where df would normally go. This issue could also happen if bash_profile or any configuration file of your interpreter was wrongly modified, causing erratics behaviours. You would solve this by fixing your $PATH variable:

- As to fix it there are several options:
  1. Manually adding what you need to your $PATH PATH="$PATH":/user/bin:/..etc
  2. You have your weird env variables backed up.
  3. You would look for your distro default $PATH variable, copy paste using method #1

- Note: There are many ways of getting errors like this: if bash_profile or any configuration file of your interpreter was wrongly modified; causing erratics behaviours, permissions issues, bad compiled software (if you compiled it by yourself)... there is no answer that will be true 100% of the time.

</details>

<details>
<summary><b><i>17.How do you schedule tasks periodically?</i></b></summary>

$\color{green}{\text{Answer}}$

- You can use the commands `cron` and `at`. With cron, tasks are scheduled using the following format:

- `*/30 * * * * bash myscript.sh` Executes the script every 30 minutes.

- The tasks are stored in a cron file, you can write in it using `crontab -e`

- Alternatively if you are using a distro with systemd it's recommended to use systemd timers.

</details>

## I/O Redirection

<details>
<summary><b><i>18.Explain Linux I/O redirection</i></b></summary>

$\color{green}{\text{Answer}}$

In Linux, IO redirection is a way of changing the default input/output behavior of a command or program. It allows you to redirect input and output from/to different sources/destinations, such as files, devices, and other commands.

Here are some common examples of IO redirection:
  - Redirecting Standard Output (stdout): `ls > filelist.txt`
  - Redirection Standard Error (stderr): `ls /some/nonexistent/directory 2> error.txt`
  - Appending to a file: `echo "hello" >> myfile.txt`
  - Redirecting Input (stdin): `sort < unsorted.txt`
  - Using Pipes: Pipes ("|"): `ls | grep ".txt$"`

</details>

<details>
<summary><b><i>19.Demonstrate Linux output redirection</i></b></summary>

$\color{green}{\text{Answer}}$

`ls > ls_output.txt`

</details>

<details>
<summary><b><i>20.Demonstrate Linux stderr output redirection</i></b></summary>

$\color{green}{\text{Answer}}$

`yippiekaiyay 2> ls_output.txt`

</details>
 
<details>
<summary><b><i>21.Demonstrate Linux stderr to stdout redirection</i></b></summary>

$\color{green}{\text{Answer}}$

`yippiekaiyay &> file`

</details>

<details>
<summary><b><i>22.What is the result of running the following command? `yippiekaiyay 1>&2 die_hard`</i></b></summary>

$\color{green}{\text{Answer}}$

- An output similar to: `yippikaiyay: command not found...`
- The file `die_hard` will not be created

</details>

## Filesystem Hierarchy Standard

<details>
<summary><b><i>23.In Linux FHS (Filesystem Hierarchy Standard) what is the `/`?</i></b></summary>

$\color{green}{\text{Answer}}$

The root of the filesystem. The beginning of the tree.

</details>

<details>
<summary><b><i>24.What is stored in each of the following paths?</i></b></summary>

$\color{green}{\text{Answer}}$

- `/bin, /sbin, /usr/bin and /usr/sbin` -> binaries
- `/etc` -> configuration files
- `/home` -> home directories of the different users
- `/var` -> files that tend to change and be modified like logs
- `/tmp` -> temporary files

</details>

<details>
<summary><b><i>25.What is special about the /tmp directory when compared to other directories?</i></b></summary>

$\color{green}{\text{Answer}}$

`/tmp` folder is cleaned automatically, usually upon reboot.

</details>

<details>
<summary><b><i>26.What kind of information one can find in /proc?</i></b></summary>

$\color{green}{\text{Answer}}$

It contains useful information about the processes that are currently running, it is regarded as control and information center for kernel.

</details>

<details>
<summary><b><i>27.What makes /proc different from other filesystems?</i></b></summary>

$\color{green}{\text{Answer}}$

`/proc` is a special virtual filesystem in Unix-like operating systems, including Linux, that provides information about processes and system resources.

</details>

<details>
<summary><b><i>28.True or False? only root can create files in /proc</i></b></summary>

$\color{green}{\text{Answer}}$

False. No one can create file in `/proc` directly (certain operations can lead to files being created in /proc by the kernel).

</details>

<details>
<summary><b><i>29.What can be found in /proc/cmdline?</i></b></summary>

$\color{green}{\text{Answer}}$

The command passed to the boot loader to run the kernel

</details>

<details>
<summary><b><i>30.In which path can you find the system devices (e.g. block storage)?</i></b></summary>

$\color{green}{\text{Answer}}$

`/dev`

</details>

## Permissions

<details>
<summary><b><i>31.How to change the permissions of a file?</i></b></summary>

$\color{green}{\text{Answer}}$

Using the `chmod` command.

</details>

<details>
<summary><b><i>32.What does the following permissions mean?</i></b></summary>

$\color{green}{\text{Answer}}$

- `777` -> You give the owner, group and other: Execute (1), Write (2) and Read (4); 4+2+1 = 7.
- `644` -> Owner has Read (4), Write (2), 4+2 = 6; Group and Other have Read (4).
- `750` -> Owner has x+r+w, Group has Read (4) and Execute (1); 4+1 = 5. Other have no permissions.

</details>

<details>
<summary><b><i>33.What this command does? `chmod +x some_file`</i></b></summary>

$\color{green}{\text{Answer}}$

It adds execute permissions to all sets i.e user, group and others.

</details>

<details>
<summary><b><i>34.Explain what is setgid and setuid</i></b></summary>

$\color{green}{\text{Answer}}$

`setuid` is a linux file permission that permits a user to run a file or program with the permissions of the owner of that file. This is possible by elevation of current user privileges.

`setgid` is a process when executed will run as the group that owns the file.

</details>

<details>
<summary><b><i>35.What is the purpose of sticky bit?</i></b></summary>

$\color{green}{\text{Answer}}$

Its a bit that only allows the owner or the root user to delete or modify the file.

</details>

<details>
<summary><b><i>36.What the following commands do?</i></b></summary>

$\color{green}{\text{Answer}}$

- `chmod` - changes access permissions to files system objects
- `chown` - changes the owner of file system files and directories
- `chgrp` - changes the group associated with a file system object

</details>

<details>
<summary><b><i>37.What is sudo? How do you set it up?</i></b></summary>

$\color{green}{\text{Answer}}$

- sudo is a command-line utility in Unix-like operating systems that allows users to run programs with the privileges of another user, usually the superuser (root). It stands for "superuser do.

- The sudo program is installed by default in almost all Linux distributions. If you need to install sudo in Debian/Ubuntu, use the command apt-get install sudo

</details>

<details>
<summary><b><i>38.True or False? In order to install packages on the system one must be the root user or use the sudo command</i></b></summary>

$\color{green}{\text{Answer}}$

True

</details>

<details>
<summary><b><i>39.Explain what are ACLs. For what use cases would you recommend to use them?</i></b></summary>

$\color{green}{\text{Answer}}$

- An Access Control List (ACL) is a set of rules that determines which users or systems are granted or denied access to a specific resource, such as a file, directory, or network.

- They are used to enforce granular security policies, and recommended use cases include managing file and directory permissions, controlling network traffic, and securing API access. 

</details>

<details>
<summary><b><i>40.You try to create a file but it fails. Name at least three different reason as to why it could happen</i></b></summary>

$\color{green}{\text{Answer}}$

- No more disk space
- No more inodes
- No permissions

</details>

<details>
<summary><b><i>41.A user accidentally executed the following `chmod -x $(which chmod)`. How to fix it?</i></b></summary>

$\color{green}{\text{Answer}}$

Using `sudo setfacl -m u::rx /usr/bin/chmod` will set the execute permissions on `chmod` for all the users. Post this, the `chmod` binary can be used as usual.

</details>

## Scenarios

<details>
<summary><b><i>42.You would like to copy a file to a remote Linux host. How would you do?</i></b></summary>

$\color{green}{\text{Answer}}$

There are multiple ways to transfer files between hosts. Personal opinion: use `rsync`

</details>

<details>
<summary><b><i>43.How to generate a random string?</i></b></summary>

$\color{green}{\text{Answer}}$

One way is to run the following: `cat /proc/sys/kernel/random/uuid`

</details>

<details>
<summary><b><i>44.How to generate a random string of 7 characters?</i></b></summary>

$\color{green}{\text{Answer}}$

- `mkpasswd -l 7`

</details>

## Systemd

<details>
<summary><b><i>45.What is systemd?</i></b></summary>

$\color{green}{\text{Answer}}$

- Systemd is a daemon (System 'd', d stands for daemon).

- A daemon is a program that runs in the background without direct control of the user, although the user can at any time talk to the daemon.

</details>

<details>
<summary><b><i>46.How to start or stop a service?</i></b></summary>

$\color{green}{\text{Answer}}$

- To start a service: `systemctl start <service name>`
- To stop a service: `systemctl stop <service name>`

</details>

<details>
<summary><b><i>47.How to check the status of a service?</i></b></summary>

$\color{green}{\text{Answer}}$

- `systemctl status <service name>`

</details>

<details>
<summary><b><i>48.On a system which uses systemd, how would you display the logs?</i></b></summary>

$\color{green}{\text{Answer}}$

- `journalctl`

</details>

<details>
<summary><b><i>49.Describe how to make a certain process/app a service</i></b></summary>

$\color{green}{\text{Answer}}$

- Create a new file with a .service extension in /etc/systemd/system/.
  - For example, my-app.service.
    - `sudo nano /etc/systemd/system/my-app.service`
   
- Populate the .service file with the necessary configurations. A basic unit file includes:
  ```Linux
  [Unit]
  Description=My Custom Application Service
  After=network.target

  [Service]
  ExecStart=/path/to/your/application/executable
  WorkingDirectory=/path/to/your/application/directory
  User=your_username
  Restart=always
  RestartSec=5
 
  [Install]
  WantedBy=multi-user.target
  ```

</details>

## Troubleshooting and Debugging

<details>
<summary><b><i>50.Where system logs are located?</i></b></summary>

$\color{green}{\text{Answer}}$

- `/var/log`

</details>

<details>
<summary><b><i>51.How to follow file's content as it being appended without opening the file every time?</i></b></summary>

$\color{green}{\text{Answer}}$

- `tail -f <file_name>`

</details>

<details>
<summary><b><i>52.What are you using for troubleshooting and debugging network issues?</i></b></summary>

$\color{green}{\text{Answer}}$

- `dstat -t` is great for identifying network and disk issues. 
- `netstat -tnlaup` can be used to see which processes are running on which ports.
- `lsof -i -P` can be used for the same purpose as netstat.
- `ngrep -d any metafilter` for matching regex against payloads of packets.
- `tcpdump` for capturing packets.
- `wireshark` same concept as tcpdump but with GUI (optional).

</details>

<details>
<summary><b><i>53.What are you using for troubleshooting and debugging disk & file system issues?</i></b></summary>

$\color{green}{\text{Answer}}$

- `dstat -t` is great for identifying network and disk issues.
- `opensnoop` can be used to see which files are being opened on the system (in real time).

</details>

<details>
<summary><b><i>54.What are you using for troubleshooting and debugging process issues?</i></b></summary>

$\color{green}{\text{Answer}}$

- `strace` is great for understanding what your program does. It prints every system call your program executed.

</details>

<details>
<summary><b><i>55.What are you using for debugging CPU related issues?</i></b></summary>

$\color{green}{\text{Answer}}$

- `top` will show you how much CPU percentage each process consumes
- `perf` is a great choice for sampling profiler and in general, figuring out what your CPU cycles are "wasted" on `flamegraphs` is great for CPU consumption visualization

</details>

<details>
<summary><b><i>56.You get a call from someone claiming "my system is SLOW". What do you do?</i></b></summary>

$\color{green}{\text{Answer}}$

- Check with `top` for anything unusual
- Run `dstat -t` to check if it's related to disk or network.
- Check if it's network related with `sar`
- Check I/O stats with `iostat`

</details>

<details>
<summary><b><i>57.Explain iostat output</i></b></summary>

$\color{green}{\text{Answer}}$

- The `iostat` command in Linux provides input/output statistics for devices and CPU utilization.

</details>

<details>
<summary><b><i>58.How to debug binaries?</i></b></summary>

$\color{green}{\text{Answer}}$

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

</details>

<details>
<summary><b><i>59.What is the difference between CPU load and utilization?</i></b></summary>

$\color{green}{\text{Answer}}$

- CPU utilization is the percentage of time a CPU is actively busy, while CPU load is the number of processes either actively using the CPU or waiting to use it.

</details>

<details>
<summary><b><i>60.How you measure time execution of a program?</i></b></summary>

$\color{green}{\text{Answer}}$

- `time` command

</details>

### Scenario

<details>
<summary><b><i>61.You have a process writing to a file. You don't know which process exactly, you just know the path of the file. You would like to kill the process as it's no longer needed. How would you achieve it?</i></b></summary>

$\color{green}{\text{Answer}}$

- Run `lsof <FILE_PATH>`
- Use the pid (process ID) from the lsof command and run `kill <PID>`

</details>

## Kernel

<details>
<summary><b><i>62.What is a kernelm and what does it do?</i></b></summary>

$\color{green}{\text{Answer}}$

The kernel is part of the operating system and is responsible for tasks like:
  - Allocating memory
  - Schedule processes
  - Control CPU

</details>

<details>
<summary><b><i>63.How do you find out which Kernel version your system is using?</i></b></summary>

$\color{green}{\text{Answer}}$

`uname -a` command

</details>

<details>
<summary><b><i>64.What is a Linux kernel module and how do you load a new module?</i></b></summary>

$\color{green}{\text{Answer}}$

A Linux kernel module is a piece of code that can be dynamically loaded into the kernel to extend its functionality. These modules are typically used to add support for hardware devices, filesystems, or system calls. The kernel itself is monolithic, but with modules, its capabilities can be extended without having to reboot the system or recompile the entire kernel.

</details>

<details>
<summary><b><i>65.Explain user space vs. kernel space</i></b></summary>

$\color{green}{\text{Answer}}$

The operating system executes the kernel in protected memory to prevent anyone from changing (and risking it crashing). This is what is known as "Kernel space". "User space" is where users executes their commands or applications. It's important to create this separation since we can't rely on user applications to not tamper with the kernel, causing it to crash.

</details>

<details>
<summary><b><i>66.In what phases of kernel lifecycle, can you change its configuration?</i></b></summary>

$\color{green}{\text{Answer}}$

- Build time (when it's compiled)
- Boot time (when it starts)
- Runtime (once it's already running)

</details>

<details>
<summary><b><i>67.Where can you find kernel's configuration?</i></b></summary>

$\color{green}{\text{Answer}}$

Usually it will reside in `/boot/config-<kernel version>.<os release>.<arch>`

</details>

<details>
<summary><b><i>68.Where can you find the file that contains the command passed to the boot loader to run the kernel?</i></b></summary>

$\color{green}{\text{Answer}}$

`/proc/cmdline`

</details>

<details>
<summary><b><i>69.How to list kernel's runtime parameters?</i></b></summary>

$\color{green}{\text{Answer}}$

`sysctl -a`

</details>

<details>
<summary><b><i>70.Will running sysctl -a as a regular user vs. root, produce different result?</i></b></summary>

$\color{green}{\text{Answer}}$

Yes, you might notice that in most systems, when running `systctl -a` with root, you'll get more runtime parameters compared to executing the same command with a regular user.

</details>

<details>
<summary><b><i>71.You would like to enable IPv4 forwarding in the kernel, how would you do it?</i></b></summary>

$\color{green}{\text{Answer}}$

- `sudo sysctl net.ipv4.ip_forward=1`

- To make it persistent (applied after reboot for example): insert `net.ipv4.ip_forward = 1` into `/etc/sysctl.conf`

- Another way to is to run `echo 1 | sudo tee /proc/sys/net/ipv4/ip_forward`

</details>

<details>
<summary><b><i>72.How `sysctl` applies the changes to kernel's runtime parameters the moment you run sysctl command?</i></b></summary>

$\color{green}{\text{Answer}}$

- If you `strace` the sysctl command you can see it does it by changing the file under /proc/sys/...

- In the past it was done with sysctl system call, but it was deprecated at some point.

</details>

<details>
<summary><b><i>73.How changes to kernel runtime parameters persist? (applied even after reboot to the system for example)</i></b></summary>

$\color{green}{\text{Answer}}$

There is a service called `systemd-sysctl` that takes the content of `/etc/sysctl.conf` and applies it. This is how changes persist, even after reboot, when they are written in `/etc/sysctl.conf`

</details>

<details>
<summary><b><i>74.Are the changes you make to kernel parameters in a container, affects also the kernel parameters of the host on which the container runs?</i></b></summary>

$\color{green}{\text{Answer}}$

No. Containers have their own `/proc` filesystem so any change to kernel parameters inside a container, are not affecting the host or other containers running on that host.

</details>

## SSH

<details>
<summary><b><i>75.What is SSH? How to check if a Linux server is running SSH?</i></b></summary>

$\color{green}{\text{Answer}}$

- Wikipedia Definition: "SSH or Secure Shell is a cryptographic network protocol for operating network services securely over an unsecured network."

- Hostinger.com Definition: "SSH, or Secure Shell, is a remote administration protocol that allows users to control and modify their remote servers over the Internet."

- An SSH server will have SSH daemon running. Depends on the distribution, you should be able to check whether the service is running (e.g. `systemctl status sshd`).

</details>

<details>
<summary><b><i>76.Why SSH is considered better than telnet?</i></b></summary>

$\color{green}{\text{Answer}}$

Telnet also allows you to connect to a remote host but as opposed to SSH where the communication is encrypted, in telnet, the data is sent in clear text, so it doesn't considered to be secured because anyone on the network can see what exactly is sent, including passwords.

</details>

<details>
<summary><b><i>77.What is stored in `~/.ssh/known_hosts`?</i></b></summary>

$\color{green}{\text{Answer}}$

The file stores the key fingerprints for the clients connecting to the SSH server. This fingerprint creates a trust between the client and the server for future SSH connections.

</details>

<details>
<summary><b><i>78.You try to ssh to a server and you get "Host key verification failed". What does it mean?</i></b></summary>

$\color{green}{\text{Answer}}$

It means that the key of the remote host was changed and doesn't match the one that stored on the machine (in `~/.ssh/known_hosts`).

</details>

<details>
<summary><b><i>79.What is the difference between SSH and SSL?</i></b></summary>

$\color{green}{\text{Answer}}$

SSH (Secure Shell) and SSL (Secure Sockets Layer) are both cryptographic protocols for secure communication, but they serve fundamentally different purposes. SSH is primarily used for secure remote access and command execution, while SSL/TLS is used to secure data in transit between a website and a user's browser

</details>

<details>
<summary><b><i>80.What `ssh-keygen` is used for?</i></b></summary>

$\color{green}{\text{Answer}}$

ssh-keygen is a tool to generate an authentication key pair for SSH, that consists of a private and a public key. It supports a number of algorithms to generate authentication keys :
  - dsa
  - ecdsa
  - ecdsa-sk
  - ed25519
  - ed25519-sk
  - rsa (default)

One can also specify number of bits in key. Command below generates an SSH key pair with RSA 4096-bits :
  - `$ ssh-keygen -t rsa -b 4096`

The output looks like this:
  - Generating public/private rsa key pair.
  - Enter file in which to save the key (/home/user/.ssh/id_rsa):
  - Enter passphrase (empty for no passphrase):
  - Enter same passphrase again:
  - Your identification has been saved in /home/user/.ssh/id_rsa
  - Your public key has been saved in /home/user/.ssh/id_rsa.pub
  - The key fingerprint is:
  - SHA256:f5MOGnhzYfC0ZCHvbSXXiRiNVYETjxpHcXD5xSojx+M user@mac-book-pro
  - The key's randomart image is:
    ```Linux
    +---[RSA 4096]----+
    |        . ..+***o|
    |         o o++*o+|
    |        . =+.++++|
    |         B.oX+. .|
    |        S *=o+   |
    |       . o oE.   |
    |      . + + +    |
    |       . = + .   |
    |        .   .    |
    +----[SHA256]-----+
    ```

One can check how many bits an SSH key has with :
  - `$ ssh-keygen -l -f /home/user/.ssh/id_rsa`
 
Output should look like this :
  - `4096 SHA256:f5MOGnhzYfC0ZCHvbSXXiRiNVYETjxpHcXD5xSojx+M user@mac-book-pro (RSA)`

It shows the key is RSA 4096-bits.

`-l` and `-f` parameters usage explanation :
  - `l Show the fingerprint of the key file.`
  - `f filename Filename of the key file.`

</details>

<details>
<summary><b><i>81.What is SSH port forwarding?</i></b></summary>

$\color{green}{\text{Answer}}$

SSH port forwarding, also known as SSH tunneling, is a powerful technique that redirects network traffic through an encrypted SSH connection. This creates a secure "tunnel" that allows you to safely transmit data, bypass firewalls, and access services that might otherwise be unavailable. 

</details>

## Globbing & Wildcards

<details>
<summary><b><i>82.What is Globbing?</i></b></summary>

$\color{green}{\text{Answer}}$

Globbing is the mechanism used by the shell (like Bash) to expand wildcard characters in a command line into a list of matching file and directory names. This process happens before the command (such as `ls`, `cp`, or `rm`) actually runs, allowing users to perform operations on multiple files with a single, concise pattern.

</details>

<details>
<summary><b><i>83.What are wildcards? Can you give an example of how to use them?</i></b></summary>

$\color{green}{\text{Answer}}$

Wildcards are special symbols used during a process called globbing to represent one or more characters when matching file or directory names in the command line. They are essential tools for managing files efficiently, allowing you to perform actions on groups of files without typing each name individually.

</details>

<details>
<summary><b><i>84.Explain what will `ls [XYZ]` match</i></b></summary>

$\color{green}{\text{Answer}}$

- The command `ls [XYZ]` uses a wildcard pattern that leverages square brackets ([]) to perform filename matching (globbing).
- The pattern `[XYZ]` specifically matches any single character that is either an X, a Y, or a Z exactly where the bracket pattern appears in the filename.

</details>

<details>
<summary><b><i>85.Explain what will `ls [^XYZ]` match</i></b></summary>

$\color{green}{\text{Answer}}$

- The command `ls [^XYZ]` utilizes a globbing pattern in Linux that uses the caret (`^`) character inside square brackets to perform negation.
- The pattern `[^XYZ]` matches any single character file name in the current directory that is not an `X`, `Y`, or `Z`.

</details>

<details>
<summary><b><i>86.Explain what will `ls [0-5]` match</i></b></summary>

$\color{green}{\text{Answer}}$

- The command `ls [0-5]` uses a standard Linux globbing pattern that leverages square brackets (`[]`) with a range definition.
- This pattern matches any single-character filename that is a digit between `0` and `5`, inclusive.

</details>

<details>
<summary><b><i>87.What each of the following matches</i></b></summary>

$\color{green}{\text{Answer}}$

- The `?` matches any single character
- The `*` matches zero or more characters

</details>

<details>
<summary><b><i>88.What do we grep for in each of the following commands?:</i></b></summary>

$\color{green}{\text{Answer}}$

- `grep '[0-9]{1,3}.[0-9]{1,3}.[0-9]{1,3}.[0-9]{1,3}' some_file` -> An IP address
- `grep -E "error|failure" some_file` -> The word "error" or "failure"
- `grep '[0-9]$' some_file` -> Lines which end with a number

</details>

<details>
<summary><b><i>89.Which line numbers will be printed when running `grep '\baaa\b'` on the following content:

```Linux
aaa bbb ccc.aaa aaaaaa
```

</i></b></summary>

$\color{green}{\text{Answer}}$

No Output

</details>

<details>
<summary><b><i>90.What is the difference single and double quotes?</i></b></summary>

$\color{green}{\text{Answer}}$

- In Linux shells (like Bash), both single quotes (`' '`) and double quotes (`" "`) are used to group strings and escape characters that would otherwise have special meaning (like spaces or wildcards).
- However, they differ fundamentally in one crucial way: single quotes disable all special meanings, while double quotes allow a select few special characters to remain active.
- This difference is often called "strong quoting" versus "weak quoting."

</details>

<details>
<summary><b><i>91.What is escaping? What escape character is used for escaping?</i></b></summary>

$\color{green}{\text{Answer}}$

- Escaping is the mechanism used to remove the special meaning from a character that would normally be interpreted by the shell

- The escape character used is the backslash (`\`).

</details>

<details>
<summary><b><i>92.What is an exit code? What exit codes are you familiar with?</i></b></summary>

$\color{green}{\text{Answer}}$

- An exit code (or return code) represents the code returned by a child process to its parent process.
- 0 is an exit code which represents success while anything higher than 1 represents error. Each number has different meaning, based on how the application was developed.

</details>

## Boot Process

<details>
<summary><b><i>93.Tell me everything you know about the Linux boot process.</i></b></summary>

$\color{green}{\text{Answer}}$

The Linux boot process is a highly choreographed sequence of events that transforms a powered-off computer into a fully operational system, passing control from low-level hardware firmware to the operating system's kernel and finally to user-space applications.

The process generally involves six major stages: 
  - 1. BIOS/UEFI (Firmware Initialization)
  - 2. Bootloader (GRUB)
  - 3. Kernel Initialization
  - 4. Initial RAM Disk (initramfs/initrd)
  - 5. Init Process (systemd)
  - 6. User Space and Login Prompt

</details>

<details>
<summary><b><i>94.What is GRUB2?</i></b></summary>

$\color{green}{\text{Answer}}$

GRUB2 (GRand Unified Bootloader version 2) is the standard and default bootloader for nearly all modern Linux distributions. It is the essential software that loads the Linux kernel (and initial RAM disk) into memory and transfers control to it, allowing the operating system to start.

</details>

<details>
<summary><b><i>95.What is Secure Boot?</i></b></summary>

$\color{green}{\text{Answer}}$

Secure Boot is a security standard and feature of the UEFI (Unified Extensible Firmware Interface) firmware designed to protect the computer's boot process from malicious software (like bootkits and rootkits) that tries to load during startup.

</details>

<details>
<summary><b><i>96.What can you find in /boot?</i></b></summary>

$\color{green}{\text{Answer}}$

The `/boot` directory in Linux contains the essential, static files required to start the system. The contents of this directory are read by the bootloader (like GRUB2) before the main operating system's configuration files in `/etc` are accessed.

</details>

## Disk and Filesystem

<details>
<summary><b><i>97.What's an inode?</i></b></summary>

$\color{green}{\text{Answer}}$

For each file (and directory) in Linux there is an inode, a data structure which stores meta data related to the file like its size, owner, permissions, etc.

</details>

<details>
<summary><b><i>98.Which of the following is not included in inode:
  
- Link count
- File size
- File name
- File timestamp

</i></b></summary>

$\color{green}{\text{Answer}}$

File name (it's part of the directory file)

</details>

<details>
<summary><b><i>99.How to check which disks are currently mounted?</i></b></summary>

$\color{green}{\text{Answer}}$

Run `mount`

</details>

<details>
<summary><b><i>100.You run the `mount` command but you get no output. How would you check what mounts you have on your system?</i></b></summary>

$\color{green}{\text{Answer}}$

`cat /proc/mounts`

</details>

<details>
<summary><b><i>101.What is the difference between a soft link and hard link?</i>/</b>/</summary>

$\color{green}{\text{Answer}}$

Hard link is the same file, using the same inode. Soft link is a shortcut to another file, using a different inode.

</details>

<details>
<summary><b><i>102.True or False? You can create an hard link for a directory</i></b></summary>

$\color{green}{\text{Answer}}$

False

</details>

<details>
<summary><b><i>103.True or False? You can create a soft link between different filesystems</i></b></summary>

$\color{green}{\text{Answer}}$

True

</details>

<details>
<summary><b><i>104.True or False? Directories always have by minimum 2 links</i></b></summary>

$\color{green}{\text{Answer}}$

True

</details>

<details>
<summary><b><i>105.What happens when you delete the original file in case of soft link and hard link?</i></b></summary>

$\color{green}{\text{Answer}}$

When the original file is deleted, a soft link breaks because it merely points to the file's path, while a hard link remains fully functional because it acts as an alternative name pointing directly to the data on the disk. The data is only truly deleted when the last hard link referencing it is removed.

</details>

<details>
<summary><b><i>106.Can you check what type of filesystem is used in /home?</i></b></summary>

$\color{green}{\text{Answer}}$

There are many answers for this question. One way is running `df -T`

</details>

<details>
<summary><b><i>107.What is a swap partition? What is it used for?</i></b></summary>

$\color{green}{\text{Answer}}$

A swap partition is a dedicated area on a Linux storage drive that the operating system uses as virtual memory when the physical RAM is full. The kernel moves inactive data from RAM to this slower disk space to free up memory for active applications, or to write the entire system state to disk during hibernation.

</details>

<details>
<summary><b><i>108.How to create a</i></b></summary>

$\color{green}{\text{Answer}}$

- new empty file -> `touch new_file.txt`
- a file with text (without using text editor) -> `cat > new_file [enter] submit text; ctrl + d to exit insert mode`
- a file with given size -> `truncate -s new_file.txt`

</details>

<details>
<summary><b><i>109.You are trying to create a new file but you get "File system is full". You check with df for free space and you see you used only 20% of the space. What could be the problem?</i></b></summary>

$\color{green}{\text{Answer}}$

- When you receive a "File system is full" error but df indicates plenty of free disk space, the problem is typically caused by exhausting all available inodes. In Linux filesystems, an inode is a metadata structure assigned to every file, storing information like ownership, permissions, and location on the disk, but not the file's actual data.
  
- While df reports on the usage of data blocks (the file content space), it doesn't always highlight inode usage. If a system has millions of extremely tiny files (e.g., temporary web cache files or session data), every single one consumes an inode. Once all inodes allocated for that specific partition are used up, the system cannot create any new files, regardless of how much physical storage space remains empty.

</details>

<details>
<summary><b><i>110.How would you check what is the size of a certain directory?</i></b></summary>

$\color{green}{\text{Answer}}$

`du -sh`

</details>

<details>
<summary><b><i>111.What is LVM?</i></b></summary>

$\color{green}{\text{Answer}}$

LVM (Logical Volume Management) is a powerful, flexible storage management system for Linux that provides an abstraction layer between the physical storage devices (hard disks, SSDs) and the filesystem partitions used by the operating system.

</details>

<details>
<summary><b><i>112.Explain the following in regards to LVM:</i></b></summary>

$\color{green}{\text{Answer}}$

- PV - A Physical Volume (PV) is the foundational layer of LVM. It is an actual, physical storage device or partition that has been initialized for use by LVM.

- VG - A Volume Group (VG) is the next layer up. It is a unified pool of storage space created by combining one or more Physical Volumes.

- LV - A Logical Volume (LV) is a "virtual partition" carved out from the storage pool provided by a Volume Group. This is the final layer that the operating system interacts with.

</details>

<details>
<summary><b><i>112.What is NFS? What is it used for?</i></b></summary>

$\color{green}{\text{Answer}}$

NFS (Network File System) is a distributed filesystem protocol in Linux that allows a user to access files and directories on a remote computer over a network as if they were stored locally on their own machine. 

</details>

<details>
<summary><b><i>113.What RAID is used for? Can you explain the differences between RAID 0, 1, 5 and 10?</i></b></summary>

$\color{green}{\text{Answer}}$

RAID (Redundant Array of Independent Disks) is a storage technology used in Linux and other operating systems that combines multiple physical disk drives into a single logical unit. Its primary purposes are to improve performance (speed), provide data redundancy (fault tolerance), or both. This allows administrators to optimize storage for specific needs, ranging from high-speed temporary storage to mission-critical, highly reliable data storage.

The primary differences lie in how data is distributed and protected:
  - RAID 0 (Striping) offers the fastest performance by splitting data across drives, but provides no data protection if a single drive fails.
  - RAID 1 (Mirroring) provides maximum safety by duplicating all data across drives, but halves the usable storage capacity and offers no performance benefit for writing.
  - RAID 5 balances performance and safety by using striping with a parity scheme, allowing for a single drive failure tolerance with minimal capacity overhead (requiring at least three drives).
  - RAID 10 (Striping and Mirroring) provides the best of both worlds—high performance and high fault tolerance—by combining mirrored pairs into a striped array, though at the cost of 50% usable capacity (requiring at least four drives).

</details>

<details>
<summary><b><i>114.Describe the process of extending a filesystem disk space</i></b></summary>

$\color{green}{\text{Answer}}$

Extending a filesystem's disk space in Linux involves several steps that must be performed sequentially, moving from the physical layer up to the logical layer. The exact process depends on whether you are using traditional disk partitions or LVM (Logical Volume Management), with LVM being the more flexible method. 

The General Process
  1. Add/Expand the Physical Disk Space: This is usually done at the hardware level (adding a new drive) or hypervisor level (expanding a virtual disk in VMware, AWS, etc.).
  2. Rescan the Kernel: The Linux kernel needs to recognize the new, unallocated space.
      - For a new disk, you might need to rescan the SCSI host: echo "- - -" > /sys/class/scsi_host/host[X]/scan.
      - For an expanded existing disk, a simple reboot often works, or you can force a rescan: echo 1 > /sys/block/sd[X]/device/rescan.
  3. Expand the Partition/Volume: This is where the process diverges based on your setup

</details>

<details>
<summary><b><i>115.What is lazy umount?</i></b></summary>

$\color{green}{\text{Answer}}$

Lazy unmount in Linux is a mechanism that allows you to immediately detach a filesystem from the system's directory hierarchy, even if it is currently "busy" (has open files or active processes using it). 

</details>

<details>
<summary><b><i>116.What is tmpfs?</i></b></summary>

$\color{green}{\text{Answer}}$

`tmpfs` (Temporary File System) is a type of volatile, in-memory filesystem used in Linux. It is a modern, faster alternative to the older `ramdisk` approach.

</details>

<details>
<summary><b><i>117.What is stored in each of the following logs?</i></b></summary>

$\color{green}{\text{Answer}}$

- `/var/log/messages` -> Stores general system activity, informational messages, and non-critical errors from the kernel and various daemons on Red Hat-based systems.
- `/var/log/boot.log` -> Contains a record of all events, service statuses, and console messages generated specifically during the system's boot process.

</details>

<details>
<summary><b><i>118.True or False? both /tmp and /var/tmp cleared upon system boot</i></b></summary>

$\color{green}{\text{Answer}}$

False. `/tmp` is cleared upon system boot while `/var/tmp` is cleared every a couple of days or not cleared at all (depends on distro).

</details>

## Performance Analysis

<details>
<summary><b><i>119.How to check what is the current load average?</i></b></summary>

$\color{green}{\text{Answer}}$

One can use `uptime` or `top`

</details>

<details>
<summary><b><i>120.You know how to see the load average, great. but what each part of it means? for example 1.43, 2.34, 2.78</i></b></summary>

$\color{green}{\text{Answer}}$

The Linux load average provides a snapshot of system demand and can typically be viewed using commands like `uptime`, `top`, or `htop`. It is represented by three numbers:

  - `load average: 1.43, 2.34, 2.78`

These three numbers represent the average number of processes that are either running or waiting to run (in a runnable state or uninterruptible sleep) over different time periods:

  - `Value	Time Period	      Meaning`
  - `1.43	  Last 1 minute	    The immediate system load average.`
  - `2.34	  Last 5 minutes    The intermediate system load average.`
  - `2.78	  Last 15 minutes	  The long-term system load average.`

</details>

<details>
<summary><b><i>121.How to check process usage?</i></b></summary>

$\color{green}{\text{Answer}}$

`pidstat`

</details>

<details>
<summary><b><i>122.How to check disk I/O?</i></b></summary>

$\color{green}{\text{Answer}}$

`iostat -xz 1`

</details>

<details>
<summary><b><i>123.How to check how much free memory a system has? How to check memory consumption by each process?</i></b></summary>

$\color{green}{\text{Answer}}$

You can use the commands `top` and `free`

</details>

<details>
<summary><b><i>124.How to check TCP stats?</i></b></summary>

$\color{green}{\text{Answer}}$

sar -n TCP,ETCP 1

</details>

## Processes

<details>
<summary><b><i>125.How to list all the processes running in your system?</i></b></summary>

$\color{green}{\text{Answer}}$

The "`ps`" command can be used to list all the processes running in a system. The "`ps aux`" command provides a detailed list of all the processes, including the ones running in the background.

</details>

<details>
<summary><b><i>126.How to run a process in the background and why to do that in the first place?</i></b></summary>

$\color{green}{\text{Answer}}$

You can achieve that by specifying & at the end of the command. As to why, since some commands/processes can take a lot of time to finish execution or run forever, you may want to run them in the background instead of waiting for them to finish before gaining control again in current session.

</details>

<details>
<summary><b><i>127.How can you find how much memory a specific process consumes?</i></b></summary>

$\color{green}{\text{Answer}}$

```Linux
mem()
{
ps -eo rss,pid,euser,args:100 --sort %mem | grep -v grep | grep -i $@ | awk '{printf $1/1024 "MB"; $1=""; print }'
}
```

</details>

<details>
<summary><b><i>128.What signal is used by default when you run 'kill *process id*'?</i></b></summary>

$\color{green}{\text{Answer}}$

The default signal is SIGTERM (15). This signal kills process gracefully which means it allows it to save current state configuration.

</details>

<details>
<summary><b><i>129.What signals are you familiar with?</i></b></summary>

$\color{green}{\text{Answer}}$

- SIGTERM -> default signal for terminating a process
- SIGHUP -> common usage is for reloading configuration
- SIGKILL -> a signal which cannot caught or ignored
- To view all available signals run `kill -l`

</details>

<details>
<summary><b><i>130.What kill 0 does?</i></b></summary>

$\color{green}{\text{Answer}}$

`kill 0` sends a signal to all processes in the current process group. It is used to check if the processes exist or not

</details>

<details>
<summary><b><i>131.What kill -0  does?</i></b></summary>

$\color{green}{\text{Answer}}$

`kill -0` checks if a process with a given process ID exists or not. It does not actually send any signal to the process.

</details>

<details>
<summary><b><i>132.What is a trap?</i></b></summary>

$\color{green}{\text{Answer}}$

A trap is a mechanism that allows the shell to intercept signals sent to a process and perform a specific action, such as handling errors or cleaning up resources before terminating the process.

</details>

<details>
<summary><b><i>133.Every couple of days, a certain process stops running. How can you look into why it's happening?</i></b></summary>

$\color{green}{\text{Answer}}$

One way to investigate why a process stops running is to check the system logs, such as the messages in `/var/log/messages` or `journalctl`. Additionally, checking the process's resource usage and system load may provide clues as to what caused the process to stop.

</details>

<details>
<summary><b><i>134.What happens when you press ctrl + c?</i></b></summary>

$\color{green}{\text{Answer}}$

When you press "Ctrl+C," it sends the SIGINT signal to the foreground process, asking it to terminate gracefully.

</details>

<details>
<summary><b><i>135.What is a Daemon in Linux?</i></b></summary>

$\color{green}{\text{Answer}}$

A background process. Most of these processes are waiting for requests or set of conditions to be met before actually running anything. Some examples: sshd, crond, rpcbind.

</details>

<details>
<summary><b><i>136.What are the possible states of a process in Linux?</i></b></summary>

$\color{green}{\text{Answer}}$

- `Running (R)`
- `Uninterruptible Sleep (D)` - The process is waiting for I/O
- `Interruptible Sleep (S)`
- `Stopped (T)`
- `Dead (x)`
- `Zombie (z)`

</details>

<details>
<summary><b><i>137.How do you kill a process in D state?</i></b></summary>

$\color{green}{\text{Answer}}$

A process in D state (also known as "uninterruptible sleep") cannot be killed using the "kill" command. The only way to terminate it is to reboot the system.

</details>

<details>
<summary><b><i>138.What is a zombie process?</i></b></summary>

$\color{green}{\text{Answer}}$

- A process which has finished to run but has not exited.

- One reason it happens is when a parent process is programmed incorrectly. Every parent process should execute wait() to get the exit code from the child process which finished to run. But when the parent isn't checking for the child exit code, the child process can still exists although it finished to run.

</details>

<details>
<summary><b><i>139.How to get rid of zombie processes?</i></b></summary>

$\color{green}{\text{Answer}}$

- You can't kill a zombie process the regular way with kill -9 for example as it's already dead.
- One way to kill zombie process is by sending SIGCHLD to the parent process telling it to terminate its child processes. This might not work if the parent process wasn't programmed properly. The invocation is kill -s SIGCHLD [parent_pid]
- You can also try closing/terminating the parent process. This will make the zombie process a child of init (1) which does periodic cleanups and will at some point clean up the zombie process.

</details>

<details>
<summary><b><i>140.How to find all the</i></b></summary>

$\color{green}{\text{Answer}}$

- Processes executed/owned by a certain user -> `ps -u [username]`
- Process which are Java processes -> `ps -ef | grep java`
- Zombie Processes -> `ps -eAo stat,pid,comm | grep -w Z`

</details>

<details>
<summary><b><i>141.What is the init process?</i></b></summary>

$\color{green}{\text{Answer}}$

It is the first process executed by the kernel during the booting of a system. It is a daemon process which runs till the system is shutdown. That is why, it is the parent of all the processes

</details>

<details>
<summary><b><i>142.Can you describe how processes are being created?</i></b></summary>

$\color{green}{\text{Answer}}$

The process creation mechanism is fundamentally based on a two-step procedure involving the fork() and exec() system calls, known as the fork-exec model.

</details>

<details>
<summary><b><i>143.How to change the priority of a process? Why would you want to do that?</i></b></summary>

$\color{green}{\text{Answer}}$

- To change the priority of a process, you can use the nice command in Linux. The nice command allows you to specify the priority of a process by assigning a priority value ranging from -20 to 19. A higher value of priority means lower priority for the process, and vice versa.
- You may want to change the priority of a process to adjust the amount of CPU time it is allocated by the system scheduler. For example, if you have a CPU-intensive process running on your system that is slowing down other processes, you can lower its priority to give more CPU time to other processes.

</details>

<details>
<summary><b><i>144.Can you explain how network process/connection is established and how it's terminated?</i></b></summary>

$\color{green}{\text{Answer}}$

When a client process on one system wants to establish a connection with a server process on another system, it first creates a socket using the socket system call. The client then calls the connect system call, passing the address of the server as an argument. This causes a three-way handshake to occur between the client and server, where the two systems exchange information to establish a connection.
Once the connection is established, the client and server can exchange data using the read and write system calls. When the connection is no longer needed, the client or server can terminate the connection by calling the close system call on the socket.

</details>

<details>
<summary><b><i>145.What `strace` does? What about `ltrace`?</i></b></summary>

$\color{green}{\text{Answer}}$

- `Strace` is a debugging tool that is used to monitor the system calls made by a process. It allows you to trace the execution of a process and see the system calls it makes, as well as the signals it receives. This can be useful for diagnosing issues with a process, such as identifying why it is hanging or crashing.
- `Ltrace`, on the other hand, is a similar tool that is used to trace the library calls made by a process. It allows you to see the function calls made by a process to shared libraries, as well as the arguments passed to those functions. This can be useful for diagnosing issues with a process that involve library calls, such as identifying why a particular library is causing a problem.

</details>

<details>
<summary><b><i>146.Find all the files which end with '.yml' and replace the number 1 in 2 in each file</i></b></summary>

$\color{green}{\text{Answer}}$

`find /some_dir -iname *.yml -print0 | xargs -0 -r sed -i "s/1/2/g"`

</details>

<details>
<summary><b><i>147.You run ls and you get "/lib/ld-linux-armhf.so.3 no such file or directory". What is the problem?</i></b></summary>

$\color{green}{\text{Answer}}$

The ls executable is built for an incompatible architecture.

</details>

<details>
<summary><b><i>148.How would you split a 50 lines file into 2 files of 25 lines each?</i></b></summary>

$\color{green}{\text{Answer}}$

You can use the `split` command this way: `split -l 25 some_file`

</details>

<details>
<summary><b><i>149.What is a kerberos file descriptor? What file descriptors are you familiar with?</i></b></summary>

$\color{green}{\text{Answer}}$

- Kerberos File descriptor, also known as file handler, is a unique number which identifies an open file in the operating system.
In Linux (and Unix) the first three file descriptors are:
  - 0 - the default data stream for input
  - 1 - the default data stream for output
  - 2 - the default data stream for output related to errors

</details>

<details>
<summary><b><i>150.What is NTP? What is it used for?</i></b></summary>

$\color{green}{\text{Answer}}$

NTP stands for Network Time Protocol. It is a networking protocol used for clock synchronization between computer systems over packet-switched, variable-latency data networks, like the internet. In simpler terms, it's a way for your Linux machine (or any networked device) to get the correct time from a highly accurate source.

</details>

<details>
<summary><b><i>151.Explain Kernel OOM.</i></b></summary>

$\color{green}{\text{Answer}}$

The Kernel OOM (Out-of-Memory) Killer is a crucial, last-resort mechanism in the Linux kernel designed to maintain system stability when the available physical RAM and swap space have been exhausted. Due to Linux's default policy of memory overcommit (where the kernel allows processes to request more memory than is physically available), it's possible for the system to run into a critical situation where a legitimate memory request cannot be fulfilled.

</details>

## Security

<details>
<summary><b><i>152.What is chroot? In what scenarios would you consider using it?</i></b></summary>

- Chroot, short for "change root," is a command and system call in Linux that changes the apparent root directory (/) for the currently running process and all its children. This action creates a restricted environment, often called a chroot jail, where the processes running inside cannot access or name files outside of the newly defined directory structure. Essentially, the processes are isolated and tricked into believing that the new directory is the topmost level of the file system. While this provides a form of basic sandboxing, it does not provide full security isolation on its own, as a process with root privileges can potentially escape the jail.

- The chroot utility is primarily used in scenarios requiring isolation, system recovery, or clean building environments. Common uses include system maintenance and repair, such as when a Linux system fails to boot: an administrator can boot from a live USB, mount the damaged system's partitions, and then use chroot to step into that broken environment to safely reinstall a bootloader or reset a forgotten password. It is also used for security sandboxing by restricting network services (like FTP or DNS daemons) to a limited part of the file system to contain the damage if the service is compromised. Furthermore, developers use it to build software packages in a clean environment that only contains the necessary dependencies, preventing unintended conflicts with the host system.

</details>

<details>
<summary><b><i>153.What is SELiunx?</i></b></summary>

$\color{green}{\text{Answer}}$

SELinux (Security-Enhanced Linux) is a Linux kernel security module that provides a mechanism for supporting Mandatory Access Control (MAC) security policies. It was originally developed by the U.S. National Security Agency (NSA) and integrated into the Linux kernel using the Linux Security Modules (LSM) framework. Its primary purpose is to add a crucial, fine-grained layer of security that operates in addition to the traditional Linux Discretionary Access Control (DAC), which is the standard owner/group/world read/write/execute permissions.

</details>

<details>
<summary><b><i>154.What is Kerberos?</i></b></summary>

$\color{green}{\text{Answer}}$

Kerberos is a network authentication protocol that uses symmetric-key cryptography to provide strong mutual authentication for client-server applications over non-secure networks. It was developed at MIT and is designed to eliminate the transmission of unencrypted passwords across the network. Instead of passwords, Kerberos uses temporary, encrypted credentials called tickets to prove the identity of both the user and the service. This is the foundation for providing a Single Sign-On (SSO) experience in a Linux or Unix network environment, allowing users to log in once and access multiple services without re-entering credentials.

</details>

<details>
<summary><b><i>155.What is nftables?</i></b></summary>

$\color{green}{\text{Answer}}$

nftables is the modern, flexible packet filtering framework that replaced the aging iptables in the Linux kernel. It is integrated with the Netfilter project and provides a more efficient, unified, and scalable approach to managing firewall rules.

</details>

<details>
<summary><b><i>156.What firewalld daemon is responsible for?</i></b></summary>

$\color{green}{\text{Answer}}$

The firewalld daemon is the dynamic firewall management service that acts as the primary network defense mechanism on many modern Linux distributions (like Fedora, CentOS/RHEL, and recent Debian/Ubuntu versions). Its main responsibility is to provide a user-friendly, dynamic, and rule-set-independent interface for configuring the underlying kernel packet filtering facilities (Netfilter, which may use iptables or nftables as the backend).

</details>

<details>
<summary><b><i>157.Do you have experience with hardening servers? Can you describe the process?</i></b></summary>

$\color{green}{\text{Answer}}$

Yes, I have extensive knowledge of server hardening best practices in a Linux environment. Hardening is a systematic process of increasing a server's security posture by reducing its attack surface, eliminating unnecessary functionality, and strengthening configurations.

The process is generally divided into several key phases
  - 1.`Baseline & Preparation` -> Establish a secure starting point, document the current configuration, and ensure all systems are up-to-date.
  - 2.`Reduce Attack Surface` - > Remove unnecessary software and services to minimize potential entry points for attackers.
  - 3.`Account & Authentication` -> Implement strong controls over user access and authentication mechanisms.
  - 4.`Kernel & System Security` -> Configure kernel parameters and security modules to defend against exploits.
  - 5.`Network & Firewall` -> Implement robust filtering and monitoring of all network traffic.
  - 6.`Logging & Auditing` -> Ensure all significant security events are logged, and implement regular reviews.

</details>

<details>
<summary><b><i>158.How do you create a private key for a CA (certificate authority)?</i></b></summary>

$\color{green}{\text{Answer}}$

One way is using openssl this way:
`openssl genrsa -aes256 -out ca-private-key.pem 4096`

</details>
 
<details>
<summary><b><i>159.How do you create a public key for a CA (certificate authority)?</i></b></summary>

$\color{green}{\text{Answer}}$

`openssl req -new -x509 -days 730 -key [private key file name] -sha256 -out ca.pem`

If using the private key from the previous question then the command would be:
  - `openssl req -new -x509 -days 730 -key ca-private-key.pem -sha256 -out ca.pem`

</details>

<details>
<summary><b><i>160.Demonstrate one way to encode and decode data in Linux</i></b></summary>

$\color{green}{\text{Answer}}$

- Encode: `echo -n "some password" | base64`
- Decode: `echo -n "allE19remO91" | base64`

</details>

## Networking

<details>
<summary><b><i>161.How to list all the interfaces?</i></b></summary>

$\color{green}{\text{Answer}}$

`ip link show`

</details>

<details>
<summary><b><i>162.What is the loopback (lo) interface?</i></b></summary>

$\color{green}{\text{Answer}}$

The loopback interface is a special, virtual network interface that your computer uses to communicate with itself. It is used mainly for diagnostics and troubleshooting, and to connect to servers running on the local machine.

</details>

<details>
<summary><b><i>163.What the following commands are used for?</i></b></summary>

$\color{green}{\text{Answer}}$

1.ip addr -> Used to display and manipulate IP addresses and their associated properties on network interfaces. It shows the current state of all interfaces (e.g., eth0, lo), their assigned IPv4 and IPv6 addresses, network masks, and hardware (MAC) addresses
    
2.ip route -> Used to display and manipulate the IP routing table. It shows how packets are directed out of the system, including the default gateway (default via), destination networks, and which network interface (dev) to use.
    
3.ip link -> Used to display and manipulate the state of network interfaces (Layer 2 configuration). It shows interface status (e.g., UP/DOWN), hardware (MAC) addresses, Multi-Transport Unit (MTU), and other physical/link layer properties. It is used to bring interfaces up or down.
    
4.ping -> Used to test basic network connectivity to a target host (IP address or hostname). It sends ICMP Echo Request packets and measures the time it takes to receive the Echo Reply, providing the Round Trip Time (RTT) and reporting packet loss. This confirms if the host is "alive" and reachable.
    
5.netstat -> (Short for Network Statistics) Used to display active network connections, routing tables, interface statistics, and open listening ports. It's useful for security auditing and troubleshooting to see what services are running, on which ports they are listening, and what connections are currently established. Note: On modern Linux systems, netstat is being superseded by the more performant ss command.
    
6.traceroute -> Used to trace the path that network packets take from the source host to a destination host. It works by sending packets with gradually increasing Time To Live (TTL) values and records the IP address and latency of each intermediate router, or hop, on the path. This is vital for identifying network bottlenecks or points of failure.

</details>

<details>
<summary><b><i>164.What is a network namespace? What is it used for?</i></b></summary>

$\color{green}{\text{Answer}}$

- A network namespace is a feature of the Linux kernel that provides a virtually isolated copy of the network stack for a set of processes. This isolation includes its own network interfaces, IP address tables, routing tables, socket lists, connection tracking tables, and firewall rules. Every new Linux system starts with at least one default network namespace, known as the initial or root namespace. Any process inside a network namespace sees only the network configuration and interfaces associated with that specific namespace, making it appear as if it is running on an entirely separate host.

- Network namespaces are a foundational technology for containerization (e.g., Docker, Kubernetes) and other virtualization solutions, as they allow multiple containers on a single host to run applications using the same port numbers (like port 80 or 443) without conflict, each binding to the interfaces within its own isolated environment. They are also used for network testing and development, enabling developers and administrators to create complex virtual network topologies, test routing protocols, and simulate different network conditions on a single machine without needing physical hardware or fully virtualized systems.

</details>

<details>
<summary><b><i>165.How to check if a certain port is being used?</i></b></summary>

$\color{green}{\text{Answer}}$

One of the following would work:
  - `netstat -tnlp | grep <port_number>`
  - `lsof -i -n -P | grep <port_number>`

</details>

<details>
<summary><b><i>166.How can you turn your Linux server into a router?</i></b></summary>

$\color{green}{\text{Answer}}$

To turn a Linux server into a router, you must configure the kernel to enable IP forwarding (or IP masquerading) so that the server can route packets between different network interfaces. This is primarily done by setting the kernel parameter `net.ipv4.ip_forward` to `1` in the `/etc/sysctl.conf` file. Additionally, you need to configure Network Address Translation (NAT) rules using the firewall (e.g., `nftables` or `iptables`) to allow devices on the private network to share the server's single external IP address when communicating with the internet.

</details>

<details>
<summary><b><i>167.What is a virtual IP? In what situation would you use it?</i></b></summary>

$\color{green}{\text{Answer}}$

- A Virtual IP (VIP) is an IP address that is not permanently assigned to a single physical network interface but is instead shared and managed by a group of hosts. It acts as a logical identifier for a service or a cluster of servers, creating a single point of access for clients. Clients connect to the VIP, and the underlying network infrastructure or cluster software determines which physical server actually receives and handles the traffic destined for that address.

- VIPs are essential in high availability (HA) and load balancing scenarios. In HA, a VIP is used to achieve failover; for instance, a master server holds the VIP, and if it fails, a heartbeat or cluster manager instantly moves (or floats) the VIP to a redundant backup server, ensuring the service remains continuously accessible to users without a change in the connection address. In load balancing, the VIP is assigned to a front-end load balancer, which then distributes incoming client connections across multiple back-end application or web servers to efficiently spread the workload and handle higher traffic volumes.

</details>

<details>
<summary><b><i>168.True or False? The MAC address of an interface is assigned/set by the OS</i></b></summary>

$\color{green}{\text{Answer}}$

False

</details>

<details>
<summary><b><i>169.Can you have more than one default gateway in a given system?</i></b></summary>

$\color{green}{\text{Answer}}$

Technically, yes.

</details>

<details>
<summary><b><i>170.What is telnet and why is it a bad idea to use it in production? (or at all)</i></b></summary>

$\color{green}{\text{Answer}}$

Telnet is a type of client-server protocol that can be used to open a command line on a remote computer, typically a server. By default, all the data sent and received via telnet is transmitted in clear/plain text, therefore it should not be used as it does not encrypt any data between the client and the server.

</details>

<details>
<summary><b><i>171.What is the routing table? How do you view it?</i></b></summary>

$\color{green}{\text{Answer}}$

- The routing table is a kernel data structure used by Linux to determine the next hop (destination) for an outgoing packet. It matches a packet's destination IP against its entries to decide which gateway and local network interface to use, including a default route for all unknown destinations.

- You can view the routing table using the command `ip route` (or the more verbose `ip route show`), which displays the destination network, the gateway IP, and the device (interface) associated with each entry.

</details>

<details>
<summary><b><i>172.How can you send an HTTP request from your shell?</i></b></summary>

$\color{green}{\text{Answer}}$

Using nc is one way

</details>

<details>
<summary><b><i>173.What are packet sniffers? Have you used one in the past? If yes, which packet sniffers have you used and for what purpose?</i></b></summary>

$\color{green}{\text{Answer}}$

It is a network utility that analyses and may inject tasks into the data-stream travelling over the targeted network.

</details>

<details>
<summary><b><i>174.How to list active connections?</i></b></summary>

$\color{green}{\text{Answer}}$

`ss -tn`

</details>

<details>
<summary><b><i>175.How to trigger neighbor discovery in IPv6?</i></b></summary>

$\color{green}{\text{Answer}}$

One way would be `ping6 ff02::1`

</details>

<details>
<summary><b><i>176.What is network interface bonding and do you know how it's performed in Linux?</i></b></summary>  

$\color{green}{\text{Answer}}$

Network interface bonding (also known as NIC Teaming or link aggregation) is a Linux technique used to combine multiple physical network interfaces (like eth0 and eth1) into a single logical link, called a bond interface (e.g., bond0).

How it's Performed in Linux
  - Bonding is implemented using the bonding kernel module and is configured via user-space tools. The high-level steps are:
    - 1.Load the Module: Ensure the bonding kernel module is loaded (modprobe bonding).
    - 2.Configuration Files: Create a configuration file for the new bond interface (bond0) that defines the IP address, netmask, and the bonding mode (e.g., Active-Backup, Round Robin).
    - 3.Configure Slaves: Configure the physical interfaces (the "slave" interfaces) to be part of the bond interface and ensure they do not have their own IP addresses.
    - 4.Networking Service Restart: Restart the networking service to bring up the bond0 interface.

</details>

<details>
<summary><b><i>177.What network bonding modes are there?</i></b></summary>

$\color{green}{\text{Answer}}$

There a couple of modes:
  - balance-rr: round robing bonding
  - active-backup: a fault tolerance mode where only one is active
  - balance-tlb: Adaptive transmit load balancing
  - balance-alb: Adaptive load balancing

</details>

<details>
<summary><b><i>178.What is a bridge? How it's added in Linux OS?</i></b></summary>

$\color{green}{\text{Answer}}$

A network bridge is a software device that functions like a Layer 2 network switch on a Linux server, forwarding traffic between multiple network segments (physical interfaces, virtual interfaces, or other bridges) based on MAC addresses.

It is added in Linux by using the brctl utility (from the bridge-utils package, for legacy setups) or the modern ip link command:
  - 1.Create the bridge: `ip link add name br0 type bridge`
  - 2.Add interfaces (ports): `ip link set eth0 master br0`
  - 3.Bring up the bridge: `ip link set br0 up`

</details>

## DNS

<details>
<summary><b><i>179.How to check what is the hostname of the system?</i></b></summary>

$\color{green}{\text{Answer}}$

`cat /etc/hostname`

- You can also run `hostnamectl` or `hostname` but that might print only a temporary hostname. The one in the file is the permanent one.

</details>

<details>
<summary><b><i>180.What the file /etc/resolv.conf is used for? What does it include?</i></b></summary>

$\color{green}{\text{Answer}}$

- The file /etc/resolv.conf configures the Linux system's DNS resolver for hostname-to-IP-address translation.
- It primarily includes the nameserver directives, which list the IP addresses of the DNS servers to query, and the search directive, which specifies domain names to append to hostnames for unqualified lookups.

</details>

<details>
<summary><b><i>181.What commands are you using for performing DNS queries (or troubleshoot DNS related issues)?</i></b></summary>

$\color{green}{\text{Answer}}$

You can specify one or more of the following:
  - dig
  - host
  - nslookup

 </details>
 
<details>
<summary><b><i>182.You run dig codingshell.com and get the following result:

```Linux
codingshell.com.	3515	IN	A	185.199.109.153
```

What is the meaning of the number 3515?

</i></b></summary>

$\color{green}{\text{Answer}}$

- This is the TTL. When you lookup for an address using a domain/host name, your OS is performing DNS resolution by contacting DNS name servers to get the IP address of the host/domain you are looking for.
- When you get a reply, this reply in cached in your OS for a certain period of time. This is period of time is also known as TTL and this is the meaning of 3515 number, it will be cached for 3515 seconds before removed from the cache and during that period of time, you'll get the value from the cache instead of asking DNS name servers for the address again.

</details>

<details>
<summary><b><i>183.How can we modify the network connection via `nmcli` command, to use `8.8.8.8` as a DNS server?</i></b></summary>

$\color{green}{\text{Answer}}$

1.Find the connection name:
  ```Linux
  # nmcli con show
  NAME         UUID                                  TYPE      DEVICE
  System ens5  8126c120-a964-e959-ff98-ac4973344505  ethernet  ens5
  System eth0  5fb06bd0-0bb0-7ffb-45f1-d6edd65f3e03  ethernet  --
  ```

Here the connection name is "System ens5". Let's say we want to modify settings for this connection.

2.Modify the connection to use 8.8.8.8 as DNS server:
  ```Linux
  # nmcli con mod "System ens5" ipv4.dns "8.8.8.8"
  ```

3.We need to reactivate the connection for the change to take effect:
  ```Linux
  nmcli con up "System ens5"
  ```

4.Verify our settings once more:
  ```Linux
  cat /etc/resolv.conf
  nmcli -f ipv4.dns con show "System ens5"
  ```

</details>

## Packaging

<details>
<summary><b><i>184.Do you have experience with packaging? (as in building packages) Can you explain how does it works?</i></b></summary>

$\color{green}{\text{Answer}}$

Yes, I have extensive knowledge of the packaging process in Linux. Building packages is the method of compiling an application's source code and bundling the resulting binaries, configuration files, documentation, and dependencies into a single, standardized archive file (like a .deb or .rpm) that can be easily installed, upgraded, and removed across many systems.

</details>

<details>
<summary><b><i>185.How packages installation/removal is performed on the distribution you are using?</i></b></summary>

$\color{green}{\text{Answer}}$

In Fedora/CentOS/RHEL/Rocky it can be done with `rpm` or `dnf` commands. In Ubuntu it can be done with the `apt` command.

</details>

<details>
<summary><b><i>186.RPM: explain the spec format (what it should and can include)</i></b></summary>

$\color{green}{\text{Answer}}$

The RPM Spec File is the blueprint for creating RPM packages, containing metadata (Name, Version, Release, License, Summary, Dependencies), build instructions (%prep, %build, %install), a list of all files to include in the package (%files), and optional scriptlets (%pre, %post, %preun, %postun) that execute during the installation or removal process.

</details>

<details>
<summary><b><i>187.How do you list the content of a package without actually installing it?</i></b></summary>

$\color{green}{\text{Answer}}$

To list the contents (the files and their installation paths) of a Linux package without actually installing it, you use the query capabilities of the package manager specific to your distribution: `rpm` for RPM-based systems or `dpkg` for Debian-based systems.

</details>

<details>
<summary><b><i>188.How to know to which package a file on the system belongs to? Is it a problem if it doesn't belongs to any package?</i></b></summary>

$\color{green}{\text{Answer}}$

- To find the owning package for a file, you use the package manager's query function: `rpm -qf /path/to/file` (for RHEL/Fedora) or `dpkg -S /path/to/file` (for Debian/Ubuntu).

- It is NOT necessarily a problem if a file doesn't belong to any package; this is normal for user-created data, logs, or manually compiled third-party software. However, it is a major security concern if critical system files (e.g., in `/usr/bin` or `/etc`) are unowned, as this can indicate a manual installation of malicious code or system tampering.

</details>

<details>
<summary><b><i>189.Where repositories are stored? (based on the distribution you are using)</i></b></summary>

$\color{green}{\text{Answer}}$

Linux distribution repositories are typically configured via files located in the /etc/apt/ or /etc/yum.repos.d/ directories.
  - Debian/Ubuntu (using APT): Repository lists are primarily defined in the `/etc/apt/sources.list` file and often in individual `.list` files within the `/etc/apt/sources.list.d/` directory.
  - RHEL/CentOS/Fedora (using DNF/YUM): Repository configurations are stored in individual `.repo` files within the `/etc/yum.repos.d/` directory (e.g., `epel.repo`).

</details>

<details>
<summary><b><i>190.What is an archive? How do you create one in Linux?</i></b></summary>

$\color{green}{\text{Answer}}$

An archive is a single file that bundles multiple other files and directories together, primarily for the purpose of data consolidation and easy portability. Archives are typically created using utilities like `tar` and often use compression algorithms (like gzip or bzip2) to reduce their size, though the archiving and compression steps are technically separate processes.

The basic command to create a compressed archive is:
  - `tar -czvf archive_name.tar.gz /path/to/files/`

</details>

<details>
<summary><b><i>191.How to extract the content of an archive?</i></b></summary>

$\color{green}{\text{Answer}}$

`tar -xzvf archive_name.tar.gz`

</details>

<details>
<summary><b><i>192.Why do we need package managers? Why not simply creating archives and publish them?</i></b></summary>

$\color{green}{\text{Answer}}$

Package managers allow you to manage packages lifecycle as in installing, removing and updating the packages.In addition, you can specify in a spec how a certain package will be installed - where to copy the files, which commands to run prior to the installation, post the installation, etc.

</details>

## DNF

<details>
<summary><b><i>193.What is DNF?</i></b></summary>

$\color{green}{\text{Answer}}$

"Dandified YUM (DNF) is the next upcoming major version of YUM. It does package management using RPM, libsolv and hawkey libraries."

</details>

<details>
<summary><b><i>194.How to look for a package that provides the command /usr/bin/git? (the package isn't necessarily installed)</i></b></summary>

$\color{green}{\text{Answer}}$

dnf provides /usr/bin/git

</details>

## Applications & Services

<details>
<summary><b><i>195.What can you find in /etc/services?</i></b></summary>

$\color{green}{\text{Answer}}$

The file `/etc/services` is a plain text configuration file in Linux that acts as a local database mapping well-known service names to their corresponding port numbers and transport protocols (TCP or UDP).

</details>

<details>
<summary><b><i>196.How to make sure a Service starts automatically after a reboot or crash?</i></b></summary>

$\color{green}{\text{Answer}}$

- Depends on the init system.

- Systemd:  `systemctl enable [service_name]`  System V:  `update-rc.d [service_name]`  and add this line  `id:5678:respawn:/bin/sh /path/to/app`  to `/etc/inittab` Upstart: add Upstart init script at /etc/init/service.conf

</details>

<details>
<summary><b><i>197.You run ssh 127.0.0.1 but it fails with "connection refused". What could be the problem?</i></b></summary>

$\color{green}{\text{Answer}}$

- 1.SSH server is not installed
- 2.SSH server is not running

</details>

<details>
<summary><b><i>198.How to print the shared libraries required by a certain program? What is it useful for?</i></b></summary>

$\color{green}{\text{Answer}}$

- To print the shared libraries required by a certain program in Linux, you use the ldd command (List Dynamic Dependencies).

- The `ldd` command is useful for troubleshooting program startup failures caused by missing dependencies and for verifying that the correct library versions are being linked. It is essential when building minimal container images or creating isolated chroot environments, as it defines the exact set of external files required for the application to run.

</details>

<details>
<summary><b><i>199.What is CUPS?</i></b></summary>

$\color{green}{\text{Answer}}$

CUPS stands for Common Unix Printing System. It is a modular printing system that allows a computer running Linux to act as a print server. It is the standard printing service used by nearly all modern Linux distributions.

</details>

<details>
<summary><b><i>200.What types of web servers are you familiar with?</i></b></summary>

$\color{green}{\text{Answer}}$

Nginx, Apache httpd.

</details>

## Users and Group

<details>
<summary><b><i>201.What is a "superuser" (or root user)? How is it different from regular users?</i></b></summary>

$\color{green}{\text{Answer}}$

A superuser, or root user, is the administrative account in Linux, possessing unrestricted system privileges.

It is fundamentally different from a regular user in the following ways:
  - Permissions: The superuser (UID 0) can bypass standard file and directory permissions (DAC), allowing it to read, write, or execute any file and perform any system-wide changes (installing software, configuring networks, managing all users).
  - Regular users have restricted permissions, primarily limited to their own home directory and files, and must use tools like sudo to temporarily gain root privileges for administrative tasks.

</details>

<details>
<summary><b><i>202.How do you create users? Where user information is stored?</i></b></summary>

$\color{green}{\text{Answer}}$

Command to create users is `useradd`
  - Syntax: `useradd [options] Username`

There are 2 configuration files, which stores users information
  - 1.`/etc/passwd` - Users information like, username, shell etc is stored in this file
  - 2.`/etc/shadow` - Users password is stored in encrypted format

</details>

<details>
<summary><b><i>203.Which file stores information about groups?</i></b></summary>

$\color{green}{\text{Answer}}$

`/etc/groups` file stores the group name, group ID, usernames which are in secondary group.

</details>

<details>
<summary><b><i>204.How do you change/set the password of a user?</i></b></summary>

$\color{green}{\text{Answer}}$

`passwd <username>` is the command to set/change password of a user.

</details>

<details>
<summary><b><i>205.Which file stores users passwords? Is it visible for everyone?</i></b></summary>

$\color{green}{\text{Answer}}$

`/etc/shadow` file holds the passwords of the users in encrypted format. NO, it is only visible to the root user

</details>

<details>
<summary><b><i>206.Do you know how to create a new user without using adduser/useradd command?</i></b></summary>

$\color{green}{\text{Answer}}$

YES, we can create new user by manually adding an entry in the `/etc/passwd` file.

For example, if we need to create a user called john.

1. Add an entry to `/etc/passwd` file, so user gets created.
  - `echo "john:x:2001:2001::/home/john:/bin/bash" >> /etc/passwd`
2. Add an entry to `/etc/group` file, because every user belong to the primary group that has same name as the username.
  - `echo "john:x:2001:" >> /etc/group`
3. Verify if the user got created
  - `id john`

</details>

<details>
<summary><b><i>207.What information is stored in /etc/passwd? explain each field</i></b></summary>

$\color{green}{\text{Answer}}$

`/etc/passwd` is a configuration file, which contains users information. Each entry in this file has, 7 fields,

`username:password:UID:GID:Comment:home directory:shell`

`username` - The name of the user.

`password` - This field is actually a placeholder of the password field. Due to security concerns, this field does not contain the password, just a placeholder (x) to the encrypted password stored in /etc/shadow file.

`UID` - User ID of the user.

`GID` - Group ID

`Comment` - This field is to provide description about the user.

`home directory` - Abousulte path of the user's home directory. This directory gets created once the user is added.
  
`shell` - This field contains the absolute path of the shell that will be used by the respective user.

</details>

<details>
<summary><b><i>208.How to add a new user to the system without providing him the ability to log-in into the system?</i></b></summary>

$\color{green}{\text{Answer}}$

`adduser user_name --shell=/bin/false --no-create-home` You can also add a user and then edit /etc/passwd.

</details>

<details>
<summary><b><i>208.How to switch to another user? How to switch to the root user?</i></b></summary>

$\color{green}{\text{Answer}}$

`su` command. Use `su -` to switch to root

</details>

<details>
<summary><b><i>209.What is the UID the root user? What about a regular user?</i></b></summary>

$\color{green}{\text{Answer}}$

- UID of root user is 0
- Default values of UID_MIN and UID_MAX in `/etc/login.defs` `UID_MIN` is `1000` `UID_MAX` is `60000`

- Actually, we can change this value. But UID < 1000 are reserved for system accounts. Therefore, as per the default configuration, for regular user UID starts from `1000`.

</details>

<details>
<summary><b><i>210.What can you do if you lost/forogt the root password?</i></b></summary>

$\color{green}{\text{Answer}}$

Re-install the OS IS NOT the right answer

</details>

<details>
<summary><b><i>211.What is /etc/skel?</i></b></summary>

$\color{green}{\text{Answer}}$

`/etc/skel` is a directory, that contains files or directories, so when a new user is created, these files/directories created under `/etc/skel` will be copied to user's home directory.

</details>

<details>
<summary><b><i>212.How to see a list of who logged-in to the system?</i></b></summary>

$\color{green}{\text{Answer}}$

Using the `last` command.

</details>

<details>
<summary><b><i>213.Explain what each of the following commands does:</i></b></summary>

$\color{green}{\text{Answer}}$
  
1. useradd -> Command for creating new users
2. usermod -> Modify the users setting
3. whoami -> Outputs, the username that we are currently logged in 
4. id -> Prints the User ID (UID), Group ID (GID)

</details>

<details>
<summary><b><i>214.You run grep $(whoami) /etc/passwd but the output is empty. What might be a possible reason for that?</i></b></summary>

$\color{green}{\text{Answer}}$

- The user you are using isn't defined locally but originates from services like LDAP.
- You can verify with: `getent passwd`

</details>

## Hardware

<details>
<summary><b><i>215.Where can you find information on the processor (like number of CPUs)?</i></b></summary>

$\color{green}{\text{Answer}}$

`/proc/cpuinfo`

</details>

<details>
<summary><b><i>216.How can you print information on the BIOS, motherboard, processor and RAM?</i></b></summary>

$\color{green}{\text{Answer}}$

`dmidecoode`

</details>

<details>
<summary><b><i>217.How can you print all the information on connected block devices in your system?</i></b></summary>

$\color{green}{\text{Answer}}$

`lsblk`

</details>

<details>
<summary><b><i>218.True or False? In user space, applications don't have full access to hardware resources</i></b></summary>

$\color{green}{\text{Answer}}$

True. Only in kernel space they have full access to hardware resources.

</details>

## Namespaces

<details>
<summary><b><i>219.What types of namespaces are there in Linux?</i></b></summary>

$\color{green}{\text{Answer}}$

`Process ID namespaces`: these namespaces include independent set of process IDs

`Mount namespaces`: Isolation and control of mountpoints

`Network namespaces`: Isolates system networking resources such as routing table, interfaces, ARP table, etc.

`UTS namespaces`: Isolate host and domains

`IPC namespaces`: Isolates interprocess communications

`User namespaces`: Isolate user and group IDs

`Time namespaces`: Isolates time machine

</details>

<details>
<summary><b><i>220.True or False? In every PID (Process ID) namespace the first process assigned with the process id number 1</i></b></summary>

$\color{green}{\text{Answer}}$

True. Inside the namespace it's PID 1 while to the parent namespace the PID is a different one.

</details>

<details>
<summary><b><i>221.True or False? In a child PID namespace all processes are aware of parent PID namespace and processes and the parent PID namespace has no visibility of child PID namespace processes</i></b></summary>

$\color{green}{\text{Answer}}$

False. The opposite is true. Parent PID namespace is aware and has visibility of processes in child PID namespace and child PID namespace has no visibility as to what is going on in the parent PID namespace.

</details>

<details>
<summary><b><i>222.rue or False? By default, when creating two separate network namespaces, a ping from one namespace to another will work fine</i></b></summary>

$\color{green}{\text{Answer}}$

False. Network namespace has its own interfaces and routing table. There is no way (without creating a bridge for example) for one network namespace to reach another.

</details>

<details>
<summary><b><i>223.True or False? With UTS namespaces, processes may appear as if they run on different hosts and domains while running on the same host</i></b></summary>

$\color{green}{\text{Answer}}$

True

</details>

<details>
<summary><b><i>224.True or False? It's not possible to have a root user with ID 0 in child user namespaces</i></b></summary>

$\color{green}{\text{Answer}}$

False. In every child user namespace, it's possible to have a separate root user with uid of 0.

</details>

<details>
<summary><b><i>225.What time namespaces are used for?</i></b></summary>

$\color{green}{\text{Answer}}$

In time namespaces processes can use different system time.

</details>

## Virtualization

<details>
<summary><b><i>226.What virtualization solutions are available for Linux?</i></b></summary>

$\color{green}{\text{Answer}}$

- KVM
- XEN
- VirtualBox
- Linux-VServer
- User-mode Linux

</details>

<details>
<summary><b><i>227.What is KVM?</i></b></summary>

$\color{green}{\text{Answer}}$

Is an open source virtualization technology used to operate on x86 hardware.

</details>

<details>
<summary><b><i>228.What is Libvirt?</i></b></summary>

$\color{green}{\text{Answer}}$

It's an open source collection of software used to manage virtual machines. It can be used with: KVM, Xen, LXC and others. It's also called Libvirt Virtualization API.

</details>

## AWK

<details>
<summary><b><i>229.What the awk command does? Have you used it? What for?</i></b></summary>

$\color{green}{\text{Answer}}$

AWK is domain-specific language designed for text processing and typically used as a data extraction and reporting tool

</details>

<details>
<summary><b><i>230.How to print the 4th column in a file?</i></b></summary>

$\color{green}{\text{Answer}}$

`awk '{print $4}'` file

</details>

<details>
<summary><b><i>231.How to print every line that is longer than 79 characters?</i></b></summary>

$\color{green}{\text{Answer}}$

`awk 'length($0) > 79'` file

</details>

<details>
<summary><b><i>232.What the lsof command does? Have you used it? What for?</i></b></summary>

$\color{green}{\text{Answer}}$

The lsof command in Unix-like operating systems stands for "LiSt Open Files." Its primary function is to report a comprehensive list of all files that are currently open by active processes on the system.

I have used `lsof` for powerful troubleshooting and system monitoring

Used it for:
  - Finding which process is using a file
  - Identifying network connections and ports
  - Listing files opened by a specific user or command
  - Finding deleting files still held open

</details>

<details>
<summary><b><i>233.What is the difference between find and locate?</i></b></summary>

$\color{green}{\text{Answer}}$

Use locate when you need a fast, system-wide search for a file by name and you don't need real-time accuracy (e.g., finding a configuration file you know exists).
  - Example: `locate httpd.conf`

Use find when you need real-time accuracy or when you need to search based on complex criteria other than just the name.
  - Example : `find /var/log -size +10M -mtime -7`

</details>

<details>
<summary><b><i>234.How a user process performs a privileged operation, such as reading from the disk?</i></b></summary>

$\color{green}{\text{Answer}}$

Using system calls

</details>

## System Call

<details>
<summary><b><i>235.What is a system call? What system calls are you familiar with?</i></b></summary>

$\color{green}{\text{Answer}}$

A system call is the programmatic way a computer program requests a service from the operating system kernel.

Some common Linux system calls are:

Process Control:
  - `fork()`: Creates a new process (a child process).
  - `execve()`: Replaces the current process image with a new program.
  - `wait()`/`wait4()`: Waits for a child process to terminate or stop.
  - `exit()`: Terminates the calling process.
  - `getpid()`: Gets the process ID of the current process
      
File Management (I/O):
  - `open()`/`openat()`: Opens or creates a file, returning a file descriptor.
  - `read()`: Reads data from a file descriptor.
  - `write()`: Writes data to a file descriptor.
  - `close()`: Closes a file descriptor.
  - `lseek()`: Changes the file offset (position) of a file descriptor.

Memory Management:
  - `brk()` / `sbrk()`: Changes the program's data segment size (heap allocation).
  - `mmap()`: Maps files or devices into memory.

Device Management / Information:
  - `ioctl()`: Performs device-specific I/O operations.
  - `stat()` / `fstat()` / `lstat()`: Gets file or file descriptor metadata (e.g., size, permissions).
  - `time()` / `gettimeofday()`: Gets the system time.

</details>

<details>
<summary><b><i>236.How a program executes a system call?</i></b></summary>

$\color{green}{\text{Answer}}$

A program executes a trap instruction. The instruction jump into the kernel while raising the privileged level to kernel space. Once in kernel space, it can perform any privileged operation. Once it's finished, it calls a "return-from-trap" instruction which returns to user space while reducing back the privilege level to user space.

</details>

<details>
<summary><b><i>237.Explain the fork() system call.</i></b></summary>

$\color{green}{\text{Answer}}$

`fork()` is used for creating a new process. It does so by cloning the calling process but the child process has its own PID and any memory locks, I/O operations and semaphores are not inherited.

</details>

<details>
<summary><b><i>238.What is the return value of fork()?</i></b></summary>

$\color{green}{\text{Answer}}$

- On success, the PID of the child process in parent and 0 in child process
- On error, -1 in the parent

</details>

<details>
<summary><b><i>239.Name one reason for fork() to fail.</i></b></summary>

$\color{green}{\text{Answer}}$

Not enough memory to create a new process

</details>

<details>
<summary><b><i>240.Why do we need the wait() system call?</i></b></summary>

$\color{green}{\text{Answer}}$

`wait()` is used by a parent process to wait for the child process to finish execution. If wait is not used by a parent process then a child process might become a zombie process.

</details>

<details>
<summary><b><i>241.How the kernel notifies the parent process about child process termination?</i></b></summary>

$\color{green}{\text{Answer}}$

The kernel notifies the parent by sending the SIGCHLD to the parent.

</details>

<details>
<summary><b><i>242.How the waitpid() is different from wait()?</i></b></summary>

$\color{green}{\text{Answer}}$

- The `waitpid()` is a non-blocking version of the wait() function.
- It also supports using library routine (e.g. `system()`) to wait a child process without messing up with other children processes for which the process has not waited.

</details>

<details>
<summary><b><i>243.True or False? The wait() system call won't return until the child process has run and exited.</i></b></summary>

$\color{green}{\text{Answer}}$

True in most cases though there are cases where wait() returns before the child exits.

</details>

<details>
<summary><b><i>244.Explain the exec() system call.</i></b></summary>

$\color{green}{\text{Answer}}$

It transforms the current running program into another program.

Given the name of an executable and some arguments, it loads the code and static data from the specified executable and overwrites its current code segment and current static code data. After initializing its memory space (like stack and heap) the OS runs the program passing any arguments as the argv of that process.

</details>

<details>
<summary><b><i>245.True or False? A successful call to exec() never returns.</i></b></summary>

$\color{green}{\text{Answer}}$

True, since a successful exec replace the current process, it can't return anything to the process that made the call.

</details>

<details>
<summary><b><i>246.What system call is used for listing files?</i></b></summary>

$\color{green}{\text{Answer}}$

There is no single system call that directly returns a list of files.

Listing files (reading directory contents) is typically accomplished in Linux using a sequence of operations based on these system calls:
  - `open()` or `openat()`: Opens the directory, returning a file descriptor.
  - `getdents()` (Get Directory Entries): This is the primary system call used to read raw directory entries from the file descriptor obtained in step 1.
  - `close()`: Closes the directory file descriptor.

In standard C programming, the `readdir()` function (part of the C library) is the wrapper that internally uses the `getdents()` system call to read and format the directory information for the user program.

</details>

<details>
<summary><b><i>247.What system calls are used for creating a new process?</i></b></summary>

$\color{green}{\text{Answer}}$

`fork()`, `exec()` and the `wait()` system call is also included in this workflow.

</details>

<details>
<summary><b><i>248.What execve() does?</i></b></summary>

$\color{green}{\text{Answer}}$

Executes a program. The program is passed as a filename (or path) and must be a binary executable or a script.

</details>

<details>
<summary><b><i>249.What is the return value of malloc?</i></b></summary>

$\color{green}{\text{Answer}}$

The return value of `malloc()` is a pointer of type `void*` (a "pointer to void").
  - This pointer points to the beginning of the block of newly allocated, uninitialized memory on the heap.
  - The `void*` type indicates that it's a generic pointer; it must be cast to the appropriate data type before being used (e.g., to `int*` or `struct Node*`).

On Failure:
  - If the requested memory allocation fails (e.g., due to insufficient memory), `malloc()` returns a null pointer ($\text{NULL}$). Always check for a $\text{NULL}$ return value.

</details>

<details>
<summary><b><i>250.Explain the pipe() system call. What does it used for?</i></b></summary>

$\color{green}{\text{Answer}}$

"Pipes provide a unidirectional interprocess communication channel. A pipe has a read end and a write end. Data written to the write end of a pipe can be read from the read end of the pipe. A pipe is created using pipe(2), which returns two file descriptors, one referring to the read end of the pipe, the other referring to the write end."

</details>

<details>
<summary><b><i>251.What happens when you execute `ls -l`?</i></b></summary>

$\color{green}{\text{Answer}}$

- Shell reads the input using getline() which reads the input file stream and stores into a buffer as a string
- The buffer is broken down into tokens and stored in an array this way: {"ls", "-l", "NULL"}
- Shell checks if an expansion is required (in case of ls *.c)
- Once the program in memory, its execution starts. First by calling readdir()

Notes:
  - `getline()` originates in GNU C library and used to read lines from input stream and stores those lines in the buffer

</details>

<details>
<summary><b><i>252.What happens when you execute ls -l *.log?</i></b></summary>

$\color{green}{\text{Answer}}$

When you execute ls -l *.log:
  - Shell Expansion: The shell (e.g., Bash) first replaces `*.log` with the list of all matching filenames (e.g., `a.log`, `b.log`) in the current directory.
  - Command Execution: The shell executes the `ls` command with the `-l` (long listing) option and the expanded file list as arguments.
  - Result: `ls` uses system calls (like `stat()`) to retrieve and print detailed metadata (permissions, size, owner, time) for each file ending in `.log`.

</details>

<details>
<summary><b><i>253.What readdir() system call does?</i></b></summary>

$\color{green}{\text{Answer}}$

The function `readdir()` (part of the C standard library, not a direct system call itself) is used to read the contents of a directory.

It repeatedly calls the underlying  `getdents()` system call to return information about the next file or directory entry (name, inode number, etc.) within a directory stream.

</details>

<details>
<summary><b><i>254.What exactly the command alias x=y does?</i></b></summary>

$\color{green}{\text{Answer}}$

The command `alias x=y` creates a temporary shortcut where the string `x` is replaced with the string `y` by the shell (e.g., Bash) whenever x is executed as the first word of a command.
  - `x` is the alias name (the new command).
  - `y` is the replacement string (the actual command or commands to execute).

This alias only persists for the current shell session.

</details>

<details>
<summary><b><i>255.Why running a new program is done using the fork() and exec() system calls? why a different API wasn't developed where there is one call to run a new program?</i></b></summary>

$\color{green}{\text{Answer}}$

This way provides a lot of flexibility. It allows the shell for example, to run code after the call to `fork()` but before the call to `exec()`. Such code can be used to alter the environment of the program it about to run.

</details>

<details>
<summary><b><i>256.Describe shortly what happens when you execute a command in the shell.</i></b></summary>

$\color{green}{\text{Answer}}$

The shell figures out, using the PATH variable, where the executable of the command resides in the filesystem. It then calls `fork()` to create a new child process for running the command. Once the fork was executed successfully, it calls a variant of `exec()` to execute the command and finally, waits the command to finish using `wait()`. When the child completes, the shell returns from `wait()` and prints out the prompt again.

</details>

## Filesystem & Files

<details>
<summary><b><i>257.How to create a file of a certain size?</i></b></summary>

$\color{green}{\text{Answer}}$

There are a couple of ways to do that:
  - dd if=/dev/urandom of=new_file.txt bs=2MB count=1
  - truncate -s 2M new_file.txt
  - fallocate -l 2097152 new_file.txt

</details>

<details>
<summary><b><i>258.What does the following block do?:
  
`open("/my/file") = 5`
`read(5, "file content")`

</i></b></summary>

$\color{green}{\text{Answer}}$

These system calls are reading the file `/my/file` and 5 is the file descriptor number.

</details>

<details>
<summary><b><i>259.Describe three different ways to remove a file (or its content)</i></b></summary>

$\color{green}{\text{Answer}}$

`rm filename`: Removes the file (inode and data blocks) from the filesystem entirely. This is the standard, permanent deletion command.
  
`truncate -s 0 filename`: Removes the content of the file (sets its size to 0 bytes) while keeping the file and its metadata (inode) intact.
  
`> filename` (Shell redirection): Removes the content of the file (truncates it) by redirecting null output into it. Similar to `truncate -s 0`, it keeps the file and its metadata.

</details>

<details>
<summary><b><i>260.What is the difference between a process and a thread?</i></b></summary>

$\color{green}{\text{Answer}}$

A Process is an independent, heavyweight execution of a program with its own dedicated, isolated virtual memory address space and resources (file descriptors, process ID - PID).

A Thread is a lightweight unit of execution within a process. Threads belonging to the same process share the process's memory space (code, data, and heap) and resources, but each has its own independent stack, registers, and Thread ID (LWP in Linux).

</details>

<details>
<summary><b><i>261.What is context switch?</i></b></summary>

$\color{green}{\text{Answer}}$

From wikipedia: a context switch is the process of storing the state of a process or thread, so that it can be restored and resume execution at a later point.

</details>

<details>
<summary><b><i>262.You found there is a server with high CPU load but you didn't find a process with high CPU. How is that possible?</i></b></summary>

$\color{green}{\text{Answer}}$

This is possible due to Interrupt Handling (IRQs) or Kernel Activity:

1.Interrupt Overload: A device (like a network card or storage controller) is generating a massive number of interrupts (IRQs). The CPU spends significant time executing the Kernel's interrupt handlers to service these events. Tools like top or ps report this time under the si (software interrupts) or ni (hardware interrupts) CPU usage fields, but it's not attributed to a specific user-space process.
    
2.Kernel Threads/Activity: The Kernel itself is busy with tasks (e.g., memory management, heavy I/O handling, scheduling) performed by kernel threads or core kernel routines. While some tools show this as sy (system time), it may not appear under a normal user-space process list.
    
3.Short-Lived Processes: Many processes are starting, executing, and terminating very rapidly, causing high load but making it difficult for periodic monitoring tools to catch any single process with sustained high CPU.

</details>

## Advanced Networking

<details>
<summary><b><i>263.When you run ip a you see there is a device called 'lo'. What is it and why do we need it?</i></b></summary>

$\color{green}{\text{Answer}}$

- `lo` stands for Loopback Interface.

- It is a virtual network interface that exists entirely in the operating system's software/kernel.

- Why is it Needed?
  - It is essential for:
    - 1.Local Communication: It allows a device to communicate with itself using standard network protocols (TCP/IP) without needing any physical hardware. Any data sent to the loopback address is immediately "looped" back up the network stack.

- 2.Testing/Development: It's used to test network services (like web servers, databases, or SSH daemons) and applications on the machine itself by connecting to the address 127.0.0.1 (or ::1 for IPv6, typically named localhost).

- 3.Guaranteed Availability: Because it's purely software, the loopback interface is always up and available, guaranteeing a working network path for inter-process communication on the host, even when all physical network interfaces are down.

</details>

<details>
<summary><b><i>264.What the traceroute command does? How does it works?</i></b></summary>

$\color{green}{\text{Answer}}$

- The `traceroute` command is a network diagnostic tool that displays the path (list of routers/hops) and the transit delays (latency) that data packets take to reach a specified destination host.

- It's primarily used to pinpoint where connection issues, latency, or packet loss are occurring along a network route.

How It Works
  - 1.It sends a series of probe packets (usually UDP or ICMP) to the destination, starting with TTL = 1.
  - 2.The first router (Hop 1) receives the packet, decrements the TTL to 0, discards the packet, and sends back an ICMP "Time Exceeded" error message, revealing its IP address.
  - 3.It repeats the process, incrementing the TTL by 1 for each subsequent set of packets (TTL = 2, TTL = 3, etc.).
  - 4.Each increment allows the packet to travel one hop further before it expires and triggers the "Time Exceeded" message from the next router.
  - 5.This continues until the packet finally reaches the destination, which responds with a different message, signifying the end of the trace.

</details>

<details>
<summary><b><i>265.What is network bonding? What types are you familiar with?</i></b></summary>

$\color{green}{\text{Answer}}$

Network Bonding (or NIC Teaming) is the Linux process of combining multiple physical network interfaces (NICs) into a single logical interface (e.g., bond0).

It is done to achieve:
  - Fault Tolerance/Redundancy: If one physical link or NIC fails, traffic automatically switches to the remaining links.
  - Load Balancing/Increased Throughput: Traffic is distributed across multiple active links, effectively increasing the available bandwidth.
 
Common Linux Bonding Modes:
  - Mode 1 (Active-Backup): Fault Tolerance. Only one NIC is active; others are standby. Simplest and most common.
  - Mode 0 (Balance-RR): Load Balancing. Transmits packets sequentially (Round-Robin) across all links.
  - Mode 4 (802.3ad (LACP)): Load Balancing & Fault Tolerance. Dynamic link aggregation. Uses an industry standard protocol.

</details>

<details>
<summary><b><i>266.How to link two separate network namespaces so you can ping an interface on one namespace from the second one?</i></b></summary>

$\color{green}{\text{Answer}}$

The primary method to link two separate Linux network namespaces (`netns`) for communication is using a Virtual Ethernet (veth) pair.

A veth pair acts as a virtual cable:
  - 1.Create Pair: Use `ip link add <vethA> type veth peer name <vethB>`.
  - 2.Move Ends: Place one end of the pair into the first namespace and the other end into the second.
    - `ip link set <vethA> netns <ns1>`
    - `ip link set <vethB> netns <ns2>`
  - 3.Configure: Assign IP addresses on the same subnet to the interfaces within their respective namespaces and bring them up.
    - e.g., `<vethA>` gets `10.0.0.1/24` in `ns1`, and `<vethB>` gets `10.0.0.2/24` in `ns2`.

Packets sent out of one end of the veth pair instantly arrive at the other end, enabling direct Layer 2 (Ethernet) communication and, consequently, ping (Layer 3) functionality between the two isolated namespaces.

</details>

<details>
<summary><b><i>267.What are cgroups?</i></b></summary>

$\color{green}{\text{Answer}}$

cgroups (Control Groups) is a Linux kernel feature that organizes processes hierarchically and allocates or limits system resources—such as CPU, memory, disk I/O, and network bandwidth—to those groups of processes.

</details>

<details>
<summary><b><i>268.Explain Process Descriptor and Task Structure</i></b></summary>

- `task_struct` (Process Descriptor) is a large data structure that contains hundreds of fields, providing the kernel with a complete picture of the process's current state and resources.
 
- The Task Structure refers to the way all active task_struct entries are logically organized by the kernel. The kernel typically manages these descriptors in a doubly linked circular list to allow for quick iteration over all running processes and to facilitate process scheduling and management.

</details>

<details>
<summary><b><i>269.What are the differences between threads and processes?</i></b></summary>

$\color{green}{\text{Answer}}$

- A Process is an isolated, heavy-weight instance of a program execution, complete with its own dedicated virtual memory space, resources, and Process ID (PID). Context switching between processes is slower due to the overhead of changing memory maps, but their isolation provides robust fault tolerance.

- A Thread is a light-weight unit of execution within a process. Threads belonging to the same process share the parent process's memory space, code, and resources (like file descriptors), but maintain their own stack and registers. This sharing allows for faster creation, quicker context switching, and easier communication between threads.

</details>

<details>
<summary><b><i>270.Explain Kernel Threads</i></b></summary>

$\color{green}{\text{Answer}}$

Kernel Threads are special threads that run entirely in kernel space and are not tied to any specific user-space process. They are managed by the kernel and perform tasks critical to the OS.

</details>

<details>
<summary><b><i>271.What happens when socket system call is used?</i></b></summary>

$\color{green}{\text{Answer}}$

When the `socket()` system call is used in Linux, the following happens:
  - 1.A request is made to the kernel to create a new network endpoint.
  - 2.The kernel creates a socket data structure internally (in kernel space) which holds all necessary information (like communication domain, type, protocol, state, and buffers).
  - 3.The kernel allocates a new, unused file descriptor number for this socket structure.
  - 4.The system call returns this new file descriptor to the calling process.

This file descriptor is used by subsequent system calls (like `bind()`, `connect()`, `send()`, `recv()`) to interact with the network. Essentially, `socket()` sets up the abstract communication channel endpoint.

</details>

<details>
<summary><b><i>272.You executed a script and while still running, it got accidentally removed. Is it possible to restore the script while it's still running?</i></b></summary>

$\color{green}{\text{Answer}}$

It is possible to restore a script while it's still running if it has been accidentally removed. The running script process still has the code in memory. You can use the /proc filesystem to retrieve the content of the running script.
 - 1.Find the Process ID by running ``` ps aux | grep yourscriptname.sh ``` Replace yourscriptname.sh with your script name.
 - 2.Once you have the PID, you can access the script's memory through the /proc filesystem. The script will be available at /proc//fd/, where is the process ID of the running script. Typically, the script's file descriptor is 0 or 1.

You can copy the script content to a new file using the cp command:
  - `cp /proc/<PID>/fd/0 /path_to_restore_your_file/yourscriptname.sh`

Replace with the actual PID of the script and
  - `/path_to_restore_your_file/yourscriptname.sh` with the path where you want to restore the script.

</details>

<details>
<summary><b><i>273.What is the difference between MemFree and MemAvailable in /proc/meminfo?</i></b></summary>

$\color{green}{\text{Answer}}$

- `MemFree` - The amount of unused physical RAM in your system
- `MemAvailable` - The amount of available memory for new workloads (without pushing system to use swap) based on MemFree, Active(file), Inactive(file), and SReclaimable.

</details>

<details>
<summary><b><i>274.What is the difference between paging and swapping?</i></b></summary>

$\color{green}{\text{Answer}}$

- Paging is a fundamental technique used in modern Linux Virtual Memory systems. It involves moving small, fixed-size chunks of a process's address space, called pages (typically 4KB), between RAM and disk (specifically, the swap space). Paging is frequent and enables Demand Paging, where only the necessary pages are loaded into memory, allowing a program to run even if only part of it is in RAM.

- Swapping (in its traditional sense) refers to moving the entire address space of an inactive process out of RAM and onto the disk to free up a large contiguous block of memory. This operation is much slower and less granular than paging. While the term "swapping" is still often used informally to describe moving pages to the swap space, modern Linux kernels primarily use paging mechanisms for virtual memory management, rarely performing full process swaps.

</details>

<details>
<summary><b><i>275.Explain what is OOM killer.</i></b></summary>

$\color{green}{\text{Answer}}$

The OOM (Out-Of-Memory) Killer is a Linux kernel component designed to gracefully recover the system when physical memory (RAM) is exhausted.

When the system runs out of memory and cannot satisfy new allocation requests, the OOM Killer steps in to:
  - 1.Select a "Victim": It uses a heuristic scoring algorithm to select the process that will cause the least damage and free the most memory. Processes with lower priority, large memory usage, and those that have recently increased their memory consumption are often targeted.
  - 2.Terminate: It forcibly kills the selected process (or processes) to immediately reclaim their memory and allow the system to continue operating, preventing a full crash or deadlock.

This behavior is a defensive mechanism, prioritizing system stability over individual application uptime. Processes can be configured to resist the OOM killer using the `oom_score_adj` setting.

</details>

## Distributions

<details>
<summary><b><i>276.What is a Linux distribution?</i></b></summary>

$\color{green}{\text{Answer}}$

- A Linux Distribution (Distro) is a complete, ready-to-use version of the Linux operating system.

- It consists of the Linux kernel combined with an extensive collection of GNU utilities (like the shell, file tools), system software (like `systemd`), libraries, and usually an installer, a package manager (like `apt` or `dnf`), and a specific set of desktop environments or applications.

</details>

<details>
<summary><b><i>277.What linux distributions are you familiar with?</i></b></summary>

$\color{green}{\text{Answer}}$

Some of the most well-known distributions I can discuss include:
  - Enterprise/Stability: Red Hat Enterprise Linux (RHEL), CentOS, Oracle Linux, and Debian.
  - User-Friendly/Desktop: Ubuntu, Fedora, Linux Mint, and Manjaro.
  - Security/Specialized: Kali Linux, Tails, and Alpine.
  - Minimal/Containerized: Alpine and CoreOS/Fedora CoreOS.

</details>

<details>
<summary><b><i>278.What are the components of a Linux distribution?</i></b></summary>

$\color{green}{\text{Answer}}$

- Kernel
- Utilities
- Services
- Software/Packages Management

</details>

## Sed

<details>
<summary><b><i>279.Using sed, extract the date from the following line: `201.7.19.90 - - [05/Jun/1985:13:42:99 +0000] "GET /site HTTP/1.1" 200 32421`</i></b></summary>

$\color{green}{\text{Answer}}$

`echo $line | sed 's/.*\[//g;s/].*//g;s/:.*//g'`

</details>

## Misc

<details>
<summary><b><i>280.What is a Linux distribution?</i></b></summary>

$\color{green}{\text{Answer}}$

A collection of packages - kernel, GNU, third party apps, ...
Sometimes distributions store some information on the distribution in `/etc/*-release` file
  - For example for Red Hat distribution it will be `/etc/redhat-release` and for Amazon it will be /etc/os-release
  - `lsb_release` is a common command you can use in multiple different distributions

</details>

<details>
<summary><b><i>281.Name 5 commands which are two letters long</i></b></summary>

$\color{green}{\text{Answer}}$

`ls`, `wc`, `dd`, `df`, `du`, `ps`, `ip`, `cp`, `cd` ...

</details>

<details>
<summary><b><i>282.What ways are there for creating a new empty file?</i></b></summary>

$\color{green}{\text{Answer}}$

`touch new_file`
`echo "" > new_file`

</details>

<details>
<summary><b><i>283.How `cd -` works? How does it knows the previous location?</i></b></summary>

$\color{green}{\text{Answer}}$

1.Updating `OLDPWD`: Every time you successfully use the `cd` command to change your directory, the shell automatically sets the value of the `OLDPWD` variable to the old current working directory (`$PWD`).

2.`cd -` Execution: When you execute `cd -`, the shell executes the equivalent of `cd $OLDPWD`.

3.Output: For convenience, the shell also prints the full path of the directory it has just switched to.

</details>

<details>
<summary><b><i>284.List three ways to print all the files in the current directory</i></b></summary>

$\color{green}{\text{Answer}}$

`ls`
`find .`
`echo *`

</details>

<details>
<summary><b><i>285.How to count the number of lines in a file? What about words?</i></b></summary>

$\color{green}{\text{Answer}}$

For these we can use `wc` command.
  - To count the number of lines in file `wc -l`
  - To count the number of words in file `wc -w`

</details>

<details>
<summary><b><i>286.You define x=2 in /etc/bashrc and x=6 ~/.bashrc you then login to the system. What would be the value of x?</i></b></summary>

$\color{green}{\text{Answer}}$

The value of x would be 6.

</details>

<details>
<summary><b><i>287.What is the difference between man and info?</i></b></summary>

$\color{green}{\text{Answer}}$

- `man` (manual pages) provides concise, traditional documentation for Linux commands, system calls, and configuration files. They are typically viewed one page at a time, formatted with a clear structure (NAME, SYNOPSIS, DESCRIPTION), and are generally better for quick lookups of command options or function signatures.

- `info` pages provide more comprehensive, hyperlinked documentation based on the GNU Texinfo format. They are structured like a manual or textbook, allowing the user to navigate between related nodes of information, which makes them ideal for in-depth tutorials and reading about complex GNU utilities in detail.

</details>

<details>
<summary><b><i>288.Explain "environment variables". How do you list all environment variables?</i></b></summary>

$\color{green}{\text{Answer}}$

Environment Variables are named values stored in the shell's memory that configure the runtime behavior of programs and processes. They are inherited by child processes.

- `env`: Lists only the variables passed to child processes.
- `printenv`: Lists environment variables (or a specific one).
- `set`: Lists all shell variables (environment, local, and functions).

</details>

<details>
<summary><b><i>289.What is a TTY device?</i></b></summary>

$\color{green}{\text{Answer}}$

A TTY (Teletypewriter or Teletype) device is the Linux term for any terminal interface that handles input/output for a user session.

TTY Types
  - 1.Console/Virtual Terminal (`/dev/ttyN`): The physical terminals accessed directly on the machine (usually via Ctrl+Alt+F1 through F6).
  - 2.Serial TTY (`/dev/ttyS`): Used for communication over serial ports.
  - 3.Pseudo-TTY (PTY) (`/dev/pts/N`): The most common type today, used by remote login sessions (SSH), terminal emulators (like GNOME Terminal or Konsole), and programs like screen or tmux.

</details>

<details>
<summary><b><i>290.How to create your own environment variables?</i></b></summary>

$\color{green}{\text{Answer}}$

`X=2` for example. But this will persist to new shells. To have it in new shells as well, use `export X=2`

</details>

<details>
<summary><b><i>291.What a double dash (--) mean?</i></b></summary>

$\color{green}{\text{Answer}}$

It's used in commands to mark the end of commands options. One common example is when used with git to discard local changes: `git checkout -- some_file`

</details>

<details>
<summary><b><i>292.Wildcards are implemented on user or kernel space?</i></b></summary>

$\color{green}{\text{Answer}}$

- Wildcards (like `*`, `?`, `[]`) are implemented in user space by the shell (e.g., Bash) before the command is executed.
  
- This process is called globbing or pathname expansion. The kernel only receives the final, expanded list of matching filenames as arguments, not the wildcard pattern itself. 

</details>

<details>
<summary><b><i>293.If I plug a new device into a Linux machine, where on the system, a new device entry/file will be created?</i></b></summary>

$\color{green}{\text{Answer}}$

`/dev`

</details>

<details>
<summary><b><i>294.Why there are different sections in man? What is the difference between the sections?</i></b></summary>

$\color{green}{\text{Answer}}$

The man (manual) pages are divided into numbered sections primarily to organize documentation by category and prevent naming conflicts between different types of files or functions (e.g., a user command and a configuration file might share the same name).

The core difference lies in the context of the documentation:
  - Section 1 covers executable commands (things you run, like ls or grep)
  - Section 2 covers system calls (functions programmers use to request services from the kernel, like open or fork)
  - Section 5 covers file formats and conventions (like /etc/passwd).

This structure allows users and developers to quickly find the relevant documentation for the specific component they are interested in.

</details>

<details>
<summary><b><i>295.What is User-mode Linux?</i></b></summary>

$\color{green}{\text{Answer}}$

- In Linux, user mode is a restricted operating mode in which a user's application or process runs. User mode is a non-privileged mode that prevents user-level processes from accessing sensitive system resources directly.
In user mode, an application can only access hardware resources indirectly, by calling system services or functions provided by the operating system. This ensures that the system's security and stability are maintained by preventing user processes from interfering with or damaging system resources.

- Additionally, user mode also provides memory protection to prevent applications from accessing unauthorized memory locations. This is done by assigning each process its own virtual memory space, which is isolated from other processes.

- In contrast to user mode, kernel mode is a privileged operating mode in which the operating system's kernel has full access to system resources, and can perform low-level operations, such as accessing hardware devices and managing system resources directly.

</details>

<details>
<summary><b><i>296.Under which license Linux is distributed?</i></b></summary>

$\color{green}{\text{Answer}}$

GPL v2

</details>

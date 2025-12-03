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





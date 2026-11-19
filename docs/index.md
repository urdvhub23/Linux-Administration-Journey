# Linux Systems Administration 
Start: Nov.3.26, Tue | Time: 05:16am
End: Nov.3.26, Tue | Time: 6:00am
Total Time

Part-1: Administration
----------------------
#### Notes During Lecture/Class:
---
#### Links:

---
#### Terms:
- Kernel
- OS Version:
- Kernel Args:
- Modules
- Mount Points:
- Text Editor:
- Semantic Versioning:
- Code Reviews:
---
#### Useful tools:
---
#### Digging Deeper:
---
#### Reflective Questions:
> 1. What questions do you still have this week?
> 2. How are you going to use what you've learned in your current role?
> 3. What you have build?
> 4. Thinking as a DevOps
> 5. Why should I listen to you?
> 6. How much confident are you in your learning?
> 7. How Linux Works?
> 8. Scalability, Reliability and Security in Linux
> 9. Infrastructure, Access, Security
> 10. What is achieveable for you?
> 11. Order of Learning
---
#### Nov 4.26, Tue | Start: 2:41 am PST
#### End: Wed Nov  4 07:22:20 PKT 2026
---
### Session-2
---
You are a new system administrator at a company. 
You've been tasked with finding out information 
about a set of servers that has very little to no 
documentation on it. You find yourself at a command prompt 
and need to find out what type of system you are working on.

1. What is the release and version of the system?
2. What is the kernel version?
3. How long has the system been up, and how was its kernel called as GRUB booted it?
4. Use the Solution to follow along and look around a new Linux system for the first time.
---
#### Notes During Lecture/Class:
---
#### Links:
---
#### Terms:
1. Kernel
2. OS Version:
3. Kernel Args:
4. Modules:
	- modules are things that plug in the the term modular means that we can add or remove components without breaking other pieces.
5. Mount Points:
6. Text Editor:
7. Semantic Versioning:
8. Code Reviews:
-----------------------
#### Command Notes:

1. First we check what version of Linux we're on.
> cat /etc/*release
	

2. Next we check the kernel version.
- apropos (2): get name and information about current kernel
	> - uname -r
	> - uname -a

3. Next we might want to know how long the system has been up.
	> uptime
	> Description:
		- uptime  gives a one line display of the following information. 			- The current time, how long the system has been running, how many users are currently logged on, and the system load averages for the past 1, 5, and 15 minutes.

4. Next we might want to see how the system booted and what kernel parameters were passed when the system was started.
	> $cat /proc/cmdline
---
#### Terms:
	> cat - concatenate files and print on the standard output
	#proc - process information, system information, and sysctl pseudo-filesystem
	#cmdline - root file containing info about kernel process starting on boot.
------------------

Useful tools:

Digging Deeper:

Reflection Questions:
---------------------
---------------------
#### Raw Notes:
> Mount points map what's going on with block devices in my system devices and the places that they exist in the file system.
>
>> Now let's dig a little deeper

Do each command and think about what output you're looking at. You may run them multiple times, if needed and to compare the output.

Solution
Let's look at the virtual memory usage of this system.
		vmstat 1 5

What are you seeing here? Is this system under high memory usage or not?

Next we check the overall CPU usage of the system every second for 5 seconds.

		mpstat 1 5

Is this system under high CPU load or not?

Next we check what processes are running on the system

		ps -ef
		ps -ef | awk '{print $1}' | sort | uniq -c

What users is using the most processes? Do you think this system is doing any real work or just sitting there running an OS?

Next we check what processes are executing on the processor every second.

pidstat 1 5

Why do these have different length output? What processes were using the most CPU? Which showed up the most often?

Next we may want to see more CPU and Disk usage on the system in 1 second increments. Do you think you could modify this to run for 30 seconds?

iostat -xz 1 5
---------------------------
Linux Commands to see networking traffic and load
Now let's dig a little deeper into networking

Do each command and think about what output you're looking at. You may run them multiple times, if needed and to compare the output.


Solution
Solution
Let's look at the network usage and load of the system.
sar -n DEV 1 5

What are you seeing here? What devices are showing up? Do any devices seem to be under high load? Which one has the most traffic?

Next we check tcp packets and errors.

sar -n TCP,ETCP 1 5

Do we appear to be seeing any large numbers of errors? Why might retransmits be a big problem?
-----------------------------------------------------
vi-editor sections:
-------------------
write changes to a new file:

$w newfile
 
view a file in read-only mode

$view file_name

command(program) Options/Switches Arguments
Options and Args change the behavior of the command entirely.
-------------------------------------------------------------
understand where the value is as an engineer - write article
-----------------------
$info command_name

NAME
       info - read Info documents

SYNOPSIS
       info [OPTION]... [MENU-ITEM...]

###### DESCRIPTION
> Read documentation in Info format.
-----------------------------------------
- *understand recursion*
---
##### Wed Nov  4 05:04:06 PKT 2026
* date cmd usage for logs
* start of Unix
* unix time
* epoch time
----------------------
#### Wed Nov  4 05:29:28 PKT 2026
	```
	pwd
	
	```
* echo $$
--------
#### NAME: lsof - list open files

**DESCRIPTION**
+ Lsof  revision  4.95.0 lists on its standard output file information about files opened by processes for the following UNIX dialects:

            Apple Darwin 9 and Mac OS X 10.[567]
            FreeBSD 8.[234], 9.0 and 1[012].0 for AMD64-based systems
            Linux 2.1.72 and above for x86-based systems
            Solaris 9, 10 and 11

       (See the DISTRIBUTION section of this manual page for information on how to obtain the latest lsof revision.)

       An open file may be a regular file, a directory, a block special file, a character  special  file,  an  executing
       text  reference, a library, a stream or a network file (Internet socket, NFS file or UNIX domain socket.)  A spe‐
       cific file or all the files in a file system may be selected by path.

       Instead of a formatted display, lsof will produce output that can be parsed by other programs.  See the  -F,  op‐
       tion description, and the OUTPUT FOR OTHER PROGRAMS section for more information.

       In addition to producing a single output list, lsof will run in repeat mode.  In repeat mode it will produce out‐
       put,  delay,  then  repeat  the  output  operation  until stopped with an interrupt or quit signal.  See the +|-r
       [t[m<fmt>]] option description for more information.
---
ps - report a snapshot of the current processes.
ps displays information about a selection of the active processes.  If you want a repetitive update of the selection and the displayed information, use top instead.
---
lrwxrwxrwx  1 urdevop2526 urdevop2526       27 Jul 10 18:01 .aws -> /mnt/c/Users/Education/.aws
lrwxrwxrwx  1 urdevop2526 urdevop2526       29 Jul 10 18:01 .azure -> /mnt/c/Users/Education/.azure

l - symbolic link
------------------
Wed Nov  4 06:38:17 PKT 2026

Process Management
------------------
#### Commands:
1. find
2. which
3. whereis
4. whatis
5. echo $PS1
6. echo $PATH
7. env; printenv
8. timedatectl
9. ps -aux
10. ps -ef
11. cal -3 y
12. top
13. ps -ef | grep -i "tcp"
14. ps -eo lstart,cmd,pid,ppid | grep -i tcp
15. lsof -p | grep -i
16. ss -ntulp | grep -i
17. systemctl | grep -i name.service
18. systemctl cat name.service
---
##### Wed Nov  4 07:11:25 PKT 2026
1. kill
2. ps -ef | grep -i [c]alico | awk '{print $2}'
3. ps -ef | grep -i [c]alico | awk '{print $2}' |xargs
4. ps -ef | grep -i [c]alico | awk '{print $2}' | xargs kill

-----------------------------------------
Terms:
------
*container networking infrastructure

Useful tools:

Digging Deeper:

Reflection Questions:
---------------------
----------------------
---Wed Nov 4, 2026 2:22:02 PM---
---------------------------------
Session-3
Thu Nov  5 01:56:47 PKT 2026

## /Linux-Labs/01-system-checking

	- You are a new system administrator at a company. You've been tasked with finding out information about a set of servers that has very little to no documentation on it. You find yourself at a command prompt and need to find out what type of system you are working on.
	- What is the release and version of the system?
	- What is the kernel version?
	- How long has the system been up, and how was its kernel called as GRUB booted it?
	- Use the Solution to follow along and look around a new Linux system for the first time.
	
	#First we check what version of Linux we're on.
	
	$cat /etc/*release

	#Next we check the kernel version.
	
	$uname -r

	#Next we might want to know how long the system has been up.

	$uptime

	#Next we might want to see how the system booted and what kernel parameters were passed when the system was started.

		$cat /proc/cmdline
			#Output: cat /proc/cmdline
			#initrd=\initrd.img WSL_ROOT_INIT=1 
			#panic=-1 nr_cpus=8 
			#hv_utils.timesync_implicit=1 
			#printk.devkmsg=on page_reporting.page_reporting_order=5 
			#hv_storvsc.storvsc_max_hw_queues=4 
			#console=hvc0 
			#debug 
			#pty.legacy_count=0 
			#WSL_ENABLE_CRASH_DUMP=1
	
	## Now let's dig a little deeper
	## Do each command and think about what output you're looking at. You may run them multiple times, if needed and to compare the output.

	#### Let's look at the virtual memory usage of this system.
		
```shell
vmstat 1 5
		
```
- What are you seeing here? Is this system under high memory usage or not?
- Next we check the overall CPU usage of the system every second for 5 seconds.

	`$mpstat 1 5`

- Is this system under high CPU load or not?
-  Next we check what processes are running on the system

		$ps -ef
		$ps -ef | awk '{print $1}' | sort | uniq -c

	#What users is using the most processes? Do you think this system is doing any real work or just sitting there running an OS?

	#Next we check what processes are executing on the processor every second.

		$pidstat 1 5

	#Why do these have different length output? What processes were using the most CPU? Which showed up the most often?

	#Next we may want to see more CPU and Disk usage on the system in 1 second increments. Do you think you could modify this to run for 30 seconds?

		$iostat -xz 1 5

	#Let's look at the network usage and load of the system.
		$sar -n DEV 1 5

	#What are you seeing here? What devices are showing up? Do any devices seem to be under high load? Which one has the most traffic?

	#Next we check tcp packets and errors.

		$sar -n TCP,ETCP 1 5

	#Do we appear to be seeing any large numbers of errors? Why might retransmits be a big problem?
---
## Session-1:
###### Start@Thursday, November 5, 2026 11:47:24 PM | End@

#### Links
#### Notes During Lecture/Class:
---
#### Links:

---
#### Terms:

---
#### Useful tools:
---
#### Digging Deeper:
---
#### Reflective Questions:
1.
---
#### What questions do you still have this week?
1.
---
#### How are you going to use what you've learned in your current role?
1.
---
#### What you have build?
1.
---
#### Thinking as a DevOps
1.
---
#### Why should I listen to you?
1.
---
#### How much confident are you in your learning?
1.
---
#### How Linux Works?
1.
---
#### Scalability, Reliability and Security in Linux
1.
---
#### Infrastructure, Access, Security
1.
---
#### What is achieveable for you?
1.
---
#### Order of Learning
1.
---
# Session-2
**Thu Nov 12 07:49:56 PKT 2026**
#### Links
	- https://lsof.readthedocs.io/en/latest/maintaining/
	- https://dev.to/pldg/customize-shell-prompt-2bpa
#### Notes
forget to write
---
# Session-3 & 4
**Saturday, November 14, 2026 9:28:43 AM**
**Links:**
1. Terminal/CLI Fundamentals
```
https://www.youtube.com/playlist?list=PLXJyD2dL4oqc93ARRc-ycwnlZ2CTmdUOe
```
2. Server Deployment
```
https://www.youtube.com/playlist?list=PLXacJyD2dL4oqdQA7QRRFd2Tvev2BAupyOr
```
3. SysAdmin Career/Interview
```
https://www.youtube.com/playlist?list=PLXJyD2dL4oqdKLI7elGZnxAAXtyB8s_cF
```
4. Performance Tuning and Benchmarking
```
https://www.youtube.com/playlist?list=PLXJyD2dL4oqcuAp2yp7j2e9e-3a_P4-A8
```

5. SystemD
```
https://www.youtube.com/playlist?list=PLXJyD2dL4oqeK7d5fIvqbrAuTnVY3SYkF
```
---

**Session 5**
Tue Nov 17 06:39:35 PKT 2026
#### Links
- github.com/het-tanis
#### Terms

#### Useful Tools

---
1. Revision--->Lecture-1
   1. block devices
   2. mount point
   3. case sensitive
   4. :w newfile_name
   5. short keys for vi, vim, nano
**Session 6**
Wed Nov 18 02:11:06 PKT 2026
   6. Linux Engineering Skillset
   7. being an engineer means "build stuff".
   8. understand where the value is.
   9. info+man+[--help]-->for command-help
   10. cal -jy --> julian day
   11. location utilities
       1. ls $PATH --> shows directory contents (files+directories)
       2. Permissions --> rwx, numerical method, alphabetic method
   12. echo $$ --> shows process id in bash shell is currently working
   13. Working with directories
       1. any HOME=dir_name can be set as HOME_DIR for locking yourself for specific tasks.
       2. find
          1. find DIR_NAME -n file* or *file
       3. whereis
       4. which
       5. echo $PATH
       6. env; printenv
       7. echo $VAR_NAME --> show variable path
    14. System Utilities
        1. echo $PS1 --> shows info about current shell or command prompt
        2. top
        3. kill
        4. ps -ef | grep -i PROCESS_NAME --> filters selected processes
        5. ps -eo lstart,cmd,pid,ppid | grep -i PROCESS_NAME --> filters specific informaton about the process.
        6. ps -eo lstart,cmd,pid,ppid | grep -i PROCESS_NAME
        7. lsof -p PID
        8. ss -ntulp | grep -i PROCESS_NAME or DEVICE_NAME
           1. ss -t -a -Z
        9. startup scripts
        10. systemctl
            1. systemctl may be used to introspect and control the state of the "systemd" system and service manager.
            2. Commands
               1. **Unit Commands (Introspection and Modification)**
                  1. list-units [PATTERN...]
                  2. list-automounts [PATTERN...]
                  3. list-paths [PATTERN...]
                  4. list-sockets [PATTERN...]
                  5. list-timers [PATTERN...]
                  6. is-active PATTERN...
                  7. is-failed [PATTERN...]
                  8. status [PATTERN...|PID...]]
                  9. show [PATTERN...|JOB...]
                  10. cat PATTERN...
                  11. help PATTERN...|PID...
                  12. list-dependencies [UNIT...]
                  13. start PATTERN...
                  14. stop PATTERN...
                  15. reload PATTERN...
                  16. restart PATTERN...
                  17. try-restart PATTERN...
                  18. try-reload-or-restart PATTERN...
                  19. isolate UNIT
                  20. kill PATTERN...
                  21. clean PATTERN...
                  22. freeze PATTERN...
                  23. 
            3. systemctl cat ssh.service
                ```    
                # /usr/lib/systemd/system/ssh.service
                [Unit]
                Description=OpenBSD Secure Shell server
                Documentation=man:sshd(8) man:sshd_config(5)
                After=network.target auditd.service
                ConditionPathExists=!/etc/ssh/sshd_not_to_be_run

                [Service]
                EnvironmentFile=-/etc/default/ssh
                ExecStartPre=/usr/sbin/sshd -t
                ExecStart=/usr/sbin/sshd -D $SSHD_OPTS
                ExecReload=/usr/sbin/sshd -t
                ExecReload=/bin/kill -HUP $MAINPID
                KillMode=process
                Restart=on-failure
                RestartPreventExitStatus=255
                Type=notify
                RuntimeDirectory=sshd
                RuntimeDirectoryMode=0755

                [Install]
                WantedBy=multi-user.target
                Alias=sshd.service
                ```
            ```
            useradd -m zeeshan
            su - zeeshan
            ls -la
            chmod 750 /usr/sbin/ModemManager
            ls -l /usr/sbin/ModemManager
            ```
**Session 7**
**Thu Nov 19 04:36:56 PKT 2026**
Thu Nov 19 05:08:09 PKT 2026

**Revision of Session 5-6**
1. Block Devices:
   1. https://unix.stackexchange.com/questions/437567/displaying-physical-block-devices [1]
      1. lsblk (8)- list block devices
        - Examples:
          - lsblk -a -d -e 230 [1]
            
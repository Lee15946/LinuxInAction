## Linux System Administration

### Linux File Editor

- A text editor is a program which enables you to create and manipulate data (text) in a Linux file
- There are several standard text editors available on most Linux systems
    - vi = Visual editor
    - ed = Standard line editor
    - ex = Extended line editor
    - emacs = A full screen editor
    - pico = Beginner's editor
    - vim = Advance version of vi
- Our editor = vi (available in almost every Linux distribution)

### Introduction to vi Editor

- vi supplies commands for
    - Inserting and deleting text
    - Replacing text
    - Moving around the file
    - Finding and substituting strings
    - Cutting and pasting text
- Most common keys:
    - i = insert
    - Esc = Escape out of any mode
    - r = replace
    - d = delete
    - :q! = quit without saving
    - :wq! = quit and save

### Difference between vi and vim Editor

- As far as function is concerned, both editors work in the same manner. Which editor you choose is a matter of personal choice. Some people recommend learning the vim editor instead of the vi editor. Due to added features, learning and using vim editor is muc easier than the vi editor
- Since vim is based on the vi, when you will learn how to use the vim editor, you will automatically learn how to use the vi editor
- vim has all the features as vi with some excellent addition
- There's also a comprehensive help systems and lots of customization options available.

### "vim" Interactive Learning Tools

- There are many websites that are offer free vim interactive training
    - openvim
    - vimgenius
    - vim-adventures

### "sed" Command

- Replace a string in a file with a new string
- Find and delete a line
- Remove empty lines
- Remove the first or n lines in a file
- To replace tabs with spaces
- Show defined lines for a file
- Substitute within vi editor
- And much more....

### User Account Management

- Commands
    - useradd
    - groupadd
    - userdel
    - groupdel
    - usermod
- Files
    - /etc/passwd
    - /etc/group
    - /etc/shadow
- Example
    - useradd -g superheros -s /bin/bash -c "user description" -m -d /home/spiderman spiderman

### Enable Password Aging

- File = /etc/login.def
    - PASS_MAX_DAYS = 9999
    - PASS_MIN_DAYS = 0
    - PASS_MIN_LEN = 5
    - PASS_WARN_AGE = 7
- The chage Command - per user
    - chage [-m mindays] [-M maxdays] [-d lastday] [-I inactive] [-E expiredate] [-W warndays] user
    - -d = 3. Last password change(lastchanged): Days since Jan 1, 1970 that password was last changed
    - -m = 4. Minimum: The minimum number of days required between password changes, i.e. the number of days left before the user is allowed to change his/her password
    - -M = 5. Maximum: The maximum number of days the password is valid (after that user is forced to changes his/her password)
    - -W = 6. Warn: The number of days before password is to expire that used is warned that his/her password must be changed
    - -I = 7. Inactive: The number of days after password expires that accounts is disabled
    - -E = 8. Expire: days since Jan 1, 1970 that account is disabled, i.e. an absolute date specifying when the login may no longer be used

### Switch Users and sudo Access

- Commands
    - su - username
    - sudo command
    - visudo
- File
    - /etc/sudoers

### Monitor Users (who, last, w, id)

- who
- last
- w
- finger
    - To install finger command on CentOS7, become root and run `yun install finger -y`
    - CentOS8 and above "finger" command is now replaced with "pinky"
- id

### Talking to Users

- users
- wall
- write

### Linux Account Authentication

- Type of Accounts
    - Local accounts
    - Domain/Directory accounts
- Client -> Account authentication -> Server -> User authenticated -> Server
- Windows = Active Directory
- Linux = LDAP? -> Lightweight Directory Access Protocol

### Difference between Active Directory, LDAP, IDM, WinBIND, OpenLDAP etc.

- Active Directory = Microsoft
- IDM = Identity Manager
- WinBIND = Used in Linux to communicate with Windows (Samba)
- OpenLDAP (open source)
- IBM Directory Server
- JumpCloud
- LDAP = Lightweight Directory Access Protocol

### System Utility Commands

- date
- uptime
    - Each filed in uptime
    - 11:18:23 up 83 days, 18:29, 4 users, load average: 0.16, 0.03, 0.01
    - 11:18:23 - that's the current Linux system time
    - up 83 days, 18:29 - shows for how long your system has been running
    - 4 users - number of users currently logged into your Linux system
    - load average: 0.16, 0.03, 0.01 - the average CPU load (average number of jobs in your system's run queue) for the 1, 5, and 15 minutes
- hostname
- uname
    - System information
- which
- cal
    - Calendar
- bc
    - Calculator

### Processes and Jobs

- Application = Service
    - Windows = Office Word, Powerpoint, Firefox
    - Linux = NTP, NFS, rsyslog, Apache
- Script
    - Shell scripts or Commands are list of instructions, e.g. adduser, cd, pwd etc.
- Process
    - Service --> Process1
    -             Process2
    -             Process3
- Daemon
    - Runs until interrupted
- Threads
    - Service --> Process --> thread1
        -                       thread2
        -                       thread3
        -                       thread4
- Job
    - Job or Workorder = Run as service or process at a schedule time

### Process / Services Commands

- systemctl or service
    - Redhat version 7 and 8 use systemctl
- ps
    - See what are the process running in your Linux system
- top
    - See process based on its load, CPU, memory
- kill
    - Kill by the process name or kills by the process id
- crontab
    - Control whe the process or application is scheduled in crontab
- at
    - Schedule as one time basis or as an ad hoc process

### systemctl command

- systemctl command is a new tool to control systemc services
- It is available in version 7 and later and it replaces the service command
- Usage example:
    - `systemctl start|stop|status servicename.service` (firewalld)
    - `systemctl enable servicename.service` (start service when your system starts at boot)
    - `systemctl restart|reload serivcename.service`
    - `systemctl list-units --all`
        - The output has the following columns:
            - UNIT: The systemd unit name
            - LOAD: Whether the unit's configuration has been parsed by systemd. The configuration of loaded units is kept in memory
            - ACTIVE: A summary state about whether the unit is active. This is actually a fairly basic way to tell if the unit has started successfully or not
            - SUB: This is a lower-level state that indicates more detailed information about the unit. This often varies by unit type, state and the actual method in which the unit runs
            - DESCRIPTION: A short textual description of what the unit is/does

#### systemctl command

- To add a service under systemctl management:
    - Create a unit file in /etc/systemd/system/servicename.service
- To control system with systemctl
    - `systemctl poweroff`
    - `systemctl halt`
    - `systemctl reboot`

### "ps" command

- ps command stands for process status and it displays all the currently running processes in the Linux system
- Usage examples:
    - ps = Shows the processes of the current shell
        - PID = the unique process ID
        - TTY = terminal type that the user logged-in to
        - TIME = amount of CPU in minutes and seconds that the process has been running
        - CMD = name of the command
    - ps -e = Shows all running processes
    - ps aux = Shows all running processes in BSD format (Berkeley Systems Description)
    - ps -ef = Shows all running processes in full format listing (Most commonly used)
    - ps -u username = Shows all processes by username

#### top command

- top command is used to show the Linux processes and it provides a real-time view of the running system
- This command shows the summary information of the system and the list of processes of threads which currently managed by the Linux Kernel
- When the top command is executed then it goes into interactive mode and you can exit by hitting q
- Usage:
    - top
        - PID: Show task's unique process id
        - USER: Username of owner of task
        - PR: The "PR" field shows the scheduling priority of the process from the perspective of the kernel
        - NI: Represents a Nice Value of task. A Negative nice value implies higher priority, and positive Nice value means lower priority
        - VIRT: Total virtual memory used by the task
        - RES: Memory consumed by the process in RAM
        - SHR: Represents the amount of shared memory used by a task
        - S: This field shows the process state in the single-letter form
        - %CPU: Represents the CPU usage
        - %MEM: Shows the Memory usage of task
        - TIME+: CPU Time, the same as "TIME", but reflecting more granularity through hundredths of a second
    - top -u yuhuali = show tasks/processes by user owned
    - top then press c = shows commands absolute path
    - top then press k = kill a process by PID within top session
    - top then M and P = To sort all Linux running processes by Memory usage
- Please note: Top command refreshes the information every 3 seconds

### "kill" command

- kill command is used to terminate processes manually
- It sends a signal which ultimately terminates or kills a particular process or group of processes
- Usage
    - kill [option] [PID]
        - OPTION = Signal name or signal number / ID
        - PID = Process ID
    - kill -l = to get a list of all signal names or signal number
    - Most used signals are
        - kill PID = Kill a process with default signal
        - kill -1 = Restart
        - kill -2 = Interrupt from the keyboard just like Ctrl C
        - kill -9 = Forcefully kill the process
        - kill -15 = Kill a process gracefully
















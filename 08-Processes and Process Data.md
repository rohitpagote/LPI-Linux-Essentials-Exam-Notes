# Package Management Principles
## Process
- A process is any running program is the Linux system.

## Package
- A package is a compressed achieve that contains all the files that are required by a particular software to run.
- Package software maintains a database of information about all installed packages, which includes:
    - Names and version numbers
    - Locations of all installed files

## Package Management Principles
- Each package is a single .
- Packages rely on other programs to do the work of installing the software.
- Packages contain dependency information.
- Packages contain version information.
- Packages contain architecture information.
- Binary packages are built from source packages.

---

# Package Management Systems (Package Managers)
- One of the common ways to categorize Linux distribution is by the package manager it uses.
- For example:
    - Distributions such as RHEL, Fedora and CentOS. are based on RPM. Hence they are known as RPM based distribution.
    - The Debian family including Ubuntu, Debian and Linux Mint e.t.c. make use of Debian based package managers such as the DPKG.
- A package manager is a software in a Linux system that provides the consistent and automated process in installing, upgrading, configuring and removing packages from the operating system.
- Always use native packages on your system.
- Software Repositories: Place from where software can be automatically downloaded as packages and then get installed.
- Software Installation Process:
    - A command is issued to install a program
    - The software locates dependencies of the specified program
    - The user issues a final approval for software installation
    - The software downloads all of the necessary packages
    - The software installs all the packages

---

# Process Hierarchy
- Init Process (<code>/sbin/init</code>)
    - Responsible for starting up all basic programs that Linux needs to run.
    - Children: Program launched by init.
    - Parent: Process that launched a program.
- Each process has a **Process ID (PID)** associated with it. 
- Init process has a PID of 1.
- Parent Process ID (PPID): Points to a parent of that process.

---

# Identifying Running Processes
## Utilities/Tools to identify processes
### <code>ps</code>: 
- The <code>ps</code> command in Linux displays a snapshot of the currently running processes on the system, providing information like process ID (PID), user, CPU usage, and command name.
- Basic Usage:
    - <code>ps</code> (without options): Displays processes associated with the current terminal. 
    - <code>ps aux</code>: Shows all processes, including those not associated with a terminal, along with their user, CPU usage, and memory usage. 
    - <code>ps -ef</code>: Lists all processes, including those associated with a terminal, showing the process ID (PID), user, and command. 

### <code>top</code>
- The <code>top</code> (table of processes) command shows a dynamic, real-time view of running processes and kernel-managed tasks in Linux.
- It is an interactive version of <code>ps</code>.
- It sorts the process which are consuming most CPU.

### <code>free</code>
- The <code>free</code> command in Linux displays the amount of free and used system memory (RAM) and swap space.
- The output shows the total, used, free, shared, buffers/cache, and available memory, as well as swap usage. 

## Load Average
- Measure of the demand of CPU time by different applications.
- Useful in detecting “runaway processes”.

---

# Measuring Memory Usage
- Pressing the **M** key on keyboard within <code>top</code> command sorts the processes by memory usage.
- A program with a memory leak consumes increasing amounts of memory.
- **Mem**: This line reveals total RAM statistics.
- **Swap**: This line reveals how much swap space Linux is using (disk space that’s set aside as an adjunct to memory, also called as virtual memory).
- The <code>free</code> command can also be use to check the used and free memory.
- The output of the free command provides valuable insights into system memory: 
    - Total: The total amount of RAM available on the system.
    - Used: The memory currently in use by processes.
    - Free: The amount of memory that is not being used by processes.
    - Shared: Memory shared by multiple processes.
    - Buffers/Cache: Memory used by the kernel for buffers, page cache, and slabs.
    - Available: The total amount of memory that can be used by applications and processes.
    - Swap: Swap space usage.

---

# Log Files
- Log files are frequently rotated.
- Log files are mostly plaintext files.
- Serve as a record or notes.
- Mostly stored in <code>/var/log</code> directory.

## Daemons
- Daemon is a program that run in the background.

## Common Log Files
- **boot.log**: Summary of services that started up late in the boot process through the systemd init startup scripts.
- **cups/**: Holds the log files related to Linux printing system.
- **gdm/**:
    - Holds the log files related to the gnome display manager or GDM environment.
    - This handles graphical-based user logins.
- **messages or syslog**: General purpose log file containing messages from many different daemons that don’t have dedicated log files.
- **Secure**: It stores security-related messages.
- **Xorg.0.log**: Info about the most recent startup of an X windows system can be found inside this log file.

## Syslog/Syslogd (system log daemon)
- It is a general standard protocol for logging system and program messages.

## Klog/Klogd (kernel log daemon)
- Klogd is a kernel log daemon that intercepts and processes log messages from the kernel.
- It handles logging messages from the kernel separately from ordinary programs.

## System Messaging
- It is a technique wherein a log daemon accepts messages from other processes.

---

# Kernel Ring Buffer
- The Linux Kernel Ring Buffer is a log file, but for the kernel itself.
- It is a fixed-size circular buffer used to store kernel log messages and other important information.
- However, unlike other log files, it is stored in memory rather than in a disk file.
- Like regular log files though, its contents are continuing to change as the computer runs.
- This buffer is available to userspace through the <code>dmesg</code> command, allowing system administrators to view and troubleshoot kernel-related issues. 
- Kernel ring buffer messages are invaluable in diagnosing hardware and driver problems.
- Some distributions place a copy  the kernel ring buffer into the <code>/var/log/dmesg</code> directory when the system first boots up.
- To manually create a kernel ring buffer log file (if the distribution doesn't create it bydefault), edit <code>/etc/rc.d/rc.local</code> by adding this at the end: <code>dmesg > /var/log/dmesg</code>.

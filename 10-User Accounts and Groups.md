# Understanding Linux Accounts (User Accounts)
- A **Linux account** is a unique user identity that grants access to a Linux system.
- It consists of a combination of a **username, password, user ID (UID), group ID (GID), and associated permissions** that define the user's ability to interact with the system.
- Every user in Linux has an associated account.
- Information about a user is stored in <code>/etc/passwd</code> file.
```bash
cat /etc/passwd
```
- Information about groups is stored into <code>/etc/group</code> file.
```bash
cat /etc/group
```

## Break down of User Accounts
- Each user has a username, a unique ID (UID), group ID (GID) (of the group they are part of) assigned to them.
- A user can be part of multiple groups.
- When the user is created and no group is specified, it assigns the user to a group with the same ID and name as the user ID. That’s the **primary GID** of the user.
- The user account also stores information about the **home directory** and the **default shell** of the user.

- Fields of <code>/etc/passwd</code> file:
    - **Username**: Most relevant feature which consists mainly of lowercase letters and some numbers.
    - **Password**: Usually contains an “x” which means it is stored in a different file known as the <code>/etc/shadow</code> file.
    - **User ID (UID)**: Used to track the accounts.
    - **Group ID (GID)**
    - **Group**: Collections of accounts that can be given special permissions within the Linux system.
    - **Comment field**: Holds the user’s full name .
    - **Home directory**: States where the home directory is.
    - **Default shell**: Defines the default shell of a user.

## General Commands:
- <code>id <username></code>: It lists the username, UID, GID and the groups user is part of.
```bash
id michael

uid=1001(michael) gid=1001(michael)groups=1001(michael),1003(developers)
```
- More details about the user account can be found in /etc/passwd eg. default shell, home directory.
```bash
grep -i michael /etc/passwd

michael:x:1001:1001::/home/michael:/bin/sh
```
- <code>who</code>: To see the list of users currently logged.
```bash
who

bob pts/2 Apr 28 06:48 (172.16.238.187)
```
- <code>last</code>: Displays the record of all logged-in users along with the date and time when the system was rebooted.
```bash
last

michael    :1    :1                      Tue May 12 20:00 still logged in
sarah      :1    :1                      Tue May 12 12:00 still running
reboot     system boot 5.3.0-758-gen     Mon May 11 13:00 - 19:00 (06:00)
```

---

# Account Security
- Previously passwords were used to store in <code>/etc/passwd</code> file, but as this file is readable by anyone in the system the passwords are then moved to stored in <code>/etc/shadow</code> file.
- The contents of <code>/etc/shadow</code> are hashed, specifically known as **salted hashed**.
- Salted hash uses a one-way mathematical process with additional random input to produce a non-readable password.

- Fields of <code>/etc/shadow</code> file:
    - **Username**: Most relevant feature which consists mainly of lowercase letters and some numbers.
    - **Password**: Stored as salted hash.
    - **Last password change**
    - **Days until a change is allowed**
    - **Days before a change is required**
    - **Days of warning before password expiration**
    - **Days between expiration and deactivation**
    - **Expiration date**
    - **Special flag**

- Difference between account expiration and account deactivation is:
    - If you have an expired account that can't be used, so at the next login it will ask the user to change their password immediately after they log in because the account has expired. Here, the password remains intact sitting in the shadow file.
    - Ex: Let's say you had 60 days to change the password, you didn't change it, and now it's day 61. It will let you login one more time but it will force to change the password now.
    - For a deactivated account, a password is actually erased from a shadow file and that account canot be used until the system administrator reactivated it again.

---

# Understanding Groups
Group is a collection of user accounts.
- Information about groups is stored into <code>/etc/group</code> file.
```bash
cat /etc/group
```

-  Fields of <code>/etc/group</code> file:
    - **Group Name**
    - **Password** (optional)
    - **GID**
    - **User list**

**Group membership**
- By specifying the group’s GID in users’ individual <code>/etc/passwd</code> entry (known as primary group).
- By specifying usernames in the user list in the <code>/etc/group</code> file (known as secondary groups).

---

# Using Account Tools
- <code>whoami</code>: Tells the user with multiple accounts which one they’re logged in as.
- <code>id</code>: It lists the username, UID, GID and the groups user is part of.
- <code>who</code>: Gives information about who’s currently using the computer
    - Username
    - Terminal identifier
    - Login date and time
    - Remote host
- <code>w</code>: Similar to who but produces more verbose output
    - Idle time
    - JCPU – total amount of CPU time for a given session
    - PCPU – total amount of CPU time for the processes running inside a given session
    - WHAT – tells what the session is running and doing

---

# Working as Root
- **Root**:
    - Also called **superuser or administrator**.
    - Has access to system files.

- **Root user privilege**:
    - Log in as root user
    - Use the switch user (<code>su</code>) command
    - Use the <codesudo</code> command
        - Similar to the su command but only works for one command at a time

- **Precautions**:
    - Confirm the need for root access
    - Verify the command
    - Do not run a suspicious program as root
    - Favor the use of <code>sudo</code> over <code>su</code>
    - Do not leave a root shell open
    - Do not share root password with others

## Switching users
- <code>su</code>: To switch to any user.
```bash
su –
    Password:

root ~#
```
- <code>su -c <command></code>: To run a specific command you can use <code>su -c "whoami"</code> (This is not recommended way)
```bash
[michael@ubuntu-server ~]$ su -c "whoami"
    Password:
root
```
- <code>sudo</code>: To run a command as a root user (recommended).
```bash
[michael@ubuntu-server ~]$ sudo apt-get install nginx
[sudo] password for michael:
```

## SUDO
- In Linux, sudo (short for "superuser do") is a command that allows users to execute commands with elevated privileges, typically as the root user.
- Users listed in <code>/etc/sudoers</code> file can make use of sudo command for privilege escalation.
- To restrict anyone from directly login as root login, this can be done by setting nologin shell.
```bash
grep -i ^root /etc/passwd
/root:x:0:0:root:/root:/usr/sbin/nologin
```